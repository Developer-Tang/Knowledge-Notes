## 线程创建方式

### 继承Thread类

> Thread类本质上是实现了Runnable接口的一个实例，代表一个线程的实例。启动线程的唯一方法就是通过Thread类的start()实例方法。start()方法是一个native方法，它将启动一个新线程，并执行run()方法。

```java
public class MyThread extends Thread { 
    public void run() { 
        System.out.println("MyThread.run()"); 
    }
    public static void main(String[] args){
        MyThread myThread1 = new MyThread(); 
        myThread1.start();
    }
} 
```

### 实现Runnable接口

```java
public class MyRunnable extends OtherClass implements Runnable { 
    public void run() { 
        System.out.println("MyThread.run()"); 
    }
    public static void main(String[] args){
        Runnable myRunnable = new MyRunnable();
        Thread thread = new Thread(myRunnable); 
        thread.start();
    }
}
```

### Callable与Future、FutureTask

- **Callable:**
    - 可以获取线程的执行结果,也称为返回值
    - 通过与Future的结合,可以实现利用Future来跟踪异步计算的结果
- **Runnable和Callable的区别:**
    - Callable规定的方法是call(),Runnable规定的接口是run()
    - Callable的任务执行后可返回值,而Runnable的任务是不能有返回值的
    - call方法可以抛出异常,run方法不可以
    - 运行Callable任务可以拿到一个Future对象,表示异步计算的结果,它提供了检查是否计算完成的方法,以等待计算的完成,并检索计算的结果,通过Future对象可以了解任务执行情况,可以取消任务的执行,还可以获取执行结果
- **Future接口:**
    - Future是一个接口,代表了一个异步计算的结果,接口中的方法用来检查计算是否完成,等待完成和得到计算结果
    - 当计算完成后,只能通过get()方法得到结果,get()方法会阻塞,一直到线程的计算结果完成并返回
    - 如果想取消,那么调用cancel()方法,其他方法用于确定任务是正常完成还是取消了
    - 一旦计算完成了,那么这个计算就不能被取消
- **FutureTask类:**
    - FutureTask类实现了RunnableFuture接口,而RunnableFuture接口是继承了Runnable和Future接口,所以说FutureTask是一个提供异步计算结果的任务
    - FutureTask可以用来包装Callable或者Runnable接口的实现对象,因为FutureTask实现了Runnable接口,所以FutureTask也可以提交给线程池

> 实现方式一：

```java
import java.util.Random;
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;
public class UseCallable {
    /**
     * 实现Callable接口的线程
     */
    private static class UseCall implements Callable<Integer>{
        private int sum;
        @Override
        public Integer call() throws Exception {
            System.out.println("callable子线程开始执行任务计算");
            Thread.sleep(2000);
            for (int i = 0; i < 5000; i++) {
                sum += i;
            }
            System.out.println("子线程任务计算完成,返回值:"+sum);
            return sum;
        }
    }

    public static void main(String[] args) throws ExecutionException, InterruptedException {
        UseCall useCall = new UseCall();
        // 使用FutureTask包装
        FutureTask<Integer> futureTask = new FutureTask<>(useCall);
        // 包装为Thread
        Thread thread = new Thread(futureTask);
        thread.start();
        // 开始主线程的任务
        Random random = new Random();
        SleepTools.second(1);
        if(random.nextBoolean()){
            System.out.println("获取Callable result:"+futureTask.get());
        }else{
            System.out.println("中断计算");
            // 中断计算,取消线程的执行
            futureTask.cancel(true);
        }
    }
}
```

> 实现方式二：

```java
UseCall useCall = new UseCall();
// 创建一个线程池
ExecutorService executorService = Executors.newCachedThreadPool();
Future<Integer> future = executorService.submit(useCall);
```

## 四种线程池

### newCachedThreadPool

> 创建一个可根据需要创建新线程的线程池，但是在以前构造的线程可用时将重用它们。对于执行很多短期异步任务的程序而言，这些线程池通常可提高程序性能。调用execute将重用以前构造的线程（如果线程可用）。如果现有线程没有可用的，则创建一个新线程并添加到池中。终止并从缓存中移除那些已有60秒钟未被使用的线程。因此，长时间保持空闲的线程池不会使用任何资源。

