# SLAM 概览与学习

## 1. Standard formulation and architecture for SLAM

## 2. Robustness in life-long SLAM
1. Front-end: abstracts sensor data into models
* feature extraction:
* data association:
    * short-term: feature trakcing
    * long-term: loop clourse
3. Back-end: performs inference on the abstracted data
    * MAP estimation: likelihood, bundle adjustment, fator graph 

**Open problems**
1. Failsafe SLAM and recovery
2. Robustness to HW failure
3. Metric relocolization
4. Time varing and deformable maps
5. Automatic parameter tuning

## 3. Scalability
design SLAM methods whose computational and memory complexity remains bounded.
1. sparsification methods
    * node and edge sparsification
    * continuous time trajectory estimation
3. out-of-core and multi robots methods
    * out-of-core (parallel) SLAM
    * distributed multi robot SLAM

**Open Problems**
1. Map representstation
2. Learning, forgetting, remmebering
3. Robust distributed mapping
4. Resource constrainted platforms
## 4. How to represent the geometry of environment
Metric representation

**2D case:** 
1. landmark-based maps
2. occupancy grid maps
**3D geometry modeling:**
1. landmark (feature)-based representation
2. low-level raw dense representation: surfel maps
3. boundary and spatial-partitioning dense representation
4. high-level object based representation

## 5. Modling of semantic information

## 6. Active SLAM (Decision making for better SLAM quality)
