#### 避免活跃度危险

- 当一个线程永远占有一个锁，而其他线程尝试去获得这个锁，那它们将被永远阻塞。

- 当线程A拥有锁L想获得锁M，线程B拥有锁M想获得锁L，两个线程将永久等待下去(最简单的死锁情况)。

- 如果所有线程以通用固定的顺序获得锁，就不会出现锁顺序死锁。也就是说只要保证同时请求锁L和锁M的任一线程，都是按照先L后M的顺序请求锁，就不会发生死锁。

- 资源死锁发生的情形和锁顺序死锁类似。

- 需要等待其他任务的结果的任务是生成线程饥饿死锁的来源(因此有界池和相互依赖的任务不能放在一起使用)。