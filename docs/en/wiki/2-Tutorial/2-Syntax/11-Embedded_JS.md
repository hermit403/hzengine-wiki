# 内嵌 JS（实验性）

::: warning 注意
目前我们不推荐动态执行 JavaScript 代码，因为 HZengine 设计为中心化分发模式，随意执行来历不明的代码会造成严重的安全隐患。请避免在您的脚本中使用内嵌 JS 特性，如有需求请联系 HZengine 开发组。
:::

目前内嵌 JS 的语句有两种：eval 和 script。

## eval 语句

eval 语句是单行语句，用来动态执行后面的 JS 代码。eval 语句将在 new Function 中执行，并注入 gd 和 sd 两个参数（分别代表全局数据和存档数据）。使用不当可能会造成对全局环境中的变量的误操作。对于 hzs 内嵌的表达式求值，我们将用独立的表达式沙盒引擎代替 eval，以保证安全。

## script 语句

script 语句是多行语句，由 `script` 开始命令和 `end script` 结束命令组成。可以用来运行多行 JS 语句。传递的参数和注意事项同上。

## 异常捕捉

当动态执行的 JS 语句抛出异常时，引擎不会终止运行，而是将错误信息输出到日志中，再继续运行。
