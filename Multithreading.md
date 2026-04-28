# Multitasking :
The concept of Multitasking is basically taken from human behaviour. For example ,sometime we do chatting on whatsapp and we talk on phone
also simultaneously.
So the same concept is use in computer for example we use vlc media player and downloading the song simultaneously.

** So performing more then one task at same time is known as Multitasking**


## Types of Multitasking :
   
### Process based Multitasking :
It means the ability to execute multiple program(process) at the same time .
For e.g. We are using vlc media player to play music and creating a java program in notepad simultaneously.

### Thread based Multitasking :
 It is the ability to execute several parts of the same program at the same time.
 For e.g. When we type in MS word at the same time the spelling checker is activates and modify if any mistake arise.Since typing and spelling
 checker and spelling modiifer perform in a single program (process) itself is known  thread based multitasking.
 

## Advantage of Multitasking :
Whether it is process based or thread based , the main objective is to reduce response time of system and to improve performance


## Main important application areas of multithreding are :
1. To develop multimedia graphics.
2. To develop animations.
3. To develop video games.

## What is thread ?
A thread is a smallest unit of execution within a process. It is like a light weight  sub-process that run independtly but share the same memory
of parent process.

## Simultaneously meaning :

Generally we think that multiple process are executing simultaneously but actually they execute one by one .Beacuse the speed of CPU is very fast
so that it appears as they are executed simultaneously. To execute a process so many process scheduling algorithms we use such as-

1. First come First Serve.
2. Shostest job-next.
3. Priority scheduling.
4. Shortest-Remaining time.
5. Round-Robin scheduling.
6. Multiple-level queues scheduling.

## Process Scheduling :
The act of determining which process is in the ready state , and should be moved to running state is known as Process scheduling. The prime
aim of process scheduling  system is to keep the CPU busy all time and to deliver minimum response time for all progress.

## Difference between process and thread -

 1. A process is an independent program in execution within its own memory space.
 1. A thread is light weight  process that share memory with other threads in same process.
 
 2. Process is heavy weight.
 2. Thread is light weight.
 
 3. Cost of communication b/w process is high  because ,switching from one process to another required some time for saving and loading
    registers.
 3. Cost of communication between thread is low.
 
 
 ## In how many ways we can create thead :
 1. By extending thread class.
 2. By implementing Runnable interface.
 
 ## Which is better way to create thread  ?
 Runnable interface is better to create thread , because here we have also a facility to apply inheritence.
 
 # Case ::
 
 ##  case 1:  Thread scheduler 
     
	 It is a part of JVM , it is responsible to schedule threads i.e.  if multiple threads are waiting to get a chance of execution then in which
	 order threads  will be executed ,is decided by scheduler.
	 We can't expect exact order followed by thread scheduler , it is varied from jvm to jvm ,hence we can't expect thread execution order and 
	 exact output .
	 
 
##   case 2:  Importance of thread  class start() method 
    
	Thread class start() method is responsible to reister thread with thread scheduler.

##  case 3 : overloading of run() method 

      Overloading of run()   method  is always  possible , but thread class Thread class start() method can invoke no arguement run() method 
	  the other overloaded method we have to call explicitly like a normal method call.
	  
## case 4 : If we not overriding run method -
       
	   If we not overriding run() method , then thread class run() method  will be executed which  has emplty implemnetation.Hence we won't get
	   any output .
	   
##  case 5 : overriding of start() method 
        If we override start() method, then our start() method will be executed  just like a normal method call and new thread won't be created.
		
		
## case 6  : After starting a thread if we are trying to restart the same thread then we will get RuntimeException saying :

        IllegalThreadStateException.
		

#  Methods :
 
 1 . start() method 
         
		  public void start()->
		  
		  When we call a start() method , a new thread is started and the run() method is executed.

2.  sleep() method 

   a. public static native void sleep(long millisec)  throws InterruptedException <br>
   b. public static native void sleep(long miilisec , int nanosec)  throws InterruptedException
   
    If a thread don't want to perform any operation for a particular amount of time then we should go for sleep() method.
	
3. stop() method  - It is depcreated

          Synatx: 
          public final void stop()
		 
		 In java , the stop() method belongs to the Thread class and was originally used to forcefully terminate a thread
		 
		 ⚠️ Why is stop() deprecated
		 stop() is considered unsafe and was deprecated because:

			1. ❌ Unsafe termination
			It kills the thread instantly.
			The thread may be in the middle of critical work.
			
			2. ❌ Leaves objects in inconsistent state
			If a thread is modifying shared data and gets stopped:
			Data may become corrupted.
			Leads to unpredictable behavior.
			
			3. ❌ Releases locks abruptly
			If the thread holds locks, they are released suddenly.
			Other threads may access half-updated data.
			

4.    suspend method() -It is deprecated 
       
     
		  Syntax :
		  public final void suspend()
		  
		  Temproarily pauses the execution of a thread without terminating it.
		  
		  
		  Why  it is deprecated :
		  
		    ❌ 1. Deadlock risk
			If a thread is suspended while holding a lock:
			Other threads cannot access that resource
			Leads to deadlock
			
			❌ 2. No control over where it pauses
			Thread may pause in the middle of critical code.
			
			❌ 3. Program can freeze
			If the suspended thread is never resumed → application may hang.
			
			
5 .      resume() method - It is  deprecated 

           Syntax :
		   public final void resume()
		   
		   It resumes execution of a thread that was paused using suspend().
		   
		   Why  it is deprecated :
		   
		    ❌ 1. Deadlock issue
			If a thread is suspended while holding a lock:
			Other threads are blocked
			Even after resume(), program behavior becomes inconsistent
			❌ 2. Timing problems
			If resume() is called before suspend(), it has no effect
			Thread may remain suspended forever → ❌ program freeze
			❌ 3. No proper control
			No guarantee when the thread will resume safely
			

6        join() method :

            Syntac :
           a. public final void join()  throws InterruptedException
		   b. public final void join(long millisec)  throws InterruptedException
		   c. public final void join(long millisec, int nanosec)  throws InterruptedException
		   
		   
		   If a thread want to wait untill completing some other thread , then we should go for join() method.
		   
		   If a thread t1 wants to wait untill completing t2 then t1 has to call t2.join().If t1 executes t2.join() then immediately t1 will
		   be entered into the waiting state untill t2 completes.Once t2 completes then t1 can continue its execution.
		   
		   

7.      yield() method :

          Syntax 
		  public static void yield()
		  
		  yield() method causes to pause current executing thread to give the chance for waiting threads of same priority.If there is no waiting
		  thread or all waiting threaad have low proirity then same thread can continue its execution.If multiple threads are waiting wiht same 
		  priority then which thread will get chance  we can't expect it depends on thread scheduler.The thread which is yielded, when 
		  it will get chance once agin it depends on thread scheduler and we can't expect exatly.
		  
		  NOTE :  Some platforms won't  provide proper support for yield method .
		  
		 
# Thread Priorities :
   Every thread in java has some priority it mat be default priority generated by JVM or customized priority provided by programmer.
   The valid range of thread priority is 1 to 10 where  1 is min prioirty adn 10 is max prioirty.

## Methods :

1 .   public static Thread currentThread() :  
         
		 It returns a reference to the currently executing thread.
		 
		 -> What happend when we print currenThread Object 
		   Thread[Name of Thread , Priority of Thread, Group of Thread]


2.  public final int getpriority()

3. public final void setPriority(int p)

4. public final String getName()

5. public final void setName(String name)

6. public boolean isAlive() :

    Used in context for thread is alive or not 

### What happens when we use thread priorities less than 1 and greater then 10

    IllegalArgumentException


## Default Priority :

The default priority only for the main thread is five but for all remaining threads default priority will be inherited from parent to child
i.e. whatever priority parent thread has the same prioirty will be there for child thread.

Note :  Some platform won't provide proper support for thread safety




# Exploring Examples ::

