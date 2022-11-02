+ These types of OSs serve real-time systems. The time interval required to process and respond to inputs is very small. This time interval is called response time.

+ Real-time systems are used when there are time requirements that are very strict like missile systems, air traffic control systems, robots, etc.

### Two types of Real-Time Operating System which are as follows:

1. Hard Real-Time Systems:

These OSs are meant for applications where time constraints are very strict and even the shortest possible delay is not acceptable. These systems are built for saving life like automatic parachutes or airbags which are required to be readily available in case of any accident. Virtual memory is rarely found in these systems.

2. Soft Real-Time Systems:

These OSs are for applications where for time-constraint is less strict.

### Advantages of RTOS:

+ Maximum Consumption: Maximum utilization of devices and system, thus more output from all the resources
+ Task Shifting: The time assigned for shifting tasks in these systems are very less. For example, in older systems, it takes about 10 microseconds in shifting one task to another, and in the latest systems, it takes 3 microseconds.
+ Focus on Application: Focus on running applications and less importance to applications which are in the queue.
+ Real-time operating system in the embedded system: Since the size of programs are small, RTOS can also be used in embedded systems like in transport and others.
+ Error Free: These types of systems are error-free.
+ Memory Allocation: Memory allocation is best managed in these types of systems.

### Disadvantages of RTOS:

+ Limited Tasks: Very few tasks run at the same time and their concentration is very less on few applications to avoid errors.
+ Use heavy system resources: Sometimes the system resources are not so good and they are expensive as well.
+ Complex Algorithms: The algorithms are very complex and difficult for the designer to write on.
+ Device driver and interrupt signals: It needs specific device drivers and interrupts signals to respond earliest to interrupts.
+ Thread Priority: It is not good to set thread priority as these systems are very less prone to switching tasks.

#### Examples of Real-Time Operating Systems are: **Scientific experiments, medical imaging systems, industrial control systems, weapon systems, robots, air traffic control systems, etc.**