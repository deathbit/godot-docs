# Control

所有 GUI 控件的基类，依据父控件自适应位置和大小，提供锚点与偏移布局、主题样式、焦点导航、鼠标与拖放交互等用户界面能力。

# 常量
- NOTIFICATION_RESIZED
- NOTIFICATION_MOUSE_ENTER
- NOTIFICATION_MOUSE_EXIT
- NOTIFICATION_MOUSE_ENTER_SELF
- NOTIFICATION_MOUSE_EXIT_SELF
- NOTIFICATION_FOCUS_ENTER
- NOTIFICATION_FOCUS_EXIT
- NOTIFICATION_THEME_CHANGED
- NOTIFICATION_SCROLL_BEGIN
- NOTIFICATION_SCROLL_END
- NOTIFICATION_LAYOUT_DIRECTION_CHANGED

# 属性
## 锚点与偏移
- anchor_bottom
- anchor_left
- anchor_right
- anchor_top
- offset_bottom
- offset_left
- offset_right
- offset_top
- grow_horizontal
- grow_vertical

## 变换
- position
- rotation
- rotation_degrees
- scale
- global_position
- pivot_offset
- pivot_offset_ratio
- offset_transform_enabled
- offset_transform_pivot
- offset_transform_pivot_ratio
- offset_transform_position
- offset_transform_position_ratio
- offset_transform_rotation
- offset_transform_scale
- offset_transform_visual_only

## 尺寸
- size
- custom_minimum_size
- custom_maximum_size
- propagate_maximum_size
- size_flags_horizontal
- size_flags_vertical
- size_flags_stretch_ratio

## 焦点
- focus_mode
- focus_behavior_recursive
- focus_neighbor_bottom
- focus_neighbor_left
- focus_neighbor_right
- focus_neighbor_top
- focus_next
- focus_previous

## 鼠标
- mouse_behavior_recursive
- mouse_default_cursor_shape
- mouse_filter
- mouse_force_pass_scroll_events

## 主题
- theme
- theme_type_variation

## 提示
- tooltip_text
- tooltip_auto_translate_mode

## 布局方向与本地化
- layout_direction
- auto_translate
- localize_numeral_system
- translation_context

## 无障碍
- accessibility_name
- accessibility_description
- accessibility_live
- accessibility_controls_nodes
- accessibility_described_by_nodes
- accessibility_flow_to_nodes
- accessibility_labeled_by_nodes

## 其他
- clip_contents
- shortcut_context

# 信号
- focus_entered
- focus_exited
- gui_input
- maximum_size_changed
- minimum_size_changed
- mouse_entered
- mouse_exited
- resized
- size_flags_changed
- theme_changed

# 枚举
## FocusMode
- FOCUS_NONE
- FOCUS_CLICK
- FOCUS_ALL
- FOCUS_ACCESSIBILITY

## FocusBehaviorRecursive
- FOCUS_BEHAVIOR_INHERITED
- FOCUS_BEHAVIOR_DISABLED
- FOCUS_BEHAVIOR_ENABLED

## MouseBehaviorRecursive
- MOUSE_BEHAVIOR_INHERITED
- MOUSE_BEHAVIOR_DISABLED
- MOUSE_BEHAVIOR_ENABLED

## MouseFilter
- MOUSE_FILTER_STOP
- MOUSE_FILTER_PASS
- MOUSE_FILTER_IGNORE

## CursorShape
- CURSOR_ARROW
- CURSOR_IBEAM
- CURSOR_POINTING_HAND
- CURSOR_CROSS
- CURSOR_WAIT
- CURSOR_BUSY
- CURSOR_DRAG
- CURSOR_CAN_DROP
- CURSOR_FORBIDDEN
- CURSOR_VSIZE
- CURSOR_HSIZE
- CURSOR_BDIAGSIZE
- CURSOR_FDIAGSIZE
- CURSOR_MOVE
- CURSOR_VSPLIT
- CURSOR_HSPLIT
- CURSOR_HELP

## LayoutPreset
- PRESET_TOP_LEFT
- PRESET_TOP_RIGHT
- PRESET_BOTTOM_LEFT
- PRESET_BOTTOM_RIGHT
- PRESET_CENTER_LEFT
- PRESET_CENTER_TOP
- PRESET_CENTER_RIGHT
- PRESET_CENTER_BOTTOM
- PRESET_CENTER
- PRESET_LEFT_WIDE
- PRESET_TOP_WIDE
- PRESET_RIGHT_WIDE
- PRESET_BOTTOM_WIDE
- PRESET_VCENTER_WIDE
- PRESET_HCENTER_WIDE
- PRESET_FULL_RECT

