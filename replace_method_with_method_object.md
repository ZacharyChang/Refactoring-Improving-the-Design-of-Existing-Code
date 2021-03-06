# Replace Method with Method Object 以函数对象取代函数

你有一个大型函数，其中对局部变量的使用使你无法采用Extract Method。将这个函数放进一个单独对象中，如此一来局部变置就成了对象内的字段。然后你可以在同一个对象中将这个大型函数分解为多个小型函数。

##动机

我在本书中不断向读者强调小型函数的优美动人。只要将相对独立的代码从大型函数中提炼出来，就可以大大提高代码的可读性。

但是，局部变量的存在会增加函数分解难度。如果一个函数之中局部变量泛滥成灾，那么想分解这个函数是非常困难的。Replace Temp with Query可以助你减轻这一负担，但有时候你会发现根本无法拆解一个需要拆解的函数。这种情况下, 你应该把手伸进工具箱的深处，祭出函数对象(method object)[Beck]这件法宝。

Replace Method with Method Object会将所有局部变量都变成函数对象的字段。然后你就可以对这个新对象使用Extract Method创造出新函数，从而将原本的大型函数拆解变短。

##做法

* 建立一个新类，根据待处理函数的用途，为这个类命名。
* 在新类中建立一个final字段，用以保存原先大型函数所在的对象。我们将这个字段称为“源对象”。同时，针对原函数的每个临时变量和每个参数，在新类中建立一个对应的字段保存之。
* 在新类中建立一个构造函数，接收源对象及原函数的所有参数作为参数。 
* 在新类中建立一个compute ()函数。
* 将原函数的代码复制到compute()函数中。如果需要调用源对象的任何函数，请通过源对象字段调用。
* 编译。
* 将旧函数的函数本体替换为这样一条语句：“创建上述新类的一个新对象，而后调用其中的compute()函数”。

现在进行到很有趣的部分了。由于所有局部变量现在都成了字段，所以你可以任意分解这个大型函数，不必传递任何参数。
