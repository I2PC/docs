Parallel Programming
----------------------

Introduction
^^^^^^^^^^^^^^^^^^^^^

In the simplest sense, **parallel computing** is the simultaneous use of
multiple compute resources to solve a computational problem:

-  To be run using multiple CPUs
-  A problem is broken into discrete parts that can be solved
   concurrently
-  Each part is further broken down to a series of instructions
-  Instructions from each part execute simultaneously on different CPUs

The compute resources might be:

-  A single computer with multiple processors (using of **threads**);
-  An arbitrary number of computers connected by a network(using
   parallel library like **MPI**);
-  A combination of both.

The computational problem should be able to:

-  Be broken apart into discrete pieces of work that can be solved
   simultaneously;
-  Execute multiple program instructions at any moment in time;
-  Be solved in less time with multiple compute resources than with a
   single compute resource.

In **Xmipp3.0** we have develop several classes to make easier the use
of threads and MPI when developing parallel programs. If you want to
read more about parallel computing there is a nice introduction
`here <https://computing.llnl.gov/tutorials/parallel_comp/>`__. ## Task
distribution

One of the first steps in designing a parallel program is to break the
problem into discrete “chunks” of work that can be distributed to
multiple tasks. This is known as decomposition or partitioning. There
are two basic ways to partition computational work among parallel tasks:
the data is partitioned or the work to be done.

In image processing for *single particles* on electron microscopy we
usually deal with several thousands of images, so the most common and
easy way to distribute is by data. Then each CPU take care of some part
of the data to perform processing tasks.

We have create the class **[[ParallelTaskDistributor]]** which have the
function to distribute N tasks (without knowing what each “task” really
means) between a group of workers (threads or MPI). Each worker will ask
for a some tasks, process it and ask for more tasks until there is
nothing to be done. The following are several subclasses of
`ParallelTaskDistributor <http://xmipp.cnb.uam.es/~xmipp/trunk/xmipp/documentation/html/classParallelTaskDistributor>`__:

::


     //...
     // Create a task distributor with N total task and serve 10 on each request
     ParallelTaskDistributor * td = new ThreadTaskDistributor(N, 10);
     //...
     //function to perform some operation
     //to N images executed in parellel
     void processSeveralImages()
     {
         size_t firstImage, lastImage;
         while (td->getTasks(firstImage, lastImage))
             for (size_t image = firstImage; image <= lastImage; ++image)
             {
                 //...
                 processOneImage(image);
                 //...
             }
     }

Using threads
^^^^^^^^^^^^^^^^^^^^^

Technically, a **thread** is defined as an independent stream of
instructions that can be scheduled to run as such by the operating
system. Before understanding a thread, one first needs to understand a
UNIX process. A process is created by the operating system, and requires
a fair amount of “overhead”. Processes contain information about program
resources and program execution state, including: Process ID, process
group ID, user ID, and group ID, environment, working directory, program
instructions, registers, stack, heap, file descriptors, signal actions,
shared libraries, inter-process communication tools (such as message
queues, pipes, semaphores, or shared memory). Threads use and exist
within these process resources, yet are able to be scheduled by the
operating system and run as independent entities largely because they
duplicate only the bare essential resources that enable them to exist as
executable code.

So, in summary, in the UNIX environment a thread:

-  Exists within a process and uses the process resources
-  Has its own independent flow of control as long as its parent process
   exists and the OS supports it
-  Duplicates only the essential resources it needs to be independently
   schedulable
-  May share the process resources with other threads that act equally
   independently (and dependently)
-  Dies if the parent process dies - or something similar
-  Is “lightweight” because most of the overhead has already been
   accomplished through the creation of its process.

Because threads within the same process share resources:

-  Changes made by one thread to shared system resources (such as
   closing a file) will be seen by all other threads.
-  Two pointers having the same value point to the same data.
-  Reading and writing to the same memory locations is possible, and
   therefore requires explicit synchronization by the programmer.

A more detailed explanation about use of POSIX threads can be found
 here. ### Creating threads and passing parameters

Imagine that you have a program that perform tasks *A*, *B* and *C*, and
tasks *A* and *C* task can be threaded. So, task *A* can be splited in
several concurrent tasks *A1, A2, A3…An* and the same for C. In the
following figure you can see the serial and threaded version of the
program execution:

