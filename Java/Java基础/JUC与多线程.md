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