## Example  : 
```java
class A  extends Thread
{
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println(" Child  Thread");
		}
	}
	
}
class demo1
{
	public static void main(String ar[])
	{
		
		A a1 = new  A();
		a1.start();
	}
}
```
---

## Output :

``` text
Child  Thread
Child  Thread
Child  Thread
Child  Thread
Child  Thread
```
---



## Example  :

```java
class A  extends Thread
{
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println(" Child  Thread");
		}
	}
	
}
class demo1
{
	public static void main(String ar[])
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println("Main method");
		}
		A a1 = new  A();
		a1.start();
	}
}
```

---

## Output :
``` text
Main method
Main method
Main method
Main method
Main method
 Child  Thread
 Child  Thread
 Child  Thread
 Child  Thread
 Child  Thread
```
---


##  Example :

```java

class A  extends Thread
{
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println(" Child  Thread");
		}
	}
	
}
class demo1
{
	public static void main(String ar[])
	{
		
		A a1 = new  A();
		a1.start();
		for(int i=1;i<=5;i++)
		{
			System.out.println("Main method");
		}
	}
}

```
---

## Output :

``` text
We are getting mixed output here
```

---


## Example ::

``` java
class A  extends Thread
{
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println(i);
		}
	}
	
}
class demo1
{
	public static void main(String ar[])
	{
		
		A a1 = new  A();
		A a2 = new A();
		a1.start();
		a2.start();
		
	}
}
```

---

## Output :
``` text
Mixed Output
```

---


## Example :

``` java

class A  extends Thread
{
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println(i);
		}
	}
	
}
class demo1
{
	public static void main(String ar[])
	{
		
		A a1 = new  A();
		a1.start();
		a1.start();
		
	}
}

```
---

## Output :

```text
Exception in thread "main" 1
2
3
4
5
java.lang.IllegalThreadStateException
        at java.base/java.lang.Thread.start(Thread.java:802)
        at demo1.main(demo1.java:20)
		
		
Here  exception ocuurs  because we are execution start() method twice for same thread ,but thread which will get CPU completes its
execution.
		
```

---


## Example :

```java
class A  extends Thread
{
	public void run()
	{
		for(int i=1;i<=1000;i++)
		{
			System.out.println("Run Method "+i);
		}
	}
	
}
class demo1
{
	public static void main(String ar[])
	{
		
		A a1 = new A();
		a1.start();
		try{
			Thread.sleep(100);
		}
		catch(Exception e)
		{
			
		}
		
		a1.stop();
		
	}
}

```

---

## Output ::
```text
Run Method 1
Run Method 2
Run Method 3
-
-
-
-
Run Method 670

Thread stops suddenly 
```


## Example : 

```java
class A  extends Thread
{
	public void run()
	{
		for(int i=1;i<=1000;i++)
		{
			System.out.println("Run Method "+i);
		}
	}
	
}
class demo1
{
	public static void main(String ar[])
	{
		
		A a1 = new A();
		a1.start();
		try{
			Thread.sleep(100);
		}
		catch(Exception e)
		{
			
		}
		a1.suspend();
		
		
		
		
		
	}
}
```
---

## Output :
```text
Run Method 1
Run Method 2
Run Method 3
-
-
-
-
Run Method 860

Thread suspended suddenly
```


## Example :


``` java
class A  extends Thread
{
	public void run()
	{
		for(int i=1;i<=1000;i++)
		{
			System.out.println("Run Method "+i);
		}
	}
	
}
class demo1
{
	public static void main(String ar[])
	{
		
		A a1 = new A();
		a1.start();
		try{
			Thread.sleep(100);
		}
		catch(Exception e)
		{
			
		}
		a1.suspend();
		try{
			Thread.sleep(100);
		}
		catch(Exception e)
		{
			
		}
		
		a1.resume();
		
		
		
		
		
		
	}
}
```

---

## Output :

```text
Run Method 1
Run Method 2
Run Method 3
-
-
-
-
Run Method 1000
```


## Example :

```java 
class A  extends Thread 
{
	public void run()
	{
		for(int i=1;i<=100000;i++)
		{
			System.out.println("Run method :" +i);
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		a1.start();
		
		try{Thread.sleep(1000);}catch(Exception e){}
		
		a1.suspend();
		System.out.println("__________");
		a1.resume();
		
	}
}
```

---

## Output 

``` text
a1 thread:
println() call kiya
    → System.out ka lock liya 🔒
        → suspend() call ho gaya
            → a1 freeze ho gaya
            → BUT System.out lock abhi bhi a1 ke paas hai! 🔒

Main thread:
println("__________") call kiya
    → System.out ka lock chahiye
    → a1 ke paas hai lock
    → Main thread WAIT karne laga... ♾️

resume() → kabhi reach hi nahi hua!

```
---

## Example : We can override start() Method

``` java
class A extends Thread 
{
	public void start()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println("start Method");
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		a1.start();
		for(int i =1 ;i<=5;i++)
		{
			System.out.println("Main method");
			
		}
	}
}
```
---

## Output :

``` text
start Method
start Method
start Method
start Method
start Method
Main method
Main method
Main method
Main method
Main method
```

---

## Example : 

``` java
class A extends Thread
{
	public void start()
	{
		for(int i=1;i<=5;i++)
		{
		
        super.start();
        System.out.println(i);		
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		a1.start();
		for(int i=1;i<=5;i++)
		{
			System.out.println(i);
		}
		
	}
}

```
---

## Output : 

``` text
1
Exception in thread "main" java.lang.IllegalThreadStateException
        at java.base/java.lang.Thread.start(Thread.java:802)
        at A.start(demo1.java:8)
        at demo1.main(demo1.java:18)

```
---


## Example :

``` java
class A extends Thread
{
	public void start()
	{
		super.start();
	}
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println("Run Method:"+i);
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		a1.start();
		for(int i=1;i<=5;i++)
		{
			System.out.println("Main Method"+i);
		}
		
	}
}
```

---

## Output :

```text
Mixed Output
```

---


## Example :


``` java
class A extends Thread
{
	public void start()
	{
		super.start();
	}
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println("Run Method:"+i);
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		a1.start();
		a1.start();
		for(int i=1;i<=5;i++)
		{
			System.out.println("Main Method"+i);
		}
		
	}
}

```
---

## Output :

``` text
Exception in thread "main" java.lang.IllegalThreadStateException
        at java.base/java.lang.Thread.start(Thread.java:802)
        at A.start(demo1.java:5)
        at demo1.main(demo1.java:21)
Run Method:1
Run Method:2
Run Method:3
Run Method:4
Run Method:5

```

---


## Example :

``` java
class A extends Thread
{
	public void start()
	{
		super.start();
		super.start();
	}
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println("Run Method:"+i);
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		a1.start();
		
		
	}
}
```

---

## Output :

``` text
Exception in thread "main" java.lang.IllegalThreadStateException
        at java.base/java.lang.Thread.start(Thread.java:802)
        at A.start(demo1.java:6)
        at demo1.main(demo1.java:21)
Run Method:1
Run Method:2
Run Method:3
Run Method:4
Run Method:5
```

---


## Example :

``` java
class A implements Runnable
{
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println("Run Method"+i);
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		Thread t1 = new Thread(a1);
		t1.start();
		for(int i=1;i<=5;i++)
		{
			System.out.println("Main Method"+i);
		}
	}
}
```

OR Shorter version of above program using lambda expression 

```java

class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		Thread t1 = new Thread(()->
		{
			for(int i=1;i<=5;i++)
			{
				System.out.println("Run  method "+i);
			}
		});
		t1.start();
		for(int i=1;i<=5;i++)
		{
			System.out.println("Main Method"+i);
		}
	}
}
```
---

## Output :
``` text
we are getting mixed output 
```

---

## Example :

```java
class A implements Runnable
{
	A()
	{
		A a2 = new A();
		Thread t1 = new Thread(a2);
		Thread t2 = new Thread(a2);
		t1.start();
		t2.start();
		
	}
	
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println(i);
			try{Thread.sleep(100);}catch(Exception e) {}
		}
	}
}

class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
	}
}
```
---

