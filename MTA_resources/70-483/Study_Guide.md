# 70-483

## Chapter 1

### Objective 1.1 Implement multithreading and asynchronous processing

#### Understanding Threads

| Term                         | Definition    |
| :------------                |:--------------|
| Parallelism                  | the use of multiple threads to do something |
| Central Processing Unit(CPU) | |
| Thread                       | a concept that isolates a process in order to free up memory. A virtualized CPU |
| Process                      | each application isolates itself in order to separate the work load a CPU does      |
| Virtual Memory               | preallocated memory for a process      |
| Context Switching            | each thread is allowed a certain amount of time to execute. After this time, the thread is paused and Windows switches to another thread      |


#### Using the Thread class 

| Term                          | Definition    |
| :------------                 |:--------------|
| System.Threading              | namespace where the Thread class can be found |
| Console                       | class that synchronizes the use of the output stream so you can write to it from multiple threads |
| Synchronization               | the mechanism of ensuring that two threads don't execute a specific portion of the program at the same time |
| Thread.Join                   | called on main thread to let it wait until the other threads are finished |
| Thread.Sleep(0)               | used to signal Windows that this thread is finished. Will immediately switch to another thread. |
| Foreground Thread             | used to keep an application alive. When foreground threads end, the CLR shuts down your application |
| Background Thread             | |
| ParameterizedThreadStart      | used to pass some data through the start method of the thread |
| Thread.Abort                  | stops a thread |
| Thread.IsBrackground          | property of thread which exits application immediately when set to true |
| ThreadAbortException          | When Thread.Abort is called by another thread which can happen at any time |
| Thread.CurrentThread          | used to ask the system which thread is excuting as well as the information about the thread |
| ExecutionContext.SuppressFlow | used to disable the behavior of getting thread information to reduce costs on resources |

#### Thread Pools

| Term        | Definition  |
| :---------- | :---------- |
| Thread Pool | a place to send threads when they finished executing in order to reuse them and save time and resources. Works in same way a database connection works. Instead of letting a thread die, you sent it back to the pool where it can be reused when a request comes in |

#### Using Tasks

| Term           | Definition  |
| :----------    | :---------- |
| Task           | an object that represents that work should be done. Can tell you if the work is completed and it the operation returns a result |
| Task Scheduler | is responsible for starting a task and managing it. By default uses threads from thread pool to execute the task |
| Task.Wait      | equivalent to calling Thread.Join. It waits until the task is finished before exiting application |
| Task<T>        | this task returns a value of class T |
| Task.Result    | forces the thread that's trying to read the result to wait until Task is finished before continuing |
| ContinueWith() | a continuation of a task which has a couple of overloads that you can use to configure when the continuation will run |
| Child Task     | nested tasks within tasks which are called when the parent task is called |
| Task Factory   | a class that can be used to create new tasks with some parameters |
| Task.WaitAll() | tells the system to wait until all tasks are finished before continuing execution |
| Task.WhenAll() | used to schedule a continuation method when all tasks have finished |
| Task.WaitAny() | used to call a task when a single task is finished |

#### Using the Parallel class

| Term             | Definition  |
| :----------      | :---------- |
| Parallelism      | involves taking a certain task and splitting it into a set of related tasks that can be executed concurrently |

#### Using async and await

| Term             | Definition  |
| :----------      | :---------- |
| async | returns a Task object that represents the results of the asynchronous operation. This task can then be continued to prevent thread blockage. Continues even after I/O |
| await | compiler generated code that checks whether or not your asynchronous operation finished |

#### Exam Tip: 
When using async and await keep in mind that you should never have a method marked async without any await statements. You should also avoid returning void from an async method except when it's an event handler.s

#### Using Parallel Language Integrated Query (PLINQ)

| Term             | Definition  |
| :----------      | :---------- |
| Parallel Language Integrated Query | turn a sequential query into a parallel one |
| PLINQ Operators | Where, Select, SelectMany, GroupBy, Join, OrderBy, Skip, Take |

#### Using Concurrent Collections

| Term             | Definition  |
| :----------      | :---------- |
| BlockingCollection<T> | collection is thread-safe for adding and removing data. Blocks removing until data becomes available. Blocks adding after manually setting upper limit |
| ConcurrentBag<T> | a bag of items, it allows duplicates and has no order. Add, TryTake, TryPeek |
| ConcurrentDictionary<T> | stores key value pairs in a thread-safe manner. Use methods to add and remove and update if already exists |
| ConcurrentQueue<T> | FIFO Enqueue and TryDequeue |
| ConcurrentStack<T> | LIFO, Push and TryPop/PushRange, TryPopRange |

-----

#### Thought Experiment

You need to build a new application, and you look into multithreading capabilities. Your application consists of a client application that communicates with a web server.

| Question         | Answer      |
| :----------      | :---------- |
| Explain how multithreading can help with your client application? |  |
| What is the difference between CPU and I/O bound operations? |  |
| Does using multithreading with the TPL offer the same advantages for your server application? |  |

----

### Objective 1.2 Manage multithreading

