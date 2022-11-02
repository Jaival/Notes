## Definition

+ An operating system is a program that controls the execution of application programs and acts as an interface between the user of a computer and the computer hardware.
+ A more common definition is that the operating system is the one program running at all times on the computer (usually called **the kernel**), with all else being application programs.
+ An operating system is concerned with the allocation of resources and services, such as memory, processors, devices, and information. The operating system correspondingly includes programs to manage these resources, such as a traffic controller, a scheduler, a memory management module, I/O programs, and a file system.

## Functions

+ Convenience: An OS makes a computer more convenient to use.
+ Efficiency: An OS allows the computer system resources to be used efficiently.
+ Ability to Evolve: An OS should be constructed in such a way as to permit the effective development, testing, and introduction of new system functions at the same time without interfering with service.
+ Throughput: An OS should be constructed so that it can give maximum throughput(Number of tasks per unit time).

## Main Functionalities of Operating System:

+ Resource Management
	+ When parallel accessing happens in the OS means when multiple users are accessing the system the OS works as Resource Manager, Its responsibility is to provide hardware to the user. It decreases the load in the system.

+ Process Management
	+ It includes various tasks like scheduling, termination of the process. OS manages various tasks at a time. Here CPU Scheduling happens means all the tasks would be done by the many algorithms that use for scheduling.

+ Storage Management
	+ The file system mechanism used for the management of the storage. NIFS, CFS, CIFS, NFS, etc. are some file systems. All the data stores in various tracks of Hard disks that all managed by the storage manager. It included Hard Disk.

+ Memory Management
	+ Refers to the management of primary memory. The operating system has to keep track, how much memory has been used and by whom. It has to decide which process needs memory space and how much. OS also has to allocate and deallocate the memory space.

+ Security/Privacy Management
	+ Privacy is also provided by the Operating system by means of passwords so that unauthorized applications can’t access programs or data. For example, Windows uses Kerberos authentication to prevent unauthorized access to data.

## Basics

+ Every general-purpose computer consists of the hardware, operating system, system programs, and application programs. The hardware consists of memory, CPU, ALU, and I/O devices, peripheral devices, and storage devices. System program consists of compilers, loaders, editors, OS, etc. The application program consists of business programs, database programs.

##### OS is designed to serve two basic purposes:

+ It controls the allocation and use of the computing System’s resources among the various user and tasks.
+ It provides an interface between the computer hardware and the programmer that simplifies and makes it feasible for coding, creation, debugging of application programs.

The Operating system must support the following tasks. The tasks are:

+ Provides the facilities to create, modification of programs and data files using an editor.
+ Access to the compiler for translating the user program from high-level language to machine language.
+ Provide a loader program to move the compiled program code to the computer’s memory for execution.
+ Provide routines that handle the details of I/O programming.

**1. I/O System Management**
The module that keeps track of the status of devices is called the I/O traffic controller. Each I/O device has a device handler that resides in a separate process associated with that device.

The I/O subsystem consists of
+ A memory Management component that includes buffering caching and spooling.
+ A general device driver interface.
+ Drivers for specific hardware devices.

**2. Assembler**
+ The input to an assembler is an assembly language program. The output is an object program plus information that enables the loader to prepare the object program for execution. 
+ At one time, the computer programmer had at his disposal a basic machine that interpreted, through hardware, certain fundamental instructions. He would program this computer by writing a series of ones and Zeros (Machine language), place them into the memory of the machine.

**3. Compiler**
+ The High-level languages - examples are FORTRAN, COBOL, ALGOL, and PL/I are processed by compilers and interpreters. A compiler is a program that accepts a source program in a “high-level language “and produces a corresponding object program. 
+ An interpreter is a program that appears to execute a source program as if it was machine language. The same name (FORTRAN, COBOL, etc.) is often used to designate both a compiler and its associated language.

**4. Loader**
+ A Loader is a routine that loads an object program and prepares it for execution. There are various loading schemes: absolute, relocating, and direct-linking. In general, the loader must load, relocate and link the object program. The loader is a program that places programs into memory and prepares them for execution.

### [[Functions of OS]]

1. Security
2. Control over system performance
3. Job accounting
4. Error detecting aids
5. Coordination between other software and users
6. Memory Management
7. Processor Management
8. Device Management
9. File Management

### Types of Operating System

1. [[Batch Operating System]] - Sequence of jobs in a program on a computer without manual interventions.
2. [[Time-Sharing Operating Systems]]- Allows many users to share the computer resources. (Max utilization of the resources).
3. [[Distributed Operating System]] - Manages a group of different computers and makes appear to be a single computer.
4. [[Network Operating System]]- Computers running in different operating systems can participate in a common network (It is used for security purposes).
5. [[Real-Time Operating System]] – Meant applications to fix the deadlines.

#### Examples of Operating System are

+ Windows (GUI based, PC)
+ GNU/Linux (Personal, Workstations, ISP, File and print server, Three-tier client/Server)
+ macOS (Macintosh), used for Apple’s personal computers and workstations (MacBook, iMac).
+ Android (Google’s Operating System for smartphones/tablets/smartwatches)
+ iOS (Apple’s OS for iPhone, iPad, and iPod Touch)