## Output ::
```text
StackOverFlowError
```
---


## Example :

```java
class A implements Runnable
{
	A()
	{
		
		Thread t1 = new Thread(this);
		Thread t2 = new Thread(this);
		t1.start();
		t2.start();
		
	}
	
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println(i);
			try{Thread.sleep(100);}catch(Exception e) {}
		}
	}
}

class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
	}
}
```
---

## Output ::
```text
Mixed Output
```
---


## Example :

``` java
class A 
{
	String s;
	A(String s)
	{
		this.s=s;
	}
	public void show()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println(s+" "+i);
			try{Thread.sleep(100);} catch(Exception e) {}
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A("Cut Ticket");
		A a2 = new A("Show Ticket");
		a1.show();
		a2.show();
		
		
	}
}
```
---

## Output :

```text
Cut Ticket 1
Cut Ticket 2
Cut Ticket 3
Cut Ticket 4
Cut Ticket 5
Show Ticket 1
Show Ticket 2
Show Ticket 3
Show Ticket 4
Show Ticket 5

Bad process for ticket cutting  and show ticket

```
---


## Example :

``` java
class A extends Thread
{
	String s;
	A(String s)
	{
		this.s=s;
	}
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println(s+" "+i);
			try{Thread.sleep(100);} catch(Exception e) {}
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A("Cut Ticket");
		A a2 = new A("Show Ticket");
		a1.start();
		a2.start();
		
		
	}
}

```

---
## Output :

``` text
Cut Ticket 1
Show Ticket 1
Show Ticket 2
Cut Ticket 2
Cut Ticket 3
Show Ticket 3
Cut Ticket 4
Show Ticket 4
Show Ticket 5
Cut Ticket 5

This is also a bad process for cut ticket and show ticket
```

---

## Example :

``` java
class A extends Thread
{
	String s;
	A(String s)
	{
		this.s=s;
	}
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println(s+" "+i);
			try{Thread.sleep(100);} catch(Exception e) {}
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A("aaa");
		A a2 = new A("bbb");
		a1.start();
	try {a1.join();} catch(Exception e) {}
		a2.start();
		
		
	}
}
``` 
---

## Output :

``` text 
aaa 1
aaa 2
aaa 3
aaa 4
aaa 5
bbb 1
bbb 2
bbb 3
bbb 4
bbb 5
```
---

## Example :

``` java
class A extends Thread
{
	String s;
	A(String s)
	{
		this.s=s;
	}
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println(s+" "+i);
			try{Thread.sleep(100);} catch(Exception e) {}
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A("aaa");
		A a2 = new A("bbb");
		a1.start();
	
		a2.start();
		System.out.println(a1.isAlive());
		System.out.println(a2.isAlive());
		
	}
}
```
---

## Output :

```text

true   false
false  true
true   true
false  false
```

---


## Example :

``` java
class A extends Thread
{
	String s;
	A(String s)
	{
		this.s=s;
	}
	public void run()
	{
		for(int i=1;i<=5;i++)
		{
			System.out.println(s+" "+i);
			try{Thread.sleep(100);} catch(Exception e) {}
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A("aaa");
		A a2 = new A("bbb");
		a1.start();
	
		a2.start();
		try{
			a1.join();
		} catch(Exception e){}
		
		System.out.println(a1.isAlive());
		System.out.println(a2.isAlive());
		
	}
}
```
---

## Output :

``` text
false
false/true
```

---


## Example : 

``` java

class demo1
{
	public static void main(String ar[])
	{
		System.out.println(Thread.currentThread());
	}
}


Output :

Thread[main,5,main]
Thread[thread-name, priority, thread-group-name]

```

---


## Example :

``` java
class demo1
{
	public static void main(String ar[])
	{
		System.out.println("Current Thread : "+Thread.currentThread());
		System.out.println("Current Thread  Name : "+Thread.currentThread().getName());
		Thread.currentThread().setName("aaa");
		System.out.println("Current Thread after Changing Name :" +Thread.currentThread());
		
	}
}

Output :
Current Thread : Thread[main,5,main]
Current Thread  Name : main
Current Thread after Changing Name :Thread[aaa,5,main]
```
---


## Example :

``` java
class demo1
{
	public static void main(String ar[])
	{
		System.out.println("Current Thread : "+Thread.currentThread());
		System.out.println("Current Thread  Priority : "+Thread.currentThread().getPriority());
		Thread.currentThread().setPriority(10);
		System.out.println("Current Thread after Changing Priority :" +Thread.currentThread());
		
	}
}

Output :

Current Thread : Thread[main,5,main]
Current Thread  Priority : 5
Current Thread after Changing Priority :Thread[main,10,main]
```

---

## Example :

``` java
class demo1
{
	public static void main(String ar[])
	{
		System.out.println("Current Thread : "+Thread.currentThread());
		Thread.currentThread().setPriority(11);
		
		
	}
}

Output :

Current Thread : Thread[main,5,main]
Exception in thread "main" java.lang.IllegalArgumentException
        at java.base/java.lang.Thread.setPriority(Thread.java:1149)
        at demo1.main(demo1.java:7)


```

---

## Thread Priority Constants 
``` text
public static final int MIN_PRIORITY = 1;
public static final int NORM_PRIORITY = 5;
public static final int MAX_PRIORITY = 10;
```
---


## Example :

``` java
class A  extends Thread
{
	public void run()
	{
		System.out.println(Thread.currentThread());
	}
	
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		A a2 = new A();
		a1.start();
		a2.start();
		System.out.println(Thread.currentThread());
	}
}

Output :

Thread[main,5,main]
Thread[Thread-1,5,main]
Thread[Thread-0,5,main]

Mixed outptut

```
---


## Example :

``` java
class A  extends Thread
{
	public void run()
	{
		System.out.println(Thread.currentThread());
	}
	
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		A a2 = new A();
		a1.start();
		a2.start();
		a1.setName("aaa");
		a2.setName("bbb");
		System.out.println(Thread.currentThread());
	}
}

Output :
Mixed output 

```
---

## Example :

``` java
class A  extends Thread
{
	public void run()
	{
		
	}
	
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		A a2 = new A();
		a1.start();
		a2.start();
		a1.setName("aaa");
		a2.setName("bbb");
		System.out.println(a1);
		System.out.println(a2);
	}
}

Output :

All Possible Outcomes

Case 1 — Both threads still alive
Thread[aaa,5,main]
Thread[bbb,5,main]

Case 2 — Both threads finished
Thread[aaa,5,]
Thread[bbb,5,]

Case 3 — a1 finished, a2 still alive
Thread[aaa,5,]
Thread[bbb,5,main]

Case 4 — a1 still alive, a2 finished
Thread[aaa,5,main]
Thread[bbb,5,]


The second field is thread group name, and after a thread finishes execution, its thread group can become null or empty.


```
---


# Synchronization  :


## What is Shared Resource ?

A shared resource is any data or object that is accessed by more than one thread at the same time.Because multiple threads use it together, it can cause data 
inconsistency if not handled properly.



## What is critical section ?

A critical section is a part of the code where a shared resource is accessed or modified.
👉Only one thread at a time should execute the critical section to avoid data inconsistency.


## What Is Data Inconsistency?

Data inconsistency occurs when multiple threads access and modify the same shared data at the same time, causing the data to become incorrect or unpredictable.


## What is Race Condition ?


A race condition occurs when two or more threads access shared data at the same time, which leads to  data inconsistency.


## What is  Synchronization ?

Synchronization is the tool , use to control  to a shared resources by multiple threads. Its main purpose is to prevent  a problem called a “race- condition ”.
where several threads try to change the same data at same time, leading to corrupted and unpredicatable results.


 
 
 
## Method synchronization :

By declaring the  method synchronized the entire method is treated as critical section , ensuring that only one thread can execute that method at any given time.
This approach locks the entire method preventing other thread from accessing it until the first thread finshses its execution.




