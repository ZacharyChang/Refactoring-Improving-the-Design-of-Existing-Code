# 异曲同工的类 Alternative Classes with Different Interfaces

如果两个函数做同一件事，却打着不同的签名，请运用Rename Method根据它们的用途重新命名。但这往往不够，请反复运用Move Method将某些行为 移入类，直到两者的协议一致为止。如果你必须重复而赘余地移入代码才能完成这些，或许可运用Extract Superclass为自己赎点罪。
