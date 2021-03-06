## 进程的结构

1. 进程的定义：一个其中运行着一个或多个线程的地址空间和这些线程所需要的系统资源

2. 进程的组成：代码，数据，变量，打开的文件和环境

3. 每个进程有唯一的PID

4. 数字1一般给init进程

5. Linux进程不能用来对存放着代码的内存区域进行写操作

6. 进程运行中，有的内容是共享的，比如一个库的代码，也有的内容是不能共享的，如变量。

7. 每个进程有自己的专属环境。

8. 可以同时运行的进程数量与用于建立进程表项的内存容量有关。

9. 进程的TTY就是显示从哪一个终端启动的。

10. 进程的状态：

| 代码 | 含义 |
| --- | --- |
| S | 睡眠，等待某个事件发生 |
| R | 运行，处在运行队列里 |
| D | 不可中断的睡眠，等待输入输出 |
| T | 停止 |
| Z | 死或僵尸 |
| N | 低优先级 |
| s | 进程是会话期首进程 |
| + | 进程属于前台进程组 |
| l | 进程是多线程的 |
| < | 高优先级任务 |

11. init进程是所有进程的祖先

12. 进程调度：一般来说，优先级高的被频繁分配时间片，一个进程的优先级与其nice值有关，nice值越高，优先级越低，进程运行得越连续，nice值就越高，那些经常中断的进程nice值降低，优先级提高。可以查看进程的nice值，通过`ps -l`，也可以修改nice值，`nice <程序名>`可以将进程的nice值提高10，利用`renice <值> <PID>`可以调整一个进程的nice值。

13. PPID是进程的父进程的ID，父进程没有了，就记作1（init）