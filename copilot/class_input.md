# Input

处理输入的单例，用于查询键盘、鼠标、手柄、触摸及设备传感器的状态，触发动作事件，并控制鼠标模式与振动反馈。

# 属性
- emulate_mouse_from_touch
- emulate_touch_from_mouse
- ignore_joypad_on_unfocused_application
- mouse_mode
- use_accumulated_input

# 信号
- joy_connection_changed

# 枚举
## MouseMode
- MOUSE_MODE_VISIBLE
- MOUSE_MODE_HIDDEN
- MOUSE_MODE_CAPTURED
- MOUSE_MODE_CONFINED
- MOUSE_MODE_CONFINED_HIDDEN
- MOUSE_MODE_MAX

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

# 方法
## 动作输入
- action_press
- action_release
- get_action_raw_strength
- get_action_strength
- get_axis
- get_vector
- is_action_pressed
- is_action_just_pressed
- is_action_just_pressed_by_event
- is_action_just_released
- is_action_just_released_by_event
- is_anything_pressed
- parse_input_event
- flush_buffered_events

## 键盘
- is_key_pressed
- is_key_label_pressed
- is_physical_key_pressed

## 鼠标与光标
- get_mouse_button_mask
- is_mouse_button_pressed
- get_last_mouse_screen_velocity
- get_last_mouse_velocity
- get_current_cursor_shape
- set_default_cursor_shape
- set_custom_mouse_cursor
- warp_mouse

## 手柄
- add_joy_mapping
- remove_joy_mapping
- get_connected_joypads
- get_joy_axis
- get_joy_guid
- get_joy_info
- get_joy_name
- is_joy_button_pressed
- is_joy_known
- should_ignore_device

## 手柄振动
- get_joy_vibration_duration
- get_joy_vibration_remaining_duration
- get_joy_vibration_strength
- is_joy_vibrating
- has_joy_vibration
- start_joy_vibration
- stop_joy_vibration
- vibrate_handheld

## 手柄运动传感器与校准
- get_joy_accelerometer
- get_joy_gravity
- get_joy_gyroscope
- get_joy_motion_sensors_calibration
- get_joy_motion_sensors_rate
- has_joy_light
- has_joy_motion_sensors
- is_joy_motion_sensors_calibrated
- is_joy_motion_sensors_calibrating
- is_joy_motion_sensors_enabled
- set_joy_light
- set_joy_motion_sensors_calibration
- set_joy_motion_sensors_enabled
- start_joy_motion_sensors_calibration
- stop_joy_motion_sensors_calibration
- clear_joy_motion_sensors_calibration

## 设备传感器
- get_accelerometer
- get_gravity
- get_gyroscope
- get_magnetometer
- set_accelerometer
- set_gravity
- set_gyroscope
- set_magnetometer
