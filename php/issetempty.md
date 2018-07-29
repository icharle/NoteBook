# PHP中isset、empty的区别

## 总结

* `empty` 用于判断一个变量是否为空，如果变量是**非空或者非零值**，则返回**FALSE**，否则返回**TRUE**
* `isset` 用于判断变量是否已存在，如果**变量存在并且非null**则返回**TRUE**，否则返回**FALSE**


或许单单一个概念很难理解，下面用具体例子说明：

```
#empty函数
empty(0)        # bool(true)
empty("0")      # bool(true)
empty(null)     # bool(true)
empty(false)    # bool(true)
empty([])       # bool(true)

#isset函数
isset(0)        # bool(true)
isset("0")      # bool(true)
isset(null)     # bool(false)
isset(false)    # bool(true)
isset([])       # bool(true)

```

