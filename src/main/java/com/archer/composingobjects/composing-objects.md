##### 组合对象

- 类的不变约束：用来判定类的某一状态是非法的还是合法的。例如一个计数器类，持有一个long类型的域value，那么任意时刻，value的值都必须在long类型能表示的范围空间内，不能发生下溢或上溢；或者对于一个表示范围的类，任意时刻它的下界都不能大于它的上界。

- 操作的后验条件：用来指出操作的状态转换是非法的还是合法的。拿计数器类来说，如当前value等于5，那么value的下一个值必须是6。

- 基于状态的先验条件：例如无法从空队列中删除一个元素。