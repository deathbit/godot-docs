# Object
引擎中所有其他类的基类，是一种高级 Variant 类型，提供属性、方法、信号、元数据、通知和脚本等基础能力。

# 常量
- NOTIFICATION_POSTINITIALIZE
- NOTIFICATION_PREDELETE
- NOTIFICATION_EXTENSION_RELOADED

# 信号
- property_list_changed
- script_changed

# 枚举
## ConnectFlags
- CONNECT_DEFERRED
- CONNECT_PERSIST
- CONNECT_ONE_SHOT
- CONNECT_REFERENCE_COUNTED
- CONNECT_APPEND_SOURCE_OBJECT

# 方法
## 虚函数（脚本可重写）
- _get
- _get_property_list
- _init
- _iter_get
- _iter_init
- _iter_next
- _notification
- _property_can_revert
- _property_get_revert
- _set
- _to_string
- _validate_property

## 方法调用
- call
- call_deferred
- callv
- set_deferred

## 信号管理
- add_user_signal
- remove_user_signal
- has_user_signal
- has_signal
- connect
- disconnect
- is_connected
- emit_signal
- get_incoming_connections
- get_signal_connection_list
- get_signal_list
- has_connections
- set_block_signals
- is_blocking_signals

## 属性访问
- get
- set
- get_indexed
- set_indexed
- get_property_list
- property_can_revert
- property_get_revert
- notify_property_list_changed

## 元数据
- set_meta
- get_meta
- has_meta
- remove_meta
- get_meta_list

## 类型与反射
- get_class
- is_class
- get_instance_id
- has_method
- get_method_argument_count
- get_method_list

## 脚本管理
- get_script
- set_script

## 对象生命周期
- free
- cancel_free
- is_queued_for_deletion
- notification

## 翻译
- tr
- tr_n
- can_translate_messages
- set_message_translation
- get_translation_domain
- set_translation_domain
