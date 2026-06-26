# Resource

可序列化对象的基类，能够保存到磁盘并在多个对象间共享复用，支持本地场景化、唯一路径标识与变更通知。

# 属性
- resource_local_to_scene
- resource_name
- resource_path
- resource_scene_unique_id

# 信号
- changed
- setup_local_to_scene_requested

# 枚举
## DeepDuplicateMode
- DEEP_DUPLICATE_NONE
- DEEP_DUPLICATE_INTERNAL
- DEEP_DUPLICATE_ALL

# 方法
## 虚函数
- _get_rid
- _reset_state
- _set_path_cache
- _setup_local_to_scene

## 复制
- duplicate
- duplicate_deep
- copy_from_resource

## 本地场景
- get_local_scene
- setup_local_to_scene
- reset_state

## 路径与标识
- get_rid
- get_id_for_path
- set_id_for_path
- generate_scene_unique_id
- is_built_in
- take_over_path
- set_path_cache

## 变更通知
- emit_changed