## Block synchronization :
If we only need to execute some subsequent lines of code not all lines of code within a method , then we should  go  for synchronized block .


## Can a constructor be synchronized ?
No.


## What is Object level lock ?
Object level lock is a mechanism where every object in Java has a built-in lock (monitor), and when a thread enters a synchronized method or block, 
it acquires that object's lock — no other thread can enter any synchronized method of that same object until the lock is released.

## What is Class level Object ?

```text
A class-level lock is a lock that is applied on the Class object itself and is shared by all objects of that class.
In Java, class-level locking is achieved using:
•	static synchronized methods
•	synchronized(ClassName.class)


┌──────────────────────────────────────────────────────────────┐
│  - Every CLASS has ONE lock (on the .class object)          │
│  - Achieved using "static synchronized" keyword             │
│  - Only ONE thread can hold the lock at a time              │
│  - Applies across ALL objects of that class                 │
│  - Used to protect STATIC data                              │
└──────────────────────────────────────────────────────────────┘

```
---


## What is deadlock ?

A deadlock is a situation where two or more threads are stuck forever , waiting for each other’s resources and none of them can proceed.

## Deadlock VS Starvation 
``` text
	Long waiting of a thread where thread never ends is called deadlock.
	Long waiting of a thread where waiting ends at certain points is called starvation.
Eg Low priority thread has to wait until completing all high priority thread . It may be long waiting but ends at certain points which is nothing but starvation .
```
---




## Examples :

```java
class A implements  Runnable
{
	int c=0;
	public void run()
	{
	   for(int i=1;i<=50000;i++)
	   {
		   c++;
	   }
	}
}
class demo1
{
	public static void main(String ar[])
	{
		
		A a1 = new A();
		A a2 = new A();
		Thread t1 = new  Thread(a1);
		Thread t2 = new Thread(a2);
		t1.start();
		t2.start();
		System.out.println("a1="+a1.c);
		System.out.println("a2="+a2.c);
		
	}
	
}

Output :
Random numbers
```

---


## Example :

```java
class A implements  Runnable
{
	int c=0;
	public void run()
	{
	   for(int i=1;i<=50000;i++)
	   {
		   c++;
	   }
	}
}
class demo1
{
	public static void main(String ar[]) throws Exception 
	{
		
		A a1 = new A();
		A a2 = new A();
		Thread t1 = new  Thread(a1);
		Thread t2 = new Thread(a2);
		t1.start();
		t2.start();
		
		t1.join();
		t2.join();
		
		System.out.println("a1="+a1.c);
		System.out.println("a2="+a2.c);
		
	}
	
}

Output :
a1=50000
a2=50000

```
---


## Example :
``` java

class A  implements Runnable 
{
	static int c=0;
	public void run()
	{
	   for(int i=1;i<=50000;i++)
	   {
		   c++;
	   }
	}
}

class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		A a2 = new A();
		Thread t1 = new Thread(a1);
		Thread t2 = new Thread(a2);
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		System.out.println("a1="+a1.c);
		System.out.println("a2="+a2.c);
		
		
	}
}
Output :
Fixed Random Numbers
```
---

## Example :
```java
class A  implements Runnable 
{
	static int c=0;
	public synchronized void run()
	{
	   for(int i=1;i<=50000;i++)
	   {
		   c++;
	   }
	}
}

class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		A a2 = new A();
		Thread t1 = new Thread(a1);
		Thread t2 = new Thread(a2);
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		System.out.println("a1="+a1.c);
		System.out.println("a2="+a2.c);
		
		
	}
}
Output :
Fixed Any random Number
```

---

## Example :
``` java
class A  implements Runnable 
{
	
	int c=0;
	public synchronized void run()
	{
	   for(int i=1;i<=50000;i++)
	   {
		   c++;
	   }
	}
}

class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		Thread t1 = new Thread(a1);
		Thread t2 = new Thread(a1);
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		System.out.println("a1="+a1.c);
		
		
		
	}
}
Output :
100000
```
---

## Example
```java
class A  implements Runnable 
{
	
	int c=0;
	public synchronized void run()
	{
	   for(int i=1;i<=50000;i++)
	   {
		   c++;
	   }
	}
}

class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		Thread t1 = new Thread(a1);
		Thread t2 = new Thread(a1);
		t1.start();
		t2.start();
		
		System.out.println("a1="+a1.c);
		System.out.println("a1="+a1.c);
		
		
		
	}
}
Output :
Random

```
---


## Example :
``` java
class A  implements Runnable 
{
	
	int c=0;
	public synchronized void run()
	{
	   for(int i=1;i<=50;i++)
	   {
		   System.out.println(Thread.currentThread().getName()+"="+ ++c);
		   try{Thread.sleep(100);} catch(Exception e){}
		   }
	}
}

class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		
		Thread t1 = new Thread(a1);
		Thread t2 = new Thread(a1);
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		
		
		
		
		
	}
}
Ouptut :
Thread-0=1
Thread-0=2
...
Thread-0=50
Thread-1=51
Thread-1=52
...
Thread-1=100



OR 
Thread-1=1
Thread-1=2
...
Thread-1=50
Thread-0=51
Thread-0=52
...
Thread-0=100


```
---

## Example :
``` java
class A  implements Runnable 
{
	
	int c=0;
	public synchronized void run()
	{
	   for(int i=1;i<=50;i++)
	   {
		   System.out.println(Thread.currentThread().getName()+"="+ ++c);
		   try{Thread.sleep(100);} catch(Exception e){}
		   }
	}
}

class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		
		Thread t1 = new Thread(a1,"A");
		Thread t2 = new Thread(a1,"B");
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		
		
		
		
		
	}
}
Output :
Either start with Thread A or Thread B 
```
---

## Example :
```java
class A  implements Runnable 
{
	
	int c=0;
	public int getCount()
	{
		return ++c;
	}
	
	public void run()
	{
		for(int i=1;i<=50000;i++)
		{
			getCount();
		}
	}
}

class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		
		Thread t1 = new Thread(a1,"A");
		Thread t2 = new Thread(a1,"B");
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		System.out.println("a1="+a1.c);
		
		
		
		
		
	}
}
Output :
Any Random Number
```
---

## Example :
``` java
class A  implements Runnable 
{
	
	int c=0;
	public int getCount()
	{
		return ++c;
	}
	
	public  synchronized void run()
	{
		for(int i=1;i<=50000;i++)
		{
			getCount();
		}
	}
}

class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		
		Thread t1 = new Thread(a1,"A");
		Thread t2 = new Thread(a1,"B");
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		System.out.println("a1="+a1.c);
		
		
		
		
		
	}
}
Output :
100000
```
---

## Example :
```java
class A  implements Runnable 
{
	
	int c=0;
	public  synchronized int getCount()
	{
		return ++c;
	}
	
	public   void run()
	{
		for(int i=1;i<=50000;i++)
		{
			System.out.println(Thread.currentThread().getName()+"="+getCount());
		}
	}
}

class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		
		Thread t1 = new Thread(a1,"A");
		Thread t2 = new Thread(a1,"B");
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		System.out.println("a1="+a1.c);
		
		
		
		
		
	}
}

Output :
Mixed Output 
```
---

## Example :

``` java
class A  implements Runnable 
{
	
	int c=0;
	
	
	public void run()
	{
		for(int i=1;i<=50000;i++)
		{
			synchronized(this)
			{
				++c;
			}
		}
	}
}

class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		
		Thread t1 = new Thread(a1,"A");
		Thread t2 = new Thread(a1,"B");
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		System.out.println("a1="+a1.c);
		
		
		
		
		
	}
}
Output :
a1=100000
```
---

## Example 
```java
class A  implements Runnable 
{
	
	int c=0;
	public synchronized void run()
	{
		for(int i=1;i<=50000;i++)
		{
			c++;
		}
	}
	
	
	
}

class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		A a2 = new A();
		
		Thread t1 = new Thread(a1,"A");
		Thread t2 = new Thread(a2,"B");
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		System.out.println("a1="+a1.c);
		System.out.println("a2="+a2.c);
		
		
		
		
		
	}
}
Output :
50000
50000
```

