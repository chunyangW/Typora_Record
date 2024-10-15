# B-spline-based vs. Mesh-based multi-objective Deformable Image Registration



## 首先是变换模型 Deformable Image Registration(DIR)

- 要去寻找图像之间的可能相关的区域
- 有两种常用的模型-B样条与Mesh models
- 在实际中也会去使用不同的优化算法
- 可变模型配准实际上是解决多物体的冲突优化问题

## 然后是优化目标

- 变换所需要的能量尽量较低原则
- 然后几乎是都需要的两幅图像比较相似

## 再是优化方法

- 使用了进化算法