# CanvasItem

一切 2D 空间对象的抽象基类，提供层级变换、绘制、可见性、调制颜色与 Z 轴渲染顺序等核心能力，由 Control 与 Node2D 继承。

# 常量
- NOTIFICATION_TRANSFORM_CHANGED
- NOTIFICATION_LOCAL_TRANSFORM_CHANGED
- NOTIFICATION_DRAW
- NOTIFICATION_VISIBILITY_CHANGED
- NOTIFICATION_ENTER_CANVAS
- NOTIFICATION_EXIT_CANVAS
- NOTIFICATION_WORLD_2D_CHANGED

# 属性
## 可见性
- visible
- modulate
- self_modulate
- show_behind_parent
- top_level
- clip_children
- visibility_layer

## 渲染顺序
- z_index
- z_as_relative
- y_sort_enabled

## 纹理与材质
- material
- use_parent_material
- texture_filter
- texture_repeat
- oversampling_with_scale

## 光照
- light_mask

# 信号
- draw
- hidden
- item_rect_changed
- visibility_changed

# 枚举
## TextureFilter
- TEXTURE_FILTER_PARENT_NODE
- TEXTURE_FILTER_NEAREST
- TEXTURE_FILTER_LINEAR
- TEXTURE_FILTER_NEAREST_WITH_MIPMAPS
- TEXTURE_FILTER_LINEAR_WITH_MIPMAPS
- TEXTURE_FILTER_NEAREST_WITH_MIPMAPS_ANISOTROPIC
- TEXTURE_FILTER_LINEAR_WITH_MIPMAPS_ANISOTROPIC
- TEXTURE_FILTER_MAX

## TextureRepeat
- TEXTURE_REPEAT_PARENT_NODE
- TEXTURE_REPEAT_DISABLED
- TEXTURE_REPEAT_ENABLED
- TEXTURE_REPEAT_MIRROR
- TEXTURE_REPEAT_MAX

## ClipChildrenMode
- CLIP_CHILDREN_DISABLED
- CLIP_CHILDREN_ONLY
- CLIP_CHILDREN_AND_DRAW
- CLIP_CHILDREN_MAX

## OversamplingWithScale
- OVERSAMPLING_WITH_SCALE_PARENT_NODE
- OVERSAMPLING_WITH_SCALE_DISABLED
- OVERSAMPLING_WITH_SCALE_ENABLED
- OVERSAMPLING_WITH_SCALE_MAX

# 方法
## 虚函数
- _draw

## 绘制基本图元
- draw_line
- draw_dashed_line
- draw_polyline
- draw_polyline_colors
- draw_arc
- draw_multiline
- draw_multiline_colors
- draw_rect
- draw_circle
- draw_ellipse
- draw_ellipse_arc
- draw_primitive
- draw_polygon
- draw_colored_polygon

## 绘制纹理
- draw_texture
- draw_texture_rect
- draw_texture_rect_region
- draw_msdf_texture_rect_region
- draw_lcd_texture_rect_region
- draw_style_box

## 绘制网格
- draw_mesh
- draw_multimesh

## 绘制文本
- draw_char
- draw_char_outline
- draw_string
- draw_string_outline
- draw_multiline_string
- draw_multiline_string_outline

## 绘制控制
- draw_set_transform
- draw_set_transform_matrix
- draw_animation_slice
- draw_end_animation
- queue_redraw

## 变换
- get_transform
- get_global_transform
- get_global_transform_with_canvas
- get_canvas_transform
- get_viewport_transform
- get_screen_transform
- force_update_transform

## 变换通知
- set_notify_transform
- is_transform_notification_enabled
- set_notify_local_transform
- is_local_transform_notification_enabled

## 坐标转换
- make_canvas_position_local
- make_input_local
- get_local_mouse_position
- get_global_mouse_position

## 可见性
- show
- hide
- is_visible_in_tree
- move_to_front

## 可见性层
- set_visibility_layer_bit
- get_visibility_layer_bit

## 着色器参数
- set_instance_shader_parameter
- get_instance_shader_parameter

## 画布与视口
- get_canvas
- get_canvas_item
- get_canvas_layer_node
- get_world_2d
- get_viewport_rect
