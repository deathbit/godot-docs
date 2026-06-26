# RefCounted

引用计数对象的基类，内部维护引用计数，当不再被引用时自动释放，无需手动调用 free，是 Resource 等众多辅助对象的基类。

# 方法
## 引用计数
- get_reference_count
- init_ref
- reference
- unreference