----

## Example :

```java
class A  implements Runnable 
{
	
	static int c=0;
	public synchronized void run()
	{
		for(int i=1;i<=50000;i++)
		{
			c++;
		}
	}
	
	
	
}

class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		A a2 = new A();
		
		Thread t1 = new Thread(a1,"A");
		Thread t2 = new Thread(a2,"B");
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		System.out.println("a1="+a1.c);
		System.out.println("a2="+a2.c);
		
		
		
		
		
	}
}
Output :
Random but fixed 
```
---

## Example :

```java
class A  implements Runnable 
{
	
	static int c=0;
	public static synchronized void run()
	{
		for(int i=1;i<=50000;i++)
		{
			c++;
		}
	}
	
	
	
}

class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		A a2 = new A();
		
		Thread t1 = new Thread(a1,"A");
		Thread t2 = new Thread(a2,"B");
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		System.out.println("a1="+a1.c);
		System.out.println("a2="+a2.c);
		
		
		
		
		
	}
}
Output :
 error: run() in A cannot implement run() in Runnable
        public static synchronized void run()
                                        ^
  overriding method is static
  
```
---

## Example : Class level lock 

```java
class A  implements Runnable 
{
	
	static int c=0;
	
	synchronized static int getCount()
	{
		return ++c;
	}
	public  void run()
	{
		for(int i=1;i<=50;i++)
		{
			System.out.println(Thread.currentThread().getName()+"="+getCount());
		}
	}
	
	
	
}

class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		A a2 = new A();
		
		Thread t1 = new Thread(a1,"A");
		Thread t2 = new Thread(a2,"B");
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		System.out.println("a1="+a1.c);
		System.out.println("a2="+a2.c);
		
		
		
		
		
	}
}

OR
class A implements Runnable 
{
    static int c = 0;

    public void run()
    {
        for(int i = 1; i <= 50; i++)
        {
            synchronized(A.class)   // 🔥 class-level lock
            {
                System.out.println(Thread.currentThread().getName() + "=" + ++c);
            }
        }
    }
}
class demo1
{
	public static void main(String ar[]) throws Exception
	{
		A a1 = new A();
		A a2 = new A();
		
		Thread t1 = new Thread(a1,"A");
		Thread t2 = new Thread(a2,"B");
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		System.out.println("a1="+a1.c);
		System.out.println("a2="+a2.c);
		
		
		
		
		
	}
}

Output :
Mixed
```
---

## Example :
```java
class A implements Runnable
{
	int t=1;
	public void run()
	{
		if(t>=1)
		{
			t=t-1;
			System.out.println("Ticket Booked by :" +Thread.currentThread().getName());
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		Thread t1 = new Thread(a1,"A");
		Thread t2 = new Thread(a1,"B");
		t1.start();
		t2.start();
	}
}
Output : Mixed Output 
```
---

## Example :

```java
class A implements Runnable
{
	int t=5;
	public void run()
	{
		if(t>=1)
		{
			t=t-5;
			System.out.println("Ticket Booked by :" +Thread.currentThread().getName());
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		Thread t1 = new Thread(a1,"A");
		Thread t2 = new Thread(a1,"B");
		Thread t3 = new Thread(a1,"C");
		Thread t4 = new Thread(a1,"D");
		Thread t5 = new Thread(a1,"E");
		Thread t6 = new Thread(a1,"F");
		Thread t7 = new Thread(a1,"G");
		Thread t8 = new Thread(a1,"H");
		Thread t9 = new Thread(a1,"I");
		Thread t10 = new Thread(a1,"J");
		t1.start();
		t2.start();
		t3.start();
		t4.start();
		t5.start();
		t6.start();
		t7.start();
		t8.start();
		t9.start();
		t10.start();
	}
}
Output :
Mixed Output :
```
---

## Example :
``` java
class A implements Runnable
{
	int t=5;
	public void run()
	{
		if(t>=1)
		{
			t=t-1;
			System.out.println("Ticket Booked by :" +Thread.currentThread().getName());
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		String s[] = {"A", "B", "C" ,"D" , "E", "F", "G", "H", "I", "J"};
		Thread t1[] = new Thread[s.length];
		for(int i=0;i<s.length;i++)
		{
			t1[i]=new Thread(a1,s[i]);
		}
		
	    for(int i=0;i<s.length;i++)
		{
			t1[i].start();
		}
	}
}
Output :
Mixed Output 
```
---

## Example :
``` java
class A  implements Runnable
{
	B b1 ;
	A()
	{
		
	}
	A (B b1)
	{
		this.b1=b1;
	}
	
	public void run()
	{
		synchronized(b1)
		{
			for(int i=1;i<=5;i++)
			{
				System.out.println("Class A ");
			}
		}
	}
	
}
class B implements Runnable
{
	A a1 ;
	B()
	{}
	
	B(A a1 )
	{
		this.a1=a1;
	}
	
	public void run()
	{
		synchronized(a1)
		{
			for(int i=1;i<=5;i++)
			{
				System.out.println("Class B ");
			}
		
		}
	}
}

class demo1
{
	public static void  main(String ar[])
	{
		A a1= new A();
		B b1 = new B();
		
		A a11 = new A(b1);
		B b11 = new B(a1);
		
		Thread t1 =new  Thread(a11,"A");
		Thread t2 =new  Thread(b11,"B");
		
		t1.start();
		t2.start();
	}
}
Output : 
Mixed Output 
```
---

## Example :
``` java
class A  implements Runnable
{
	B b1 ;
	A()
	{
		
	}
	A (B b1)
	{
		this.b1=b1;
	}
	
	public void run()
	{
		synchronized(b1)
		{
			for(int i=1;i<=5;i++)
			{
				System.out.println("Class A ");
			}
		}
	}
	
}
class B implements Runnable
{
	A a1 ;
	B()
	{}
	
	B(A a1 )
	{
		this.a1=a1;
	}
	
	public void run()
	{
		synchronized(a1)
		{
			for(int i=1;i<=5;i++)
			{
				System.out.println("Class B ");
			}
		
		}
	}
}

class demo1
{
	public static void  main(String ar[])
	{
		A a1= new A();
		B b1 = new B();
		
		A a11 = new A(b1);
		B b11 = new B(a1);
		
		Thread t1 =new  Thread(a1,"A");
		Thread t2 =new  Thread(b1,"B");
		
		t1.start();
		t2.start();
	}
}
Output :
NullPointerException 
```
---

## Example : DeadLock through Synchronization block
``` java
class A  {}

class B {}

class C extends Thread
{
	A a1;
	B b1;
	C(A a1 , B b1)
	{
		this.a1=a1;
		this.b1=b1;
	}
	
	public void run()
	{
		System.out.println("Class C run method");
		synchronized(a1)
		{
	     System.out.println("Class C block 1");
		 synchronized(b1)
		 {
			 System.out.println("Class C block 2");
		 }
		}
	}
}

class D extends Thread
{
	A a1;
	B b1;
	D(A a1 , B b1)
	{
		this.a1=a1;
		this.b1=b1;
	}
	
	public void run()
	{
		System.out.println("Class D run method");
		synchronized(b1)
		{
	     System.out.println("Class D block 1");
		 synchronized(a1)
		 {
			 System.out.println("Class D  block 2");
		 }
		}
	}
}

class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		B b1 = new B();
		C c1 = new C(a1,b1);
		D d1 = new D(a1,b1);
		c1.start();
		d1.start();
	}
}
Output 
DeadLock 
```
---

