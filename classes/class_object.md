# Object 类说明文档

> 本文档基于 `classes/class_object.rst` 整理，使用中文对 Godot 引擎中 **Object** 类的方法、信号、枚举与常量进行归类与简要说明，便于快速查阅。

## 综合描述

**Object** 是 Godot 引擎中所有其他类的基类，是一种高级的 [`Variant`](class_variant.rst) 类型。引擎中的每个类都继承自 Object，每个类可以定义新的属性、方法或信号，并可供其所有派生类使用。

主要特性：

- **实例创建与释放**：在 GDScript 中可使用 `Object.new()` 创建实例，在 C# 中使用 `new GodotObject`。删除实例需调用 [`free()`](#free)，否则容易造成内存泄漏。少数类会自行管理内存，例如 [`RefCounted`](class_refcounted.rst)（及其派生的 [`Resource`](class_resource.rst)）在不再被引用时自动删除，[`Node`](class_node.rst) 在释放时会删除其子节点。
- **脚本扩展**：Object 可以附加 [`Script`](class_script.rst)。脚本实例化后会作为基类的扩展，允许定义和继承新的属性、方法与信号。Godot 的运行期非常动态，对象的脚本及其成员都可以在运行时改变。
- **动态访问的安全性**：由于成员可能在运行时不存在，可使用 [`set()`](#set)、[`get()`](#get)、[`call()`](#call)、[`has_method()`](#has_method)、[`has_signal()`](#has_signal) 等方法来避免运行时错误（但这些方法比直接引用慢得多）。在 GDScript 中也可用 `in` 运算符检查某属性、方法或信号是否存在。
- **通知机制**：通知是对象之间常用于收发的 [`int`](class_int.rst) 常量。可通过 [`notification()`](#notification) 与 [`_notification()`](#_notification) 来使用通知。
- **元数据（Metadata）**：每个对象可以携带元数据（关于数据的数据），通过 [`set_meta()`](#set_meta) 存储对象本身不依赖的信息。不建议过度使用元数据。

> **注意**
> - 对象的引用可能在未被设为 `null` 的情况下失效。检查对象是否已被删除时，**不要**与 `null` 比较，应使用 [`@GlobalScope.is_instance_valid()`](class_@globalscope.rst)。存储数据的类建议继承 [`RefCounted`](class_refcounted.rst)。
> - `script` 不像普通属性那样暴露，需使用 [`set_script()`](#set_script) 和 [`get_script()`](#get_script) 进行设置/获取。
> - 在布尔上下文中，等于 `null` 或已被释放的 Object 求值为 `false`，否则总是 `true`。

**教程参考：**

- Object 类介绍（`engine_details/architecture/object_class`）
- 何时以及如何避免事事都用节点（`tutorials/best_practices/node_alternatives`）
- Object 通知（`tutorials/best_practices/godot_notifications`）

---

## 方法（Methods）

方法按功能划分为以下几类。带 `_` 前缀的为可被脚本覆写的虚方法（virtual）。

### 1. 虚方法（可覆写 / virtual）

用于在脚本中自定义对象的底层行为，由引擎在适当时机调用。

| 返回类型 | 方法 | 简要说明 |
| --- | --- | --- |
| `Variant` | `_get`(property) | 覆写属性的读取逻辑，返回给定属性的值。 |
| `Array[Dictionary]` | `_get_property_list`() | 返回自定义的属性列表（用于编辑器显示、分组、保存等）。 |
| `void` | `_init`() | 对象构造时调用，相当于构造函数。 |
| `Variant` | `_iter_get`(iter) | 自定义迭代器：返回当前迭代值。 |
| `bool` | `_iter_init`(iter) | 自定义迭代器：初始化迭代，返回是否可迭代。 |
| `bool` | `_iter_next`(iter) | 自定义迭代器：前进到下一个元素，返回是否继续。 |
| `void` | `_notification`(what) | 接收并处理引擎发送的通知。 |
| `bool` | `_property_can_revert`(property) | 返回某属性是否支持还原为默认值。 |
| `Variant` | `_property_get_revert`(property) | 返回某属性的默认（可还原）值。 |
| `bool` | `_set`(property, value) | 覆写属性的写入逻辑，返回是否处理成功。 |
| `String` | `_to_string`() | 自定义对象转字符串时的表示。 |
| `void` | `_validate_property`(property) | 在属性显示前修改其特性（如可见性、用法标志）。 |

### 2. 方法调用（Call）

动态地按名称调用方法。

| 返回类型 | 方法 | 简要说明 |
| --- | --- | --- |
| `Variant` | `call`(method, ...) | 立即按名称调用方法并传入可变参数。 |
| `Variant` | `call_deferred`(method, ...) | 延迟到当前帧空闲时再调用方法。 |
| `Variant` | `callv`(method, arg_array) | 以数组形式传参调用方法。 |
| `int` | `get_method_argument_count`(method) | 返回指定方法的参数个数。 |
| `Array[Dictionary]` | `get_method_list`() | 返回对象的方法列表。 |
| `bool` | `has_method`(method) | 判断对象是否存在指定方法。 |

### 3. 属性访问（Property）

按名称或路径动态读写属性。

| 返回类型 | 方法 | 简要说明 |
| --- | --- | --- |
| `Variant` | `get`(property) | 按名称获取属性值。 |
| `Variant` | `get_indexed`(property_path) | 按属性路径（NodePath）获取嵌套属性值。 |
| `Array[Dictionary]` | `get_property_list`() | 返回对象的属性列表。 |
| `void` | `set`(property, value) | 按名称设置属性值。 |
| `void` | `set_deferred`(property, value) | 延迟到帧末再设置属性值。 |
| `void` | `set_indexed`(property_path, value) | 按属性路径设置嵌套属性值。 |
| `void` | `notify_property_list_changed`() | 通知属性列表发生变化（刷新编辑器）。 |
| `bool` | `property_can_revert`(property) | 返回属性是否可还原为默认值。 |
| `Variant` | `property_get_revert`(property) | 返回属性的默认（可还原）值。 |

### 4. 信号系统（Signal）

连接、断开、发射信号以及管理用户自定义信号。

| 返回类型 | 方法 | 简要说明 |
| --- | --- | --- |
| `void` | `add_user_signal`(signal, arguments=[]) | 添加一个用户自定义信号。 |
| `Error` | `connect`(signal, callable, flags=0) | 将信号连接到可调用对象（可附带连接标志）。 |
| `void` | `disconnect`(signal, callable) | 断开信号与可调用对象的连接。 |
| `Error` | `emit_signal`(signal, ...) | 发射指定信号并传入参数。 |
| `Array[Dictionary]` | `get_incoming_connections`() | 返回连接到本对象信号的入站连接列表。 |
| `Array[Dictionary]` | `get_signal_connection_list`(signal) | 返回指定信号的连接列表。 |
| `Array[Dictionary]` | `get_signal_list`() | 返回对象的信号列表。 |
| `bool` | `has_connections`(signal) | 判断指定信号是否存在任何连接。 |
| `bool` | `has_signal`(signal) | 判断对象是否存在指定信号。 |
| `bool` | `has_user_signal`(signal) | 判断是否存在指定的用户自定义信号。 |
| `bool` | `is_connected`(signal, callable) | 判断信号是否已与可调用对象连接。 |
| `bool` | `is_blocking_signals`() | 返回信号是否被阻塞。 |
| `void` | `set_block_signals`(enable) | 启用/禁用信号阻塞（阻塞时发射不生效）。 |
| `void` | `remove_user_signal`(signal) | 移除用户自定义信号。 |

### 5. 元数据（Metadata）

存储对象本身不依赖的附加数据。

| 返回类型 | 方法 | 简要说明 |
| --- | --- | --- |
| `Variant` | `get_meta`(name, default=null) | 获取指定名称的元数据（可带默认值）。 |
| `Array[StringName]` | `get_meta_list`() | 返回所有元数据条目的名称列表。 |
| `bool` | `has_meta`(name) | 判断是否存在指定元数据。 |
| `void` | `set_meta`(name, value) | 设置元数据条目。 |
| `void` | `remove_meta`(name) | 移除指定元数据条目。 |

### 6. 类型与实例信息（Type / Instance）

获取类名、实例 ID 以及脚本等信息。

| 返回类型 | 方法 | 简要说明 |
| --- | --- | --- |
| `String` | `get_class`() | 返回对象的类名（不含脚本类名）。 |
| `bool` | `is_class`(class) | 判断对象是否为指定类或其派生类。 |
| `int` | `get_instance_id`() | 返回对象的唯一实例 ID。 |
| `Variant` | `get_script`() | 返回附加在对象上的脚本。 |
| `void` | `set_script`(script) | 为对象设置脚本。 |

### 7. 生命周期与通知（Lifecycle / Notification）

控制对象的释放及通知派发。

| 返回类型 | 方法 | 简要说明 |
| --- | --- | --- |
| `void` | `free`() | 立即删除对象，释放其占用的内存。 |
| `void` | `cancel_free`() | 取消之前请求的释放（`free`/`queue_free`）。 |
| `bool` | `is_queued_for_deletion`() | 判断对象是否已排队等待删除。 |
| `void` | `notification`(what, reversed=false) | 向对象发送通知（可选反向派发）。 |

### 8. 翻译与本地化（Translation）

文本翻译及翻译域设置。

| 返回类型 | 方法 | 简要说明 |
| --- | --- | --- |
| `String` | `tr`(message, context=&"") | 翻译消息（可指定上下文）。 |
| `String` | `tr_n`(message, plural_message, n, context=&"") | 按数量 n 翻译单复数消息。 |
| `bool` | `can_translate_messages`() | 返回对象是否启用消息翻译。 |
| `void` | `set_message_translation`(enable) | 启用/禁用对象的消息翻译。 |
| `StringName` | `get_translation_domain`() | 返回对象使用的翻译域。 |
| `void` | `set_translation_domain`(domain) | 设置对象的翻译域。 |

### 9. 字符串转换（String）

| 返回类型 | 方法 | 简要说明 |
| --- | --- | --- |
| `String` | `to_string`() | 返回对象的默认字符串表示。 |

---

## 信号（Signals）

| 信号 | 说明 |
| --- | --- |
| `property_list_changed`() | 当调用 [`notify_property_list_changed()`](#方法methods) 时发射。 |
| `script_changed`() | 当对象的脚本被更改时发射。**注意**：发射时新脚本尚未初始化，若需访问新脚本，请使用 `CONNECT_DEFERRED` 进行延迟连接。 |

---

## 枚举（Enumerations）

### ConnectFlags（连接标志，flags 位标志）

用于 [`connect()`](#方法methods) 的连接行为控制，可按位组合。

| 常量 | 值 | 说明 |
| --- | --- | --- |
| `CONNECT_DEFERRED` | `1` | 延迟连接：在空闲时（帧末）触发回调，而非立即触发。 |
| `CONNECT_PERSIST` | `2` | 持久连接：对象序列化时（如 `PackedScene.pack()`）会被保存。编辑器信号面板创建的连接均为持久连接。（注：连接到 lambda 函数无法持久化。） |
| `CONNECT_ONE_SHOT` | `4` | 一次性连接：发射一次后自动断开。 |
| `CONNECT_REFERENCE_COUNTED` | `8` | 引用计数连接：同一可调用对象可多次连接，每次断开计数减一，计数归零时才完全断开。 |
| `CONNECT_APPEND_SOURCE_OBJECT` | `16` | 发射时自动将源对象追加到信号原始参数之后（不受可调用对象 unbind 影响）。 |

---

## 常量（Constants）

以下为对象生命周期相关的通知常量。

| 常量 | 值 | 说明 |
| --- | --- | --- |
| `NOTIFICATION_POSTINITIALIZE` | `0` | 对象初始化完成、脚本附加之前收到的通知（内部使用）。 |
| `NOTIFICATION_PREDELETE` | `1` | 对象即将被删除时收到的通知，类似于面向对象语言中的析构函数。该通知以反向顺序发送。 |
| `NOTIFICATION_EXTENSION_RELOADED` | `2` | 对象完成热重载时收到的通知，仅对扩展类及其派生类发送。 |
