# Inline Class 将类内联化

某个类没有做太多事情。将这个类的所有特性搬移到另一个类中，然后移除原类。

##动机
Inline Class正好与Extract Class相反。如果一个类不再承担足够责任、不再有单独存在的理由（这通常是因为此前的重构动作移走了这个类的责任），我就会挑选这一“萎缩类”的最频繁用户（也是个类），以Inline Class手法将“萎缩类”塞进另一个类中。

##做法
* 在目标类身上声明源类的public协议，并将其中所有函数委托至源类。
  * 如果“以一个独立接口表示源类函数”更合适的话，就应该在内联之前先使用Extract Interface。
* 修改所有源类引用点，改而引用目标类。
  * 将源类声明为private,以斩断包之外的所有引用可能。同时修改源类的名称，这便可使编译器帮助你捕捉到所有对于源类的隐藏引用点。
* 编译，测试。
* 运用Move Method和Move Field,将源类的特性全部搬移到目标类。
* 为源类举行一个简单的“丧礼”