#### Synchronizing Resources

When accessing the same data from multiple threads simultaneously, it is important to utilize the lock method in order to properly specify order of execution. However, deadlocking can occur where ThreadA is waiting for ThreadB and ThreadB is currently being stopped by the main thread because it is waiting for ThreadA to finish executing.

System.Threading.Volatile is a class with special Write/Read methods that disable compiler optimizations so you can force the correct order in your code. However, the performance suffers when using this class. 

The Interlocked Class can be used to atomically increment and decrement values.

#### Canceling Tasks

A CancellationToken can be passed into a task which periodically monitors the token to see whether a cancellation is requested.

-----

#### Thought Experiment

You are experiencing deadlocks in your code. It's true that you have a lot of locking statements and you are trying to improve your code to avoid deadlocks.

| Question         | Answer      |
| :----------      | :---------- |
| How can you orchestrate your locking code to avoid deadlocks? |  |
| How can the Interlocked class help you? |  |

----

### Objective 1.3 Implement program flow

#### Working with Boolean expressions

| Operator    | Description              | Example          |
| :---------- | :----------              | :------          |
| <           | Less Than                | x < 42           |
| >           | Greater Than             | x > 42           |
| <=          | Less Than or Equal to    | x <= 42          |
| >=          | Greater Than or Equal to | x >= 42          |
| ==          | Equal To                 | x == 42          |
| !=          | Not Equal To             | x != 42          |
| ||          | OR                       | x != 42 || x > 2 |
| &&          | AND                      | x != 42 && x > 1 |
| ^           | Exclusive OR             | x != 42 ^ x < 10 |

Exclusive OR operator returns true only when exactly one of the operands is true

| Left-Operand | Right-Operand | Result    |
| :----------  | :----------   | :------   |
| True         | True          | False     |
| True         | False         | True      |
| False        | True          | True      |
| False        | False         | False     |

#### Making Decisions

| Term                         | Definition      |
| :----------                  | :----------     |
| Flow Control statements      | if, while, do while, for, foreach, switch, break, continue, goto, Null-coalescing operator(??), conditional operator(?:) |
| if                           | enables you to execute a piece of code depending on a specific condition |
| switch                       | used to simplify complex if statements |
| break                        | jump statement - used to stop a loop from continuing |
| continue                     | jump statement - used to continue loop |
| goto                         | jump statement - avoid using this |
| Null-coalescing operator(??) | you can use it to provide a default value for nullable value types or for reference types |
| conditional operator(?:)     | returns one of two values depending on a boolean expression. If true, returns first value, if false, returns second value |

#### Iterating Across Collections

| Term        | Definition      |
| :---------- | :----------     |
| while       | executes a piece of code as long as a boolean expression is true |
| do while    | executes at least once even if expression is false |
| for         | used to iterate over a collection until a condition is reached |
| foreach     | used to iterate over a collection where it automatically stores the current item in a loop variable |

#### Thought Experiment

You are updating an old C# 2 console application to WPF C#5 application. The application is used by hotels to keep track of reservations and guests coming and leaving. You are going through the old code base to determine whether there is code that can be easily reused. You notice a couple of things: 
1. the code uses goto statement to manage flow
2. there are a lot of long if statements that map user input
3. the code uses the for loop extensively

| Question         | Answer      |
| :----------      | :---------- |
| What is the disadvantage of using goto? How can you avoid using the goto statement?        |  |
| Which statement can you use to improve the long if statements?                             | Switch |
| What are the differences between the for and foreach statement? When should you use which? |  |

### Objective 1.4 Create and implement events and callbacks

#### Understanding Delegates

| Term           | Definition      |
| :----------    | :----------     |
| Delegate       | a type that defines a method signature |
| Multi-Casting  | when you combine delegates together |
| Covariance     | makes it possible that a method has a return type that is more derived than that defined in the delegate |
| Contravariance | permits a method that has parameter types that are less derived than those in the delegate type |

#### Using Lambda Expressions

#### Using Events

### Objective 1.5 Implement exception handling

#### Handling Exceptions

#### Throwing Exceptions

#### Creating Custom Exceptions

## Chapter 2 Create and use types

### Objective 2.1 Create types

### Objective 2.2 Consume types

### Objective 2.3 Enforce encapsulation

### Objective 2.4 Create and implement a class hierarchy

### Objective 2.5 Find, execute, and create types at runtime by using reflection

### Objective 2.6 Manage the object life cycle

### Objective 2.7 Manipulate strings

## Chapter 3 Debug applications and implement security

### Objective 3.1 Validate application input

### Objective 3.2 Perform symmetric and asymmetric encryption

### Objective 3.3 Manage assemblies

### Objective 3.4 Debug an application

### Objective 3.5 Implement diagnostics in an application

## Chapter 4 Implement data access

### Objective 4.1 Perform I/O operations

### Objective 4.2 Consume data

### Objective 4.3 Query and manipulate data and objects by using LINQ

### Objective 4.4 Serialize and deserialize data

### Objective 4.5 Store data in and retrieve data from collections