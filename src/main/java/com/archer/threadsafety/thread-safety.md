#### 线程安全

- 编写线程安全的代码，本质上就是管理对状态的访问，而且通常都是共享的、可变的状态。

- 通俗的说，一个对象的状态就是它的数据，存储在状态变量中，比如实例变量和类变量；对象的状态还包括了其他附属对象的状态。也就是说一个对象的状态包含了任何会对它外部可见行为产生影响的数据。

- 所谓共享，是指一个变量可以被多个线程访问；所谓可变，是指变量的值在其生命周期内可以改变。

- 无论何时，只要有多于一个的线程访问给定的状态变量，而且其中某个线程会写入该变量，此时必须使用同步来协调线程对该变量的访问。

- 线程安全的关键在于"正确性"，正确性意味着一个类与它的规约保持一致。良好的规约定义了用于强制对象状态的不变约束以及描述操作影响的后验条件。例如对于有界队列的入队操作，队列已满时不能插入新元素是它的不变约束，如果成功插入新元素，队列的长度会递增是它的后验条件。

- 无状态(stateless)的对象永远是线程安全的。对无状态对象来说，它不包含任何属性也没有引用其他类的属性，它不能保存数据，因而是线程安全的。

- 当计算的正确性依赖于运行中相关的时序或线程交替执行的顺序，会产生竞争条件。最常见的一种竞争条件是"先检查后执行"，这可能会导致使用一个潜在过期的数据作为判定下一步执行的依据。

- 竞争条件的诱因：为获取期望的结果，需要依赖相关事件的分时。竞争条件的特点：使用潜在的过期观察值在做决策或执行计算。

- 当只向无状态的类中加入唯一的状态元素，而这个状态完全被线程安全的对象所管理，那么新的类仍然是线程安全的。

- 当一个不变约束涉及多个变量时，变量之间不是彼此独立的：某个变量的值会制约其他几个变量的值，因此更新一个变量的时候，要在同一个原子操作中更新其它几个。

- 为了维护状态的一致性，要在单一的原子操作中更新相互关联的状态变量。

- 用锁来协调访问变量时，每次访问变量都需要用同一把锁。

- 对于每个可被多个线程访问的可变状态变量，如果每个访问它的线程在执行是都占有同一把锁，这种情况下，我们称这个变量是被这个锁保护的。

- 对于每一个涉及多个变量的不变约束，需要同一个锁保护其所有的变量。