## LayoutPresetMode
- PRESET_MODE_MINSIZE
- PRESET_MODE_KEEP_WIDTH
- PRESET_MODE_KEEP_HEIGHT
- PRESET_MODE_KEEP_SIZE

## SizeFlags
- SIZE_SHRINK_BEGIN
- SIZE_FILL
- SIZE_EXPAND
- SIZE_EXPAND_FILL
- SIZE_SHRINK_CENTER
- SIZE_SHRINK_END

## GrowDirection
- GROW_DIRECTION_BEGIN
- GROW_DIRECTION_END
- GROW_DIRECTION_BOTH

## Anchor
- ANCHOR_BEGIN
- ANCHOR_END

## LayoutDirection
- LAYOUT_DIRECTION_INHERITED
- LAYOUT_DIRECTION_APPLICATION_LOCALE
- LAYOUT_DIRECTION_LTR
- LAYOUT_DIRECTION_RTL
- LAYOUT_DIRECTION_SYSTEM_LOCALE
- LAYOUT_DIRECTION_MAX
- LAYOUT_DIRECTION_LOCALE

## TextDirection
- TEXT_DIRECTION_INHERITED
- TEXT_DIRECTION_AUTO
- TEXT_DIRECTION_LTR
- TEXT_DIRECTION_RTL

# 方法
## 虚函数
- _accessibility_get_contextual_info
- _can_drop_data
- _drop_data
- _get_accessibility_container_name
- _get_cursor_shape
- _get_drag_data
- _get_maximum_size
- _get_minimum_size
- _get_tooltip
- _get_tooltip_auto_translate_mode_at
- _gui_input
- _has_point
- _make_custom_tooltip
- _structured_text_parser

## 锚点与偏移
- get_anchor
- set_anchor
- set_anchor_and_offset
- get_begin
- set_begin
- get_end
- set_end
- get_offset
- set_offset
- set_anchors_preset
- set_anchors_and_offsets_preset
- set_offsets_preset

## 尺寸与最小尺寸
- get_minimum_size
- get_combined_minimum_size
- update_minimum_size
- get_maximum_size
- get_combined_maximum_size
- update_maximum_size
- get_bound_minimum_size
- get_combined_pivot_offset
- reset_size
- set_size

## 位置与矩形
- set_position
- set_global_position
- get_rect
- get_global_rect
- get_screen_position
- get_parent_area_size
- get_parent_control

## 焦点
- grab_focus
- grab_click_focus
- release_focus
- has_focus
- find_next_valid_focus
- find_prev_valid_focus
- find_valid_focus_neighbor
- get_focus_neighbor
- set_focus_neighbor
- get_focus_mode_with_override

## 拖放
- accessibility_drag
- accessibility_drop
- force_drag
- is_drag_successful
- set_drag_forwarding
- set_drag_preview

## 主题覆盖
- add_theme_color_override
- add_theme_constant_override
- add_theme_font_override
- add_theme_font_size_override
- add_theme_icon_override
- add_theme_stylebox_override
- remove_theme_color_override
- remove_theme_constant_override
- remove_theme_font_override
- remove_theme_font_size_override
- remove_theme_icon_override
- remove_theme_stylebox_override
- has_theme_color_override
- has_theme_constant_override
- has_theme_font_override
- has_theme_font_size_override
- has_theme_icon_override
- has_theme_stylebox_override
- begin_bulk_theme_override
- end_bulk_theme_override

## 主题查询
- get_theme_color
- get_theme_constant
- get_theme_font
- get_theme_font_size
- get_theme_icon
- get_theme_stylebox
- has_theme_color
- has_theme_constant
- has_theme_font
- has_theme_font_size
- has_theme_icon
- has_theme_stylebox
- get_theme_default_base_scale
- get_theme_default_font
- get_theme_default_font_size

## 光标与提示
- get_cursor_shape
- get_tooltip

## 输入与其他
- accept_event
- get_mouse_filter_with_override
- is_layout_rtl
- warp_mouse