## Example :
``` java
class A  {}

class B {}

class C extends Thread
{
	A a1;
	B b1;
	C(A a1 , B b1)
	{
		this.a1=a1;
		this.b1=b1;
	}
	
	public void run()
	{
		System.out.println("Class C run method");
		synchronized(a1)
		{
	     System.out.println("Class C block 1");
		 synchronized(b1)
		 {
			 System.out.println("Class C block 2");
		 }
		}
	}
}

class D extends Thread
{
	A a1;
	B b1;
	D(A a1 , B b1)
	{
		this.a1=a1;
		this.b1=b1;
	}
	
	public void run()
	{
		System.out.println("Class D run method");
		synchronized(new B())
		{
	     System.out.println("Class D block 1");
		 synchronized(new A())
		 {
			 System.out.println("Class D  block 2");
		 }
		}
	}
}

class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		B b1 = new B();
		C c1 = new C(a1,b1);
		D d1 = new D(a1,b1);
		c1.start();
		d1.start();
	}
}
Output : Mixed 
```
---

## Example : Example of DeadLock throuhg Synchrinized method
``` java
class A 
{
	public synchronized void show1()
	{
		System.out.println("Class A show1 method");
		
	}
	public  synchronized void show2(B b1)
	{
		System.out.println("Class A show 2 method");
		b1.show1();
	}

}
class B 
{
	public synchronized void show1()
	{
		System.out.println("class B show1 method ");
	}
	
	public synchronized void show2(A a1)
	{
		System.out.println("class B show2 method");
		a1.show1();
	}
}

class C extends Thread
{
	A a1;
	B b1;
	 C(A a1 , B b1)
	 {
		 this.a1=a1;
		 this.b1=b1;
	 }
	 
	 public void run()
	 {
		 a1.show2(b1);
	 }
}


class D extends Thread
{
	A a1;
	B b1;
	 D(A a1 , B b1)
	 {
		 this.a1=a1;
		 this.b1=b1;
	 }
	 
	 public void run()
	 {
		 b1.show2(a1);
	 }
}

class demo1
{
	public static void main(String ar[])
	{
		A a1  = new A();
		B b1 = new  B();
		C c1 = new C(a1,b1);
		D d1 = new D(a1,b1);
		
		c1.start();
		d1.start();
	}
}
Output :
Deadlock
```
---

## Example :
``` java
class A 
{
	public synchronized void show1()
	{
		System.out.println("Class A show1 method");
		
	}
	public  synchronized void show2(B b1)
	{
		System.out.println("Class A show 2 method");
		b1.show1();
	}

}
class B 
{
	public synchronized void show1()
	{
		System.out.println("class B show1 method ");
	}
	
	public synchronized void show2(A a1)
	{
		System.out.println("class B show2 method");
		new A().show1();
	}
}

class C extends Thread
{
	A a1;
	B b1;
	 C(A a1 , B b1)
	 {
		 this.a1=a1;
		 this.b1=b1;
	 }
	 
	 public void run()
	 {
		 a1.show2(b1);
	 }
}


class D extends Thread
{
	A a1;
	B b1;
	 D(A a1 , B b1)
	 {
		 this.a1=a1;
		 this.b1=b1;
	 }
	 
	 public void run()
	 {
		 b1.show2(a1);
	 }
}

class demo1
{
	public static void main(String ar[])
	{
		A a1  = new A();
		B b1 = new  B();
		C c1 = new C(a1,b1);
		D d1 = new D(a1,b1);
		
		c1.start();
		d1.start();
	}
}
Output :
Mixed output 
```
---

# wait() , wait(long) , wait(long, int) ,notify(), notifyAll()
wait() , notify() , notifyAll() all are used for inter thread communication.

## What is wait() method in java >
wait()  is a method in object  class that causes the current thread to pause execution and releases the lock(monitor) on that object ,putting
the thread into waiting state untill it is awkened by notify() or notifyAll().

## What is notify() method ?
```text
notify() method in the object  class that wake up a single thread i.e waiting thread on monitor(lock) of object.
The choosen thread moves from waiting state and it will resume execution only after it successfully re-acquires the lock.
``` 
---

## Real life scenario for both  wait() and notifyAll()
``` java
classroom-question-answer

Thread A (Student) -> has a question 

Thread B (Teacher) -> has the answer

The speaking  time in claas = monitor lock.

Flow :
Student asks a question and wait( wait() ) , giving the floor to  teacher

Teacher thinks and prepare the answer-

Teacher says : "Here the answer" (notify()) student  resumes the conversations
```
---

##  Note :
-Compulory to use wait() ,notify() and notifyAll()  inside synchronized block or method otherwise we will get  IllegalMonitorStateException.
-wait() method throws InterruptedException.


## Differnece between notify() and notifyAll()
``` java
We use notify() method  to give notification for only one waiting thread ,if multiple threads are waiting then only one thread is notify() and
remaining thread will have to wait() for further notification, which thread will be notify we can't except it depends on JVM.


notifyAll() is a method of the Java Object class that is used in thread communication.
It wakes up all threads that are waiting on the same object (monitor).

```
---



## Example :

``` java
class demo1
{
	public static void main(String ar[])
	{
		System.out.println("aaa");
		wait();
		System.out.println("bbb");
	}
}
Output :
 error: non-static method wait() cannot be referenced from a static context
```
---

## Example :
```java
class A 
{
	void show()
	{
		System.out.println("aaa");
		wait();
		System.out.println("bbb");
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		a1.show();
	}
}
Output :
error: unreported exception InterruptedException; must be caught or declared to be thrown
```
---

## Example : 
``` java
class A 
{
	void show() throws Exception 
	{
		System.out.println("aaa");
		wait();
		System.out.println("bbb");
	}
}
class demo1
{
	public static void main(String ar[]) throws Exception 
	{
		A a1 = new A();
		a1.show();
	}
}
Output :
aaa
Exception in thread "main" java.lang.IllegalMonitorStateException: current thread is not owner
```
---

## Example :
``` java
class A 
{
	void show() throws Exception 
	{
		System.out.println("aaa");
		try{
		wait();
		} catch(Exception e) {}
		System.out.println("bbb");
	}
}
class demo1
{
	public static void main(String ar[]) throws Exception 
	{
		A a1 = new A();
		a1.show();
	}
}
Output : 
aaa
bbb
```
---

##  Example :
``` java
class A 
{
	 public synchronized void show() throws Exception 
	{
		System.out.println("aaa");
		try{
		 this. wait();
		} catch(Exception e) {System.out.println("Exception Handled");}
		System.out.println("bbb");
	}
}
class demo1
{
	public static void main(String ar[]) throws Exception 
	{
		A a1 = new A();
		a1.show();
	}
}
Output :
"aaa" prints ✅
wait() is called
Thread releases the lock
Thread goes into WAITING state
❌ No other thread calls notify()

👉 So the program stops here forever
```
---

## Example : Solution for Above Problem :
``` java
class A 
{
    public synchronized void show() throws Exception 
    {
        System.out.println("aaa");
        wait();   // waiting
        System.out.println("bbb");
    }
}

class demo1
{
    public static void main(String ar[]) throws Exception 
    {
        A a1 = new A();

        // Thread that will wake up the waiting thread
        new Thread(() -> {
            try {
                Thread.sleep(1000); // wait 1 sec
                synchronized(a1) {
                    a1.notify();   // 🔔 wake up
                }
            } catch(Exception e) {}
        }).start();

        a1.show();
    }
}
Output : 
aaa
bbb 
```
---

## Example : If in Above program  we remove the Thread.sleep() method 

``` java
class A 
{
    public synchronized void show() throws Exception 
    {
        System.out.println("aaa");
        wait();   // waiting
        System.out.println("bbb");
    }
}

class demo1
{
    public static void main(String ar[]) throws Exception 
    {
        A a1 = new A();

        // Thread that will wake up the waiting thread
        new Thread(() -> {
            try {
               
                synchronized(a1) {
                    a1.notify();   // 🔔 wake up
                }
            } catch(Exception e) {}
        }).start();

        a1.show();
    }
}
Output : 

✅ Case 1: Correct execution (most expected sometimes)
Flow:
Main thread starts show()
Prints "aaa"
Calls wait() → goes to WAITING
Second thread runs → calls notify()
Main thread wakes up → prints "bbb"
Output:
aaa
bbb
❌ Case 2: Lost notification (important case)
Flow:
Second thread runs first
It acquires lock and calls notify()
❗ No thread is waiting yet → notification is lost
Main thread runs:
prints "aaa"
calls wait()
❌ No one will notify now

👉 Main thread waits forever

Output:
aaa

(Program hangs)

```
---

