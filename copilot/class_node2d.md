# Node2D

带有 2D 变换（位置、旋转、缩放和倾斜）的 2D 游戏对象基类，所有 2D 相关节点都继承自它，并可控制子节点的移动、缩放、旋转及渲染顺序。

# 属性
## 局部变换
- position
- rotation
- rotation_degrees
- scale
- skew
- transform

## 全局变换
- global_position
- global_rotation
- global_rotation_degrees
- global_scale
- global_skew
- global_transform

# 方法
## 变换操作
- apply_scale
- rotate
- translate
- global_translate
- move_local_x
- move_local_y
- look_at

## 角度与朝向
- get_angle_to

## 坐标转换
- to_global
- to_local

## 相对变换
- get_relative_transform_to_parent
