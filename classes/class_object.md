# Object

Object 是 Godot 引擎中所有非 [Variant] 类型的基类，提供属性、方法、信号、脚本扩展、通知与元数据等核心能力。

# 方法

| 分类 | 方法 |
| --- | --- |
| 虚方法（可覆写） | <ul><li>`_get` — 覆写以自定义 `get()` 的行为，返回属性值或 `null` 交由引擎正常处理。</li><li>`_get_property_list` — 覆写以向引擎提供一组自定义的附加属性。</li><li>`_init` — 脚本实例化时调用，类似于大多数语言中的构造函数。</li><li>`_iter_get` — 返回当前迭代值，供 `for` 循环迭代使用。</li><li>`_iter_init` — 初始化迭代器，并在未到达末尾时返回 `true`。</li><li>`_iter_next` — 将迭代器移动到下一项，并在未到达末尾时返回 `true`。</li><li>`_notification` — 对象收到通知时调用，可通过 `what` 与常量比较来识别通知类型。</li><li>`_property_can_revert` — 覆写以自定义属性的回退行为，返回该属性是否可在检查器中回退。</li><li>`_property_get_revert` — 覆写以返回属性的自定义默认（回退）值。</li><li>`_set` — 覆写以自定义 `set()` 的行为，成功设置属性返回 `true`，否则返回 `false`。</li><li>`_to_string` — 覆写以自定义 `to_string()` 的返回值，即对象的字符串表示。</li><li>`_validate_property` — 覆写以自定义已有属性（如修改其可见性、用途等）。</li></ul> |
| 方法调用 | <ul><li>`call` — 在对象上调用指定方法并返回结果，支持可变数量参数。</li><li>`call_deferred` — 在空闲时（帧末）调用指定方法，始终返回 `null`。</li><li>`callv` — 在对象上调用指定方法，所有参数以数组形式传入并返回结果。</li><li>`get_method_argument_count` — 返回指定方法的参数个数。</li><li>`get_method_list` — 以字典数组形式返回对象的方法及其签名。</li><li>`has_method` — 返回对象中是否存在指定名称的方法。</li></ul> |
| 属性访问 | <ul><li>`get` — 返回指定属性的值，属性不存在时返回 `null`。</li><li>`get_indexed` — 通过属性路径获取属性值，可用冒号访问嵌套属性。</li><li>`get_property_list` — 以字典数组形式返回对象的属性列表。</li><li>`set` — 为指定属性赋值，属性不存在或类型不匹配时不做任何操作。</li><li>`set_deferred` — 在当前帧末为指定属性赋值。</li><li>`set_indexed` — 通过属性路径为属性赋值，可用冒号访问嵌套属性。</li><li>`notify_property_list_changed` — 发射 `property_list_changed` 信号以刷新编辑器。</li><li>`property_can_revert` — 返回指定属性是否具有自定义默认值。</li><li>`property_get_revert` — 返回指定属性的自定义默认值。</li></ul> |
| 信号系统 | <ul><li>`add_user_signal` — 添加一个用户自定义信号。</li><li>`connect` — 按名称将信号连接到可调用对象，可通过 `flags` 配置连接行为。</li><li>`disconnect` — 按名称断开信号与指定可调用对象的连接。</li><li>`emit_signal` — 按名称发射指定信号，支持可变数量参数。</li><li>`get_incoming_connections` — 返回该对象接收到的信号连接数组。</li><li>`get_signal_connection_list` — 返回指定信号的连接列表。</li><li>`get_signal_list` — 以字典数组形式返回已存在的信号列表。</li><li>`has_connections` — 返回指定信号上是否存在任意连接。</li><li>`has_signal` — 返回对象中是否存在指定名称的信号。</li><li>`has_user_signal` — 返回是否存在指定的用户自定义信号。</li><li>`is_connected` — 返回指定信号与可调用对象之间是否存在连接。</li><li>`is_blocking_signals` — 返回对象当前是否处于阻止发射信号的状态。</li><li>`set_block_signals` — 设置对象是否阻止发射信号。</li><li>`remove_user_signal` — 从对象中移除指定的用户自定义信号。</li></ul> |
| 元数据 | <ul><li>`get_meta` — 返回指定名称的元数据值，不存在时返回默认值。</li><li>`get_meta_list` — 返回对象所有元数据条目名称的数组。</li><li>`has_meta` — 返回是否存在指定名称的元数据条目。</li><li>`set_meta` — 添加或修改对象中指定名称的元数据条目。</li><li>`remove_meta` — 从对象元数据中移除指定名称的条目。</li></ul> |
| 类型与实例信息 | <ul><li>`get_class` — 返回对象内置的类名（字符串）。</li><li>`is_class` — 返回对象是否继承自指定类。</li><li>`get_instance_id` — 返回对象唯一的实例 ID。</li><li>`get_script` — 返回对象附加的脚本实例，无脚本时返回 `null`。</li><li>`set_script` — 为对象附加脚本并实例化它。</li></ul> |
| 生命周期与通知 | <ul><li>`free` — 立即从内存中删除对象，已有引用将失效。</li><li>`cancel_free` — 在 `NOTIFICATION_PREDELETE` 期间调用以拒绝被释放（主要供内部错误处理使用）。</li><li>`is_queued_for_deletion` — 返回是否已对该对象调用过 `free` 或 `queue_free`。</li><li>`notification` — 向对象继承的所有类发送指定通知，触发 `_notification` 调用。</li></ul> |
| 翻译与本地化 | <ul><li>`tr` — 使用项目设置中的翻译目录翻译消息。</li><li>`tr_n` — 根据数量 `n` 翻译单/复数消息。</li><li>`can_translate_messages` — 返回对象当前是否允许翻译消息。</li><li>`set_message_translation` — 设置对象是否允许翻译消息（默认启用）。</li><li>`get_translation_domain` — 返回 `tr` 和 `tr_n` 使用的翻译域名称。</li><li>`set_translation_domain` — 设置 `tr` 和 `tr_n` 使用的翻译域名称。</li></ul> |
| 字符串转换 | <ul><li>`to_string` — 返回表示对象的字符串，默认为 `"<ClassName#RID>"`，可通过覆写 `_to_string` 自定义。</li></ul> |