##  Example :
``` java
class A 
{
    public synchronized void show() throws Exception 
    {
        System.out.println("aaa");
        wait(2000);   // waiting
        System.out.println("bbb");
    }
}

class demo1
{
    public static void main(String ar[]) throws Exception 
    {
        A a1 = new A();

       
        a1.show();
    }
}
```
---

## Example :
``` java
class  A 
{
	void show()
	{
		System.out.println("ccc");
		 notify() ;
		System.out.println("ddd");
	}
	synchronized void show2()  
	{
		System.out.println("aaa");
		try {wait(); } catch (Exception e) { System.out.println("Exception  Handled in show 2 method ");}
		System.out.println();
	}
}

class demo1 
{
	public static void main(String ar[])
	{
		A a1 = new A();
		a1.show2();
		a1.show();
	}
}
Ouptut 
aaa
then stuck forever
```
---

## Example  : Solution for above problem
``` java 
class A 
{
    synchronized void show()
    {
        System.out.println("ccc");
        notify();
        System.out.println("ddd");
    }

    synchronized void show2()  
    {
        System.out.println("aaa");
        try { wait(); } catch (Exception e) {}
        System.out.println("bbb");
    }
}

class demo1 
{
    public static void main(String ar[])
    {
        A a1 = new A();

        new Thread(() -> {
			
			try {Thread.sleep(100);} catch(Exception e) {}
            a1.show();   // will notify
        }).start();

        a1.show2();  // will wait
    }
}
Output :
aaa
bbb
ccc
ddd
```
---

## Example : 
``` java
class A implements Runnable 
{
	synchronized void show1()
	{
		System.out.println("ccc");
		System.out.println("notify() method call");
		notify();
		System.out.println("ddd");
		
	}
	synchronized void show2()
	{
		System.out.println("aaa");
		System.out.println("wait method ");
		try{ wait (); } catch(Exception e) {}
		System.out.println("bbb");
	}
	
	int c=0;
	public void run()
	{
		if(c==0)
		{
			c++;
			show2();
		}
		else
			show1();
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		A a2 = new A ();
		
		Thread t1 = new Thread(a1);
		Thread t2 = new Thread(a2);
		
		t1.start();
		t2.start();
		
	}
}
Output : 
aaa
wait method
aaa
wait method
then stuck  forever 

```
---

## Example :
``` java
class A implements Runnable 
{
	synchronized void show1()
	{
		System.out.println("ccc");
		System.out.println("notify() method call");
		notify();
		System.out.println("ddd");
		
	}
	synchronized void show2()
	{
		System.out.println("aaa");
		System.out.println("wait method call  ");
		try{ wait (); } catch(Exception e) {}
		System.out.println("bbb");
	}
	
	int c=0;
	public void run()
	{
		if(c==0)
		{
			c++;
			show2();
		}
		else
			show1();
	}
}
class demo1
{
	public static void main(String ar[])
	{
		A a1 = new A();
		
		Thread t1 = new Thread(a1);
		Thread t2 = new Thread(a1);
		
		t1.start();
		t2.start();
		
	}
}
Output :
aaa
wait method call
ccc
notify() method call
ddd
bbb
```
---

## Example :
``` java
class MyThread extends Thread 
{
	int total=0;
	public void run()
	{
		synchronized(this)
		{
			System.out.println("Child thread starts calculating");
			for(int i=1;i<=100;i++)
			{
				total=total+i;
			}
			System.out.println("Chile thread give notification ");
			this.notify();
		}
	}
}
class demo1
{
	public static void main(String ar[]) throws Exception 
	{
		MyThread t = new MyThread();
		t.start();
		synchronized(t)
		{
			System.out.println("Maib thread trying to call wait() method");
			t.wait();
			System.out.println(t.total);
			
		}
		
	}
}
Ouput scenes : 

✅ Case 1: Correct order (most expected)
Flow:
Main thread enters:
synchronized(t)
Prints:
Maib thread trying to call wait() method
Calls wait() → goes to WAITING
Child thread runs:
Child thread starts calculating
Chile thread give notification
Calls notify() → wakes main thread
Main resumes:
5050
✅ Output:
Maib thread trying to call wait() method
Child thread starts calculating
Chile thread give notification
5050
⚠️ Case 2: Child runs first (lost notification)
Flow:
Child thread runs first:
Child thread starts calculating
Chile thread give notification

👉 Calls notify() ❗ (no thread is waiting → lost)

Main thread runs:
Maib thread trying to call wait() method
Calls wait()

👉 ❌ No notification now → waits forever

❌ Output:
Child thread starts calculating
Chile thread give notification
Maib thread trying to call wait() method

👉 Program hangs, 5050 never prints
```
---
## Producer-Consumer Problem 
```text
Producer thread is responsible to produce items to the queue  and consumer thread is responsible to consume items from the queue.If queue 
is empty will call wait() method and entered into waiting state , After prodcing items to the queue , producer thread  is responsible 
to call notify() method then waiting consumer will get that notification  and continue its execution with updated items.
```
---	

## DeadLock 
``` text
A DeadLock is a situation where two or more threads are stuck forever , waiting  for each other's resources and none of them can proceed.
```
---
## DeadLock vs Starvation
```text
-Long waiting of a thread where waiting never ends is called deadLock.

- Lond waiting of a thread where waiting enda at certain point  is called starvation.

Eg. Low priority  thread has to wait untill completing all high prioirty threads. It may be long waiting but ends at certain point which
is nothing but a starvation.

```
---

## Daemon Threads :
``` text
The thread which is executing in the backgroud is called daemon thread.
Eg Garbage collector ,AttachListener, Signal Dispatcher.

The main objective of daemon threads is to provide support for non-daemon thread(main thread).

Eg :
If the main thread runs wiht low memory then jvm runs GC to destroy useless objects so that no. of bytes of free memory will be improved,
with this free memory main thread can continue its execution/

Usually daemon thread having low priorit but based on our requirement daemon threads can run with higher priority also.

Two Method--:
1.public boolean isDaemon()
2. public void setDaemon(boolean b)

If we are using setDaemon() method after starting the thread then we will get IllegalThreadStateException

By default main thread is always non-daemon  and for all remaining threads, daemon nature will be inherited from parent to child.


When last non-daemon thread terminates automatically all daemon threads will be terminated irrespective of their position.

```
---


## ThreadGroup :
``` text 
Based on functionality we can group threads into a single unit which is nothing but Thread group i.e.  thread group  contains a group of threads.
In addition to threads , thread group can  also contain sub-thread groups.


The main advantage of maintaining threads in form of thread group is we can perform thread group very easily.


Every thread in java belongs to some group , main thread belongs to main  group , every thread  group in java is child  group directly
or indirectly . Hence System group acts as a root for all thread groups in java.


System group contains several system level threads , like finalizer , reference handler, signal dispatcher, attachListener


System.out.println(Thread.currenThread().getThreadGroup().getName());
System.out.println(Thread.currenThread().getThreadGroup().getParent());
System.out.println(Thread.currenThread().getThreadGroup().getParent().getName());


ThreadGroup :

ThreadGroup is a class and directly extedns object class

Constructor :

1️⃣ ThreadGroup(String name)
ThreadGroup tg = new ThreadGroup("MyGroup");

👉 Creates a new thread group with:

Given name
Parent = current thread’s group
2️⃣ ThreadGroup(ThreadGroup parent, String name)
ThreadGroup parent = new ThreadGroup("ParentGroup");
ThreadGroup child = new ThreadGroup(parent, "ChildGroup");

👉 Creates:

A child thread group
Under a specified parent group
```
---


