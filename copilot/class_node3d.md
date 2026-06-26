# Node3D

3D 空间中所有 3D 节点的基类，提供位置、旋转、缩放等三维变换能力，并支持局部/全局变换、可见性控制、变换通知与编辑器 Gizmo。

# 常量
- NOTIFICATION_TRANSFORM_CHANGED
- NOTIFICATION_ENTER_WORLD
- NOTIFICATION_EXIT_WORLD
- NOTIFICATION_VISIBILITY_CHANGED
- NOTIFICATION_LOCAL_TRANSFORM_CHANGED

# 属性
## 局部变换
- position
- rotation
- rotation_degrees
- quaternion
- basis
- scale
- transform

## 全局变换
- global_position
- global_rotation
- global_rotation_degrees
- global_basis
- global_transform

## 旋转设置
- rotation_edit_mode
- rotation_order

## 其他
- top_level
- visible
- visibility_parent

# 信号
- visibility_changed

# 枚举
## RotationEditMode
- ROTATION_EDIT_MODE_EULER
- ROTATION_EDIT_MODE_QUATERNION
- ROTATION_EDIT_MODE_BASIS

# 方法
## 变换操作
- rotate
- rotate_x
- rotate_y
- rotate_z
- rotate_object_local
- global_rotate
- scale_object_local
- global_scale
- translate
- translate_object_local
- global_translate
- look_at
- look_at_from_position
- orthonormalize
- set_identity

## 变换获取与坐标转换
- get_global_transform_interpolated
- to_global
- to_local
- force_update_transform

## 缩放控制
- set_disable_scale
- is_scale_disabled

## 变换通知
- set_notify_transform
- is_transform_notification_enabled
- set_notify_local_transform
- is_local_transform_notification_enabled
- set_ignore_transform_notification

## 可见性
- show
- hide
- is_visible_in_tree

## 场景与父节点
- get_parent_node_3d
- get_world_3d

## Gizmo
- add_gizmo
- get_gizmos
- clear_gizmos
- update_gizmos
- set_subgizmo_selection
- clear_subgizmo_selection
