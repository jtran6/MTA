# 70-483

## Chapter 1

### Objective 1.1 Implement multithreading and asynchronous processing

#### Vocabulary
##### Understanding Threads

| Term                         | Definition    |
| :------------                |:--------------|
| Parallelism                  | the use of multiple threads to do something |
| Central Processing Unit(CPU) | |
| Thread                       | a concept that isolates a process in order to free up memory. A virtualized CPU |
| Process                      | each application isolates itself in order to separate the work load a CPU does      |
| Virtual Memory               | preallocated memory for a process      |
| Context Switching            | each thread is allowed a certain amount of time to execute. After this time, the thread is paused and Windows switches to another thread      |


##### Using the Thread class 

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

##### Thread Pools

| Term        | Definition  |
| :---------- | :---------- |
| Thread Pool | a place to send threads when they finished executing in order to reuse them and save time and resources. Works in same way a database connection works. Instead of letting a thread die, you sent it back to the pool where it can be reused when a request comes in |

##### Using Tasks

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

##### Using the Parallel class

| Term             | Definition  |
| :----------      | :---------- |
| Parallelism      | involves taking a certain task and splitting it into a set of related tasks that can be executed concurrently |

##### Using async and await

| Term             | Definition  |
| :----------      | :---------- |
|  |  |


### Objective 1.2 Manage multithreading

### Objective 1.3 Implement program flow

### Objective 1.4 Create and implement events and callbacks

### Objective 1.5 Implement exception handling

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