``` java
setMaxPriority() does NOT affect already created threads
It only restricts future threads

class demo1
{
	public static void main(String ar[])
	{
	
	 ThreadGroup g1 = new ThreadGroup("tg");
	 Thread t1  = new Thread(g1,"Thread_1");
	 Thread t2  = new Thread(g1,"Thread_2");
	 
	 g1.setMaxPriority(3);
	 Thread t3  = new Thread(g1,"Thread_3");
	 System.out.println(t1.getPriority());
	 System.out.println(t2.getPriority());
	 System.out.println(t3.getPriority());
	 
	}

}
5
5
3
``` 
---
# java.util.concurrent package 


## Problems before concurrent package 
```text

1. Thread Management Complexity :
Creating and managing thread manually  is messy.

2.  Deadlocks from Poor Locking → Solved by ReentrantLock, tryLock()
Problem: synchronized blocks could deadlock with no way to timeout or back off.


3. Race Conditions → Solved by Atomic classes & Locks
Problem: Multiple threads reading/writing shared data simultaneously causes unpredictable results.

4. No Way to Return Results from Threads → Solved by Callable + Future

5. Thread Coordination was Error-Prone → Solved by CountDownLatch, CyclicBarrier
Problem: Using wait()/notify() for coordination was fragile and hard to understand.


6. Unsafe Shared Collections → Solved by Concurrent Collections
Problem: HashMap, ArrayList etc. throw ConcurrentModificationException or corrupt data under concurrent access.


7. Blocking I/O Wasted Threads → Solved by BlockingQueue + thread pools
Problem: Threads would sit idle waiting for data with no structured handoff mechanism.

8. No Async Pipeline Support → Solved by CompletableFuture
Problem: Chaining async steps required deeply nested callbacks or blocking get() calls.

```
---

## Problems with traditional synchonized keyword 

1. We are  not having any flexibility to try for a lock without waiting.

2. There is no way to specify maximun waiting time for a thread to get a lock  ,so that thread will wait untill getting lock  which may
     created performance problems which may causes deadlock.

3. If a thread releases lock  which waiting thread will get that lock, we are not having  any control on this.

4. There is no API  to list out all waiting threads for a lock .

5 . The synchronization keyword compulsory  we have to use either at method level or within  a method  and it is not possible to use across
     multiple methods

To overcome thid problems   we have java .util. concurrent.locks in version 1.5 



## Lock interface 
The Lock interface (from java.util.concurrent.locks) provides a more flexible and powerful way to handle synchronization compared to synchronized.
Lock object is similar to  implicit lock acquired by a thread to execute synchonized method or block .

## Methods of Lock interface 
``` text
1. void lock()

👉 Acquires the lock (waits indefinitely if not available)

lock.lock();
Thread will block until lock is available
Similar to entering a synchronized block



2 boolean tryLock()

👉 Attempts to acquire lock without waiting

if(lock.tryLock()) {
    // critical section
}
else 
{
perform alternative operation 
}

Returns:
true → lock acquired
false → lock not acquired


3 boolean tryLock(long time, TimeUnit unit)

👉 Waits for a specific time to acquire lock

lock.tryLock(2, TimeUnit.SECONDS);
Avoids infinite waiting
Helps prevent deadlocks

4 void lockInterruptibly() throws InterruptedException

acquires the lock if it is available and return immediately , if the lock is not returm immediately then it will wait() , while waiting if the
thread is interrrupted then thread won't get the lock.


5 void unlock()

👉 Releases the lock

lock.unlock();

⚠️ Must always be called after lock()

To call this compulosry current thread should be owner of lock otherwise we will get runtime exception saying IllegalMonitorStateException 



6 . ondition newCondition()

👉 Creates a condition object (like wait/notify)

Condition condition = lock.newCondition();

Used with:

await() → wait
signal() → notify



```
---


## ReentrantLock 
``` text 
Implementation class of ReentrantLock.

Internally  ReentrantLock increaments threads personal count  whenever we call lock method and decreament count value , whenever thread calls
unlock method and lock will be released whenever count reacher zero.


🔹 Why is it called Reentrant?

👉 Reentrant means:

The same thread can acquire the same lock multiple times without getting blocked.

🔸 Example idea:

If a thread already holds the lock, it can enter again.

lock.lock();  // 1st time
lock.lock();  // 2nd time (allowed)

⚠️ But you must call unlock() the same number of times.

-----------


🔹 Basic Example
import java.util.concurrent.locks.*;

class Demo {
    static ReentrantLock lock = new ReentrantLock();

    public static void main(String[] args) {

        lock.lock();
        try {
            System.out.println("Inside critical section");
        } finally {
            lock.unlock();
        }
    }
}



2 Fairness Policy (Important 🔥)
ReentrantLock lock = new ReentrantLock(true); // fair lock
true → FIFO order (first come, first serve)
false (default) → faster but no guarantee



# Constructors of ReentrantLock

1. ReentrantLock lock = new ReentrantLock();

2.ReentrantLock lock = new ReentrantLock(boolean fairness);

Creates a RL with the given fairness policy , if fairness is true then longest waiting thread  can acquire the lock if it is available  i.e. it follows
FCFS policy.

If fairness is false then which waiting thread will get a chance we can't expect.

Note : the default value for fairness is false 

```
---



## Examples :
``` java
# Working using Synchronization

class Display
{
	public synchronized void wish(String name)
	{
		for(int i=1;i<=10;i++)
		{
			System.out.print("Good Morning");
			try{Thread.sleep(1000);} catch(InterruptedException e ){}
			System.out.println(name);
		}
	}
}

class MyThread extends Thread 
{
	Display d;
	String name ;
	MyThread(Display d , String name)
	{
		this.d=d;
		this.name=name;
	}
	
	public void run()
	{
		d.wish(name);
	}
}
class demo1
{
	public static void main(String ar[])
	{
		Display d = new Display();
		MyThread t1 = new MyThread(d,"dhoni");
		MyThread t2 = new MyThread(d,"yuraj");
		t1.start();
		t2.start();
	}
}

Output : Regular output


# Same working without using synchronization 

import java.util.concurrent.locks.*;
class Display
{
	 ReentrantLock l =  new ReentrantLock();
	public  void wish(String name)
	{
		l.lock();
		for(int i=1;i<=10;i++)
		{
			
			System.out.print("Good Morning : ");
			try{Thread.sleep(1000);} catch(InterruptedException e ){}
			System.out.println(name);
		}
		l.unlock();
	}
}

class MyThread extends Thread 
{
	Display d;
	String name ;
	MyThread(Display d , String name)
	{
		this.d=d;
		this.name=name;
	}
	
	public void run()
	{
		d.wish(name);
	}
}
class demo1
{
	public static void main(String ar[])
	{
		Display d = new Display();
		MyThread t1 = new MyThread(d,"dhoni");
		MyThread t2 = new MyThread(d,"yuraj");
		t1.start();
		t2.start();
	}
}
Output : Regular output 


# With using tryLock() method 

import java.util.concurrent.locks.*;

class MyThread extends Thread 
{
	 static  ReentrantLock l = new ReentrantLock();
	MyThread(String name) 
	{
		super(name);
	}
	
	public void run()
	{
		if(l.tryLock())
		{
			System.out.println(Thread.currentThread().getName()+".....got lock and performing safe operations");
			try{
				Thread.sleep(2000);
			}
			catch(InterruptedException e) {}
			l.unlock();
		}
		else
		{
			System.out.println(Thread.currentThread().getName()+"...unable to get lock  and hence perform alternate operations");
		}
	}
}
class demo1
{
	public static void main(String ar[])
	{
		MyThread t1 = new MyThread("First Thread");
		MyThread t2 = new MyThread("Second Thread");
		t1.start();
		t2.start();
	}
}
Output : Regular 

```
---















































































































































































































































































































































































































































































































































































































































































     
   
   
		  
		  
				   
		   
		   
 
		
		

      
 
 