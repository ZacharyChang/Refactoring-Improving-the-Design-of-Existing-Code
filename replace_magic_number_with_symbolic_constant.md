# Replace Magic Number with Symbolic Constant 以字面常量取代魔法数

你有一个字面数值，带有特别含义。创造一个常量，根据其意义为它命名，并将上述的字面数值替换为这个常量。

##动机

在计算科学中，魔法数（magic number)是历史最悠久的不良现象之一。所谓魔法数是指拥有特殊意义，却又不能明确表现出这种意义的数字。如果你需要在不同的地点引用同一个逻辑数，魔法数会让你烦恼不已,因为一旦这些数发生改变， 你就必须在程序中找到所有魔法数，并将它们全部修改一遍，这简直就是一场噩梦。就算你不需要修改，要准确指出每个魔法数的用途，也会让你颇费脑筋。

许多语言都允许你声明常量。**常量不会造成任何性能开销，却可以大大提高代码的可读性**。

进行本项重构之前，你应该先寻找其他替换方案。你应该观察魔法数如何被使用，而后你往往会发现一种更好的使用方式。如果这个魔法数是个类型码，请考虑使用Replace Type Code with Class;如果这个魔法数代表一个数组的长度，请在遍历该数组的时候，改用Array.length()。

##做法

* 声明一个常量，令其值为原本的魔法数值。
* 找出这个魔法数的所有引用点。
* 检査是否可以使用这个新声明的常量来替换该魔法数。如果可以，便以此常量替换之。
* 编译。
* 所有魔法数都被替换完毕后，编译并测试。此时整个程序应该运转如常，就像没有做任何修改一样。
  * 有个不错的测试办法：检查现在的程序是否可以被你轻松地修改常量值 (这可能意味某些预期结果将有所改变，以配合这一新值。实际工作中并非总是可以进行这样的测试）。如果可行，这就是一个不错的手法。