# Reactive Planner
## Motion Planning in Frenet Frame

1. 轨迹方程
$x(s, d) = r(s) + d \cdot n(s)$
其中，r是沿着参考路径方向，n为垂直于参考路径方向

![](https://i.imgur.com/tbSkH7p.png)

2. 初始和终了条件
初始条件: $P_0=[p_0, \dot{p}_0, \ddot{p}_0]$
终了条件: $P_1=[p_1, \dot{p}_1, \ddot{p}_1]$
规划时间: $T:= t_1 - t_0$

3. 主要的损失泛函：
$J_t(p(t)) = \int_{t_0}^{t_1}\dddot{p}(\tau)d\tau$
可生成五阶多项式曲线的损失函数的一般形式为：
$C=k_{j}J_t + k_{t}g(T) + k_{p}h(p_1)$
即损失函数跟jerk的平滑程度，规划总时间，终了状态有关

### Lateral 方向上的规划：
* 高速情况下：
$C_d = k_{j}J_t(d(t)) + k_{t}\Delta T + k_{d}d_1^2$
* 低速情况下：
$C_d = k_{j}J_s(d(s)) + k_{t}\Delta S + k_{d}d_1^2$

### Longitudinal 方向上的规划：
一般情况下，在longitudinal方向上的规划多用于车辆的following，merging和停车上，以上任务均对一个目标位置进行跟随$s_{target}(t)$。相应的，终了条件为：
$[s_1, \dot{s}_1, \ddot{s}_1, T] = [[s_{target}(T_j)+\Delta s_i], \dot{s}_{target}(T_j), \ddot{s}_{target}(T_j), T_j]$
对应的损失函数为：
$C_t = k_{j}J_t + k_{t}T + k_{s}[s_1 - s_d]^2$

针对特殊情况:
* following:
$s_{target}(t):= s_{lv}(t) - [D_0 + \tau\dot{s}_{lv}(t)]$
因为我们需要对前方车辆的行驶状态进行估计预测，不失一般性，本文将前车的减速度值设为恒定值。根据时间的积分情况，这里可以设计成：
$\dot{s}_{lv}(t)=s_{target}(t_0) + \ddot{s}_{lv}(t_0)[t-t_0]$
$s_{lv}(t)=s_{lv}(t_0)+\dot{s}_{lv}(t_0)[t-t_0]+\frac{1}{2}\ddot{s}_{lv}(t_0)[t-t_0]^2$
* merging:
定义的目标点为：$s_{target}(t) = \frac{1}{2}[s_a(t) + s_b(t)]$
* stopping:
目标点为：$s_{target}=s_{stop}$, $\dot{s}_{target}=0$, $\ddot{s}_{target}=0$ 
* velocity keeping:
损失函数为：$C_{v}=k_{j}J_{t}(s(t)) + k_{t}T + k_{\dot{s}}[\dot{s}_1-\dot{s}_d]^2$

### 考虑两个方向的规划问题：
总损失函数由各自的损失函数加权求和
* 需要检测轨迹是否符合车辆的动力学特性
* 检测轨迹车辆是否会与其他车辆相撞


