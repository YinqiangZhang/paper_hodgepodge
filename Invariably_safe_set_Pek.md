
# **Invariably Safe Set (ISS)**

解释:该集合中的所有状态都能够保证agent始终保持安全的状态

## 相关变量：
1. agent的动力学模型 $\dot{x}=f(x(t), u(t))$
2. 输入变量轨迹 $u([0, t_h])$
3. 通过控制率生成控制变量的轨迹 $u([t_1, t_2])=\Phi(x([t_1, t_2]), r_{ref})$，其中控制率的表示可以看作$\Phi$，$r_{ref}$是
4. 将agent的状态投影到lane-based环境中。定义一个操作：$occ(\mathcal{X})=\{occ(x)|x\in\mathcal{X}\}$
5. 免除碰撞的状态（collision-free states）$\mathcal{F}^t\subseteq\mathcal{X}$，为定义该集合的无碰撞特性，有以下公式：$occ(\mathcal{F}^t) \cap \mathcal{O}_{\mathcal{B}}(t)=\emptyset$

本文提出的ISS是为了进一步解决并保证车辆的安全。agent如果在上述集合$\mathcal{F}^t$只能保证该agent在当前时刻$t$是安全的，但不能保证其随后一直处于安全的状态。因此，我们需要计算一个$\mathcal{F}$的子集。若agent的状态位于此该子状态集时，该agent能够保证其状态在随后的时间中一直处于安全的状态。

## 可达集合

Collision-free backward reachable set $\mathcal{R}\subseteq\mathcal{X}$定义为：

$\mathcal{R}(t, \mathcal{o}([t_f-t, t]), \mathcal{X}_f):=\big\{x|\exists r\in [0, t]:\forall\xi\in[t_f-r, t_f]:occ(\chi(\xi, x, u([t_f-r, t_f])))\cap\mathcal{O}(\xi)=\emptyset, u(\xi)\in\mathcal(U), \chi(t_f, x, u([t_f-r, t_f]))\in\mathcal{X}_f\big\}$

## 安全不变集
$\mathcal{S}^t:=\{x\in\mathcal{F}^t|\forall\tau>t:\chi(\tau, x, \Phi(x([t, \tau], r_{ref})))\in\mathcal{F}^\tau\}$




