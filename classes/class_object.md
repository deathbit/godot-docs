# Object 类说明文档

> 本文档基于 `classes/class_object.rst` 整理，使用中文对 Godot 引擎中 **Object** 类的方法、信号、枚举与常量进行归类与简要说明，便于快速查阅。

## 综合描述

Object 是 Godot 引擎中所有其他类的基类，提供属性、方法、信号、脚本扩展、通知与元数据等核心能力。

## 方法

方法按功能划分为以下几类，带 `_` 前缀的为可被脚本覆写的虚方法。

| 分类 | 方法 |
| --- | --- |
| 虚方法（可覆写） | `_get`、`_get_property_list`、`_init`、`_iter_get`、`_iter_init`、`_iter_next`、`_notification`、`_property_can_revert`、`_property_get_revert`、`_set`、`_to_string`、`_validate_property` |
| 方法调用 | `call`、`call_deferred`、`callv`、`get_method_argument_count`、`get_method_list`、`has_method` |
| 属性访问 | `get`、`get_indexed`、`get_property_list`、`set`、`set_deferred`、`set_indexed`、`notify_property_list_changed`、`property_can_revert`、`property_get_revert` |
| 信号系统 | `add_user_signal`、`connect`、`disconnect`、`emit_signal`、`get_incoming_connections`、`get_signal_connection_list`、`get_signal_list`、`has_connections`、`has_signal`、`has_user_signal`、`is_connected`、`is_blocking_signals`、`set_block_signals`、`remove_user_signal` |
| 元数据 | `get_meta`、`get_meta_list`、`has_meta`、`set_meta`、`remove_meta` |
| 类型与实例信息 | `get_class`、`is_class`、`get_instance_id`、`get_script`、`set_script` |
| 生命周期与通知 | `free`、`cancel_free`、`is_queued_for_deletion`、`notification` |
| 翻译与本地化 | `tr`、`tr_n`、`can_translate_messages`、`set_message_translation`、`get_translation_domain`、`set_translation_domain` |
| 字符串转换 | `to_string` |

## 信号

- `property_list_changed` — 当调用 `notify_property_list_changed` 时发射。
- `script_changed` — 当对象的脚本被更改时发射。注意：发射时新脚本尚未初始化，若需访问新脚本，请使用 `CONNECT_DEFERRED` 进行延迟连接。

## 枚举

ConnectFlags（连接标志，按位组合，用于 `connect` 的连接行为控制）：

- `CONNECT_DEFERRED`（值 `1`）— 延迟连接：在空闲时（帧末）触发回调，而非立即触发。
- `CONNECT_PERSIST`（值 `2`）— 持久连接：对象序列化时会被保存；编辑器信号面板创建的连接均为持久连接（连接到 lambda 函数无法持久化）。
- `CONNECT_ONE_SHOT`（值 `4`）— 一次性连接：发射一次后自动断开。
- `CONNECT_REFERENCE_COUNTED`（值 `8`）— 引用计数连接：同一可调用对象可多次连接，每次断开计数减一，计数归零时才完全断开。
- `CONNECT_APPEND_SOURCE_OBJECT`（值 `16`）— 发射时自动将源对象追加到信号原始参数之后（不受可调用对象 unbind 影响）。

## 常量

以下为对象生命周期相关的通知常量：

- `NOTIFICATION_POSTINITIALIZE`（值 `0`）— 对象初始化完成、脚本附加之前收到的通知（内部使用）。
- `NOTIFICATION_PREDELETE`（值 `1`）— 对象即将被删除时收到的通知，类似于面向对象语言中的析构函数，该通知以反向顺序发送。
- `NOTIFICATION_EXTENSION_RELOADED`（值 `2`）— 对象完成热重载时收到的通知，仅对扩展类及其派生类发送。
