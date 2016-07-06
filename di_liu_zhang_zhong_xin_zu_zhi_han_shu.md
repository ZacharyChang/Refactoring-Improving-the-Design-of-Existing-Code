# 第六章 重新组织函数

对付过长函数，一项重要的重构手法就是Extract Method，它把一段代码从原先函数中提取出来，放进一个单独函数中。Inline Method正好相反：将一个函数调用动作替换为该函数本体。如果在进行多次提炼之后，意识到提炼所得的某些函数并没有做任何实质事情，或如果需要回溯恢复原先函数，我就需要Inline Method。

Extract Method最大的困难就是处理局部变量，而临时变最则是其中一个主要的困难源头。处理一个函数时，我喜欢运用Replace Temp with Query去掉所有可去掉的临时变量。如果很多地方使用了某个临时变量，我就会先运用Spilt Temporary Variable将它变得比较容易替换。

但有时候临时变量实在太混乱，难以替换。这时候我就需要使用Replace Method with Method Object。它让我可以分解哪怕最混乱的函数，代价则是引入一个新类。

参数带来的问题比临时变量稍微少一些，前提是你不在函数内赋值给它们。如 果你己经这样做了，就得使用Remove Assignments to Parameters。

函数分解完毕后，我就可以知道如何让它工作得更好。也许我还会发现算法可以改进，从而使代码更清晰。这时我就使用Substitute Algorithm引入更清晰的算法。


