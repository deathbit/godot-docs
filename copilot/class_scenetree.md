# SceneTree

通过节点层级管理游戏主循环的类，负责场景树的运行与切换、节点分组调用、定时器与补间创建以及多人游戏轮询。

# 属性
- auto_accept_quit
- current_scene
- debug_collisions_hint
- debug_navigation_hint
- debug_paths_hint
- edited_scene_root
- multiplayer_poll
- paused
- physics_interpolation
- quit_on_go_back
- root

# 信号
- node_added
- node_removed
- node_renamed
- node_configuration_warning_changed
- physics_frame
- process_frame
- scene_changed
- tree_changed
- tree_process_mode_changed

# 枚举
## GroupCallFlags
- GROUP_CALL_DEFAULT
- GROUP_CALL_REVERSE
- GROUP_CALL_DEFERRED
- GROUP_CALL_UNIQUE

# 方法
## 分组操作
- call_group
- call_group_flags
- notify_group
- notify_group_flags
- set_group
- set_group_flags
- get_first_node_in_group
- get_nodes_in_group
- get_node_count_in_group
- has_group

## 场景切换
- change_scene_to_file
- change_scene_to_node
- change_scene_to_packed
- reload_current_scene
- unload_current_scene

## 节点管理
- get_node_count
- queue_delete

## 定时器与补间
- create_timer
- create_tween
- get_processed_tweens

## 多人游戏
- get_multiplayer
- set_multiplayer

## 帧与无障碍
- get_frame
- is_accessibility_enabled
- is_accessibility_supported

## 应用控制
- quit
