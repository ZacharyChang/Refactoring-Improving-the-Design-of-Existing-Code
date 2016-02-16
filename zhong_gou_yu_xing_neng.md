# 重构与性能

虽然重构可能使软件运行更慢，但它也使软件的性能优化更容易。除了对性能有严格要求的实时系统，其他任何情况下“编写快速软件”的秘密就是：首先写出可调的软件，然后调整它以求获得足够速度。

我看过二种编写快速软件的方法。其中最严格的是时间预算法，这通常只用于性能要求极卨的实时系统。如果使用这种方法，分解你的设计时就要做好预算，给每个组件预先分配一定资源——包括时间和执行轨迹。每个组件绝对不能超出自己的预兑，就算拥有组件之间调度预配时间的机制也不行。

第二种方法是持续关注法。这种方法要求任何程序员在任何时间做任何事时，都要设法保持系统的高性能。这种方式很常见，感觉上很有吸引力，但通常不会起太大作用。任何修改如果楚为了提高性能，通常会使程序难以维护，继而减缓开发速度。

**关于性能，一件很有趣的事情是：如果你对大多数程序进行分析，就会发现它把大半时间都耗费在一小半代码身上。**

第三种性能提升法就是利用上述的90%统计数据。采用这种方法时，你编写构造良好的程序，不对性能投以特别的关注，直至进入性能优化阶段——那通常是在开发后期。一旦进入该阶段，你再按照某个特定程序來调整程序性能。

在性能优化阶段，你首先应该用一个度最工具来监控程序的运行，让它告诉你程序中哪些地方大量消耗时间和空间。这样你就可以找出性能热点所在的一小段代码。然后你应该集中关注这些性能热点，并使用持续关注法中的优化手段来优化它们。由于你把注意力都集中在热点上，较少的工作量便吋显现较好的成果。即便如此你还是必须保持谨慎。和重构一样，你应该小幅度进行修改。每走一步都需要编译、测试、再次度童。如果没能提高性能，就应该撤销此次修改。你应该继续这个“发现热点、去除热点”的过程，直到获得客户满意的性能为止。