# 信号

| 分类 | 信号 |
| --- | --- |
| 属性与脚本变更 | <ul><li>`property_list_changed` — 当 `notify_property_list_changed()` 被调用时发射。</li><li>`script_changed` — 当对象的脚本被更改时发射；发射时新脚本尚未初始化，如需访问可使用 `CONNECT_DEFERRED` 延迟连接。</li></ul> |

# 枚举

| 分类 | 枚举值 |
| --- | --- |
| ConnectFlags（`connect` 连接标志，可按位组合） | <ul><li>`CONNECT_DEFERRED`（值 `1`）— 延迟连接：在空闲时（帧末）触发回调，而非立即触发。</li><li>`CONNECT_PERSIST`（值 `2`）— 持久连接：对象序列化时会被保存；编辑器信号面板创建的连接均为持久连接（连接到 lambda 函数无法持久化）。</li><li>`CONNECT_ONE_SHOT`（值 `4`）— 一次性连接：发射一次后自动断开。</li><li>`CONNECT_REFERENCE_COUNTED`（值 `8`）— 引用计数连接：同一可调用对象可多次连接，每次断开计数减一，计数归零时才完全断开。</li><li>`CONNECT_APPEND_SOURCE_OBJECT`（值 `16`）— 发射时自动将源对象追加到信号原始参数之后。</li></ul> |

# 常量

| 分类 | 常量 |
| --- | --- |
| 生命周期通知 | <ul><li>`NOTIFICATION_POSTINITIALIZE`（值 `0`）— 对象初始化完成、脚本附加之前收到的通知（内部使用）。</li><li>`NOTIFICATION_PREDELETE`（值 `1`）— 对象即将被删除时收到的通知，类似于析构函数，按反向顺序发送。</li><li>`NOTIFICATION_EXTENSION_RELOADED`（值 `2`）— 对象完成热重载时收到的通知，仅对扩展类及其派生类发送。</li></ul> |

> 说明：截至当前文档版本，Object 类的方法、信号、枚举与常量均无被标注为废弃（deprecated）的成员，因此无需列出替换项。