This type of threading now can be easily done using the following
classes:

-  *[[ThreadManager]]* will create the threads and run diffent functions
   in parallel
-  *[[ThreadFunction]]* prototype of function that can be runned by
   *[[ThreadManager]]*.
-  Its definition is typedef void( **[[ThreadFunction]] )(ThreadArgument
   &arg) typedef void(** [[ThreadFunction]] )(ThreadArgument &arg)
-  *[[ThreadArgument]]*: Argument type that is passed to
   *[[ThreadFunction]]*. It contains:
-  thread_id: number identifying each thread
-  data: void \* pointer to pass additional information
-  workClass: void \* pointer to hold a reference to working class

The previous example can be coded:

::


      void * functionA(ThreadArgument & data)
     {
         //...     
     }
      void * functionB()
     {
         //...     
     }
      void * functionC(ThreadArgument & data)
     {
         //...     
     }

     int main()
     {
     //Start 4 threads to work
     ThreadManager * tm = new ThreadManager(4);
     // Run in parallel functionA
     tm.run(functionA);
     // All threads are syncronized at this point
     functionB(); 
     //If you need to pass some additional information
    // to work on functionB you can do:
    tm.setData(myData);
     // Put the threads works on functionB
     tm.run(functionB);
     }

Synchronizing threads
^^^^^^^^^^^^^^^^^^^^^

Synchronization is vital for almost all parallel programs. We want
things done faster but also we want things done well. Through
synchronization we can guarantee that things are done in the correct
order and provide the same results as if it was done sequentially.

Synchronization between threads is done primarily through mutexes. A
mutex allows to protect a portion of the code so only one thread can
access it at a time. We have created the *Mutex* class wich encapsulates
the mutex creation, initialization and clean up through the *pthreads*
library.

::


   Mutex mutexUpdate;
   //....
   // Inside some threaded function:
   mutexUpdate.lock();
   //Perform the updated
   mutexUpdate.unlock();

Other different synchronization structures exist that can adapt better
to different circumstances. For example, a barrier is used when we want
to synchronize a number of threads at a point of the code so no one can
continue working until all of them have reached such point. Barriers are
not always present on all computing platforms. For example, old Unix
implementations do not have such structure defined on the pthreads
library. To avoid problems of this type, a *Barrier* class have been
implemented base on mutexes. ### Example

 Here you will find a complete example of a parallel program using all
the elements together. This example estimate the value of PI. ### Some
Tips

Programming threads is easy… but debugging threads can be a nightmare.
So take note of these tips:

-  Do not use static variables on threaded code. Such variables are
   shared between all threads and can lead to unexpected results.
-  Do not use threads for everything. Use them when it is clear they
   will represent an advantage. Using too much threads will lead to a
   decreared performance.
-  Try to create threads once and reuse them. Creating and destroying
   threads will represent a slight overhead. On some applications this
   can translate into lower performance. (Create just one
   *[[ThreadManager]]* and run several functions )
-  Be careful with critical regions and the use of *Mutex* and
   *Barrier*. A misuse can lead to race conditions(bad results) or
   deadlock (program will runs forever)

Programming with MPI
^^^^^^^^^^^^^^^^^^^^^

The Message Passing Interface Standard ( **MPI**) is a message passing
library standard based on the consensus of the MPI Forum, which has over
40 participating organizations, including vendors, researchers, software
library developers, and users. The goal of the Message Passing Interface
is to establish a portable, efficient, and flexible standard for message
passing that will be widely used for writing message passing programs.
As such, MPI is the first standardized, vendor independent, message
passing library. The advantages of developing message passing software
using MPI closely match the design goals of portability, efficiency, and
flexibility. MPI is not an IEEE or ISO standard, but has in fact, become
the “industry standard” for writing message passing programs on HPC
platforms. You can find more about MPI  here.

We have created some useful classes like *[[MpiNode]]* that will take
care of some MPI initialization and cleaning. This class also have a
method to synchronize: *barrierWait* and other utilities. The same
concepts for task distribution can be used with MPI through the
*[[MpiTaskDistributor]]* class.

A complete example using the MPI tools is available  Here .