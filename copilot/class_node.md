# Node

场景的基本构建块，可作为其他节点的子节点形成树状结构，提供生命周期回调、处理与帧更新、输入处理、分组、多人网络 RPC 等核心能力。

# 常量
## 节点树与生命周期
- NOTIFICATION_ENTER_TREE
- NOTIFICATION_EXIT_TREE
- NOTIFICATION_MOVED_IN_PARENT
- NOTIFICATION_READY
- NOTIFICATION_PARENTED
- NOTIFICATION_UNPARENTED
- NOTIFICATION_SCENE_INSTANTIATED
- NOTIFICATION_PATH_RENAMED
- NOTIFICATION_CHILD_ORDER_CHANGED
- NOTIFICATION_POST_ENTER_TREE

## 处理状态
- NOTIFICATION_PAUSED
- NOTIFICATION_UNPAUSED
- NOTIFICATION_PHYSICS_PROCESS
- NOTIFICATION_PROCESS
- NOTIFICATION_INTERNAL_PROCESS
- NOTIFICATION_INTERNAL_PHYSICS_PROCESS
- NOTIFICATION_DISABLED
- NOTIFICATION_ENABLED
- NOTIFICATION_RESET_PHYSICS_INTERPOLATION

## 拖拽
- NOTIFICATION_DRAG_BEGIN
- NOTIFICATION_DRAG_END

## 编辑器
- NOTIFICATION_EDITOR_PRE_SAVE
- NOTIFICATION_EDITOR_POST_SAVE

## 窗口管理
- NOTIFICATION_WM_MOUSE_ENTER
- NOTIFICATION_WM_MOUSE_EXIT
- NOTIFICATION_WM_WINDOW_FOCUS_IN
- NOTIFICATION_WM_WINDOW_FOCUS_OUT
- NOTIFICATION_WM_CLOSE_REQUEST
- NOTIFICATION_WM_GO_BACK_REQUEST
- NOTIFICATION_WM_SIZE_CHANGED
- NOTIFICATION_WM_DPI_CHANGE
- NOTIFICATION_WM_POSITION_CHANGED
- NOTIFICATION_WM_OUTPUT_MAX_LINEAR_VALUE_CHANGED
- NOTIFICATION_WM_ABOUT

## 视口
- NOTIFICATION_VP_MOUSE_ENTER
- NOTIFICATION_VP_MOUSE_EXIT

## 应用与操作系统
- NOTIFICATION_OS_MEMORY_WARNING
- NOTIFICATION_OS_IME_UPDATE
- NOTIFICATION_CRASH
- NOTIFICATION_APPLICATION_RESUMED
- NOTIFICATION_APPLICATION_PAUSED
- NOTIFICATION_APPLICATION_FOCUS_IN
- NOTIFICATION_APPLICATION_FOCUS_OUT
- NOTIFICATION_APPLICATION_PIP_MODE_ENTERED
- NOTIFICATION_APPLICATION_PIP_MODE_EXITED
- NOTIFICATION_TEXT_SERVER_CHANGED
- NOTIFICATION_TRANSLATION_CHANGED

## 无障碍
- NOTIFICATION_ACCESSIBILITY_UPDATE
- NOTIFICATION_ACCESSIBILITY_INVALIDATE

# 属性
- auto_translate_mode
- editor_description
- multiplayer
- name
- owner
- physics_interpolation_mode
- process_mode
- process_physics_priority
- process_priority
- process_thread_group
- process_thread_group_order
- process_thread_messages
- scene_file_path
- unique_name_in_owner

# 信号
- child_entered_tree
- child_exiting_tree
- child_order_changed
- editor_description_changed
- editor_state_changed
- ready
- renamed
- replacing_by
- tree_entered
- tree_exited
- tree_exiting

# 枚举
## ProcessMode
- PROCESS_MODE_INHERIT
- PROCESS_MODE_PAUSABLE
- PROCESS_MODE_WHEN_PAUSED
- PROCESS_MODE_ALWAYS
- PROCESS_MODE_DISABLED

## ProcessThreadGroup
- PROCESS_THREAD_GROUP_INHERIT
- PROCESS_THREAD_GROUP_MAIN_THREAD
- PROCESS_THREAD_GROUP_SUB_THREAD
- FLAG_PROCESS_THREAD_MESSAGES
- FLAG_PROCESS_THREAD_MESSAGES_PHYSICS
- FLAG_PROCESS_THREAD_MESSAGES_ALL

## PhysicsInterpolationMode
- PHYSICS_INTERPOLATION_MODE_INHERIT
- PHYSICS_INTERPOLATION_MODE_ON
- PHYSICS_INTERPOLATION_MODE_OFF

## DuplicateFlags
- DUPLICATE_SIGNALS
- DUPLICATE_GROUPS
- DUPLICATE_SCRIPTS
- DUPLICATE_USE_INSTANTIATION
- DUPLICATE_INTERNAL_STATE
- DUPLICATE_DEFAULT

## InternalMode
- INTERNAL_MODE_DISABLED
- INTERNAL_MODE_FRONT
- INTERNAL_MODE_BACK

## AutoTranslateMode
- AUTO_TRANSLATE_MODE_INHERIT
- AUTO_TRANSLATE_MODE_ALWAYS
- AUTO_TRANSLATE_MODE_DISABLED

# 方法
## 虚函数
- _enter_tree
- _exit_tree
- _ready
- _process
- _physics_process
- _input
- _shortcut_input
- _unhandled_input
- _unhandled_key_input
- _get_configuration_warnings
- _get_accessibility_configuration_warnings
- _get_focused_accessibility_element

## 子节点管理
- add_child
- add_sibling
- remove_child
- move_child
- get_child
- get_child_count
- get_children
- get_index
- reparent

## 节点查找与路径
- get_node
- get_node_or_null
- get_node_and_resource
- has_node
- has_node_and_resource
- find_child
- find_children
- find_parent
- get_parent
- get_path
- get_path_to
- is_ancestor_of

## 组管理
- add_to_group
- remove_from_group
- is_in_group
- get_groups

## 处理与帧回调
- set_process
- is_processing
- set_physics_process
- is_physics_processing
- set_process_input
- is_processing_input
- set_process_unhandled_input
- is_processing_unhandled_input
- set_process_unhandled_key_input
- is_processing_unhandled_key_input
- set_process_shortcut_input
- is_processing_shortcut_input
- set_process_internal
- is_processing_internal
- set_physics_process_internal
- is_physics_processing_internal
- can_process
- request_ready
- get_process_delta_time
- get_physics_process_delta_time

## 物理插值
- is_physics_interpolated
- is_physics_interpolated_and_enabled
- reset_physics_interpolation

## 场景树与视口
- get_tree
- is_inside_tree
- is_node_ready
- get_viewport
- get_window
- get_last_exclusive_window
- create_tween

## 多人游戏与 RPC
- rpc
- rpc_id
- rpc_config
- get_node_rpc_config
- set_multiplayer_authority
- get_multiplayer_authority
- is_multiplayer_authority

## 线程安全
- call_deferred_thread_group
- set_deferred_thread_group
- notify_deferred_thread_group
- call_thread_safe
- set_thread_safe
- notify_thread_safe

## 编辑器与配置
- set_editable_instance
- is_editable_instance
- set_display_folded
- is_displayed_folded
- set_scene_instance_load_placeholder
- get_scene_instance_load_placeholder
- is_part_of_edited_scene
- update_configuration_warnings
- queue_accessibility_update
- get_accessibility_element

## 打印与调试
- print_tree
- print_tree_pretty
- get_tree_string
- get_tree_string_pretty
- print_orphan_nodes
- get_orphan_node_ids

## 翻译
- atr
- atr_n
- can_auto_translate
- set_translation_domain_inherited

## 复制与替换
- duplicate
- replace_by

## 通用
- queue_free
- propagate_call
- propagate_notification
- is_greater_than