### newFixedThreadPool

> 创建一个可重用固定线程数的线程池，以共享的无界队列方式来运行这些线程。在任意点，在大多数nThreads线程会处于处理任务的活动状态。如果在所有线程处于活动状态时提交附加任务，则在有可用线程之前，附加任务将在队列中等待。如果在关闭前的执行期间由于失败而导致任何线程终止，那么一个新线程将代替它执行后续的任务（如果需要）。在某个线程被显式地关闭之前，池中的线程将一直存在。

### newScheduledThreadPool

> 创建一个线程池，它可安排在给定延迟后运行命令或者定期地执行

```java
ScheduledExecutorService scheduledThreadPool= Executors.newScheduledThreadPool(3); 
scheduledThreadPool.schedule(newRunnable(){ 
    @Override 
    public void run() {
        System.out.println("延迟三秒");
    }
}, 3, TimeUnit.SECONDS);
scheduledThreadPool.scheduleAtFixedRate(newRunnable(){ 
    @Override 
    public void run() {
        System.out.println("延迟 1 秒后每三秒执行一次");
    }
},1,3,TimeUnit.SECONDS)
```

### newSingleThreadExecutor

> Executors.newSingleThreadExecutor()返回一个线程池（这个线程池只有一个线程）,这个线程池可以在线程死后（或发生异常时）重新启动一个线程来替代原来的线程继续执行下去

## 线程的生命周期

> 当线程被创建并启动以后，它既不是一启动就进入了执行状态，也不是一直处于执行状态。在线程的生命周期中，它要经过新建（New）、就绪（Runnable）、运行（Running）、阻塞（Blocked）和死亡（Dead）5种状态。尤其是当线程启动以后，它不可能一直"霸占"着CPU独自运行，所以CPU需要在多条线程之间切换，于是线程状态也会多次在运行、阻塞之间切换

### 新建（NEW）

> 当程序使用new关键字创建了一个线程之后，该线程就处于新建状态，此时仅由JVM为其分配内存，并初始化其成员变量的值

### 就绪（RUNNABLE）

> 当线程对象调用了start()方法之后，该线程处于就绪状态。Java 虚拟机会为其创建方法调用栈和程序计数器，等待调度运行

### 运行（RUNNING）

> 如果处于就绪状态的线程获得了CPU，开始执行run()方法的线程执行体，则该线程处于运行状态

### 阻塞（BLOCKED）

> 阻塞状态是指线程因为某种原因放弃了cpu使用权，也即让出了cpu timeslice，暂时停止运行。直到线程进入可运行(runnable)状态，才有机会再次获得cpu timeslice转到运行(running)状态。阻塞的情况分三种：
>
> - **等待阻塞(o.wait->等待对列)：**运行(running)的线程执行 o.wait()方法，JVM 会把该线程放入等待队列(waitting queue)
    > 中。
> - **同步阻塞(lock->锁池)：**运行(running)的线程在获取对象的同步锁时，若该同步锁被别的线程占用，则 JVM 会把该线程放入锁池(lock pool)中。
> - **其他阻塞(sleep/join)：**运行(running)的线程执行 Thread.sleep(long ms)或 t.join()方法，或者发出了 I/O 请求时，JVM 会把该线程置为阻塞状态。当sleep()状态超时、join()等待线程终止或者超时、或者 I/O处理完毕时，线程重新转入可运行(runnable)状态。

### 线程死亡（DEAD）

> 线程会以下面三种方式结束，结束后就是死亡状态
>
> - **正常结束：**run()或 call()方法执行完成，线程正常结束
> - **异常结束：**线程抛出一个未捕获的 Exception 或 Error
> - **调用stop：**直接调用该线程的 stop()方法来结束该线程—该方法通常容易导致死锁，不推荐使用

### 生命周期流程

![](JUC与多线程/Java线程的生命周期.drawio.svg)



> 后续待补充，知识储备补充后完善
