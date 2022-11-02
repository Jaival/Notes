### **Need for Operating System:** 

-   **OS as a platform for Application programs:**   
    + The operating system provides a platform, on top of which, other programs, called application programs can run. These application programs help the users to perform a specific task easily. It acts as an interface between the computer and the user. It is designed in such a manner that it operates, controls, and executes various applications on the computer.  
     
-   **Managing Input-Output unit:**   
    + Operating System also allows the computer to manage its own resources such as memory, monitor, keyboard, printer, etc. Management of these resources is required for effective utilization. The operating system controls the various system input-output resources and allocates them to the users or programs as per their requirements.
    -   **Consistent user interface:**   
        + Operating System provides the user with an easy-to-work user interface, so the user doesn’t have to learn a different UI every time and can focus on the content and be productive as quickly as possible. Operating System provides templates, and UI components to make the working of a computer, really easy for the user.  
         
-   **Multitasking:**   
    + Operating System manages memory and allows multiple programs to run in their own space and even communicate with each other through shared memory. Multitasking gives users a good experience as they can perform several tasks on a computer at a time.
    

**Functions of an Operating System :**  
+ An operating system has a variety of functions to perform. Some of the prominent functions of an operating system can be broadly outlined as:   
 

-   **Processor Management:** 
	- This deals with the management of the Central Processing Unit (CPU). The operating system takes care of the allotment of CPU time to different processes. When a process finishes its CPU processing after executing for the allotted time period, this is called scheduling. There is various type of scheduling techniques that are used by the operating systems: 
    1.  **Shortest Job First(SJF)**: The process which needs the shortest CPU time is scheduled first.
    2.  **Round Robin Scheduling:** Each process is assigned a fixed CPU execution time in a cyclic way.
    3.  **Priority Based Scheduling (Non-Preemptive):** In this scheduling, processes are scheduled according to their priorities, i.e., the highest priority process is scheduled first. If the priorities of the two processes match, then schedule according to arrival time.
-   **Context Switching:** 
	- In most multitasking OSs, multiple running processes on the system may need a change of state in execution. Even if there are multiple processes being executed at any one point in time, only one task is executed in the foreground, while the others are put in the background. So the process that is in the foreground is determined by the priority-based scheduling, and the OS saves the execution state of the previous process before switching to the current one. This is known as context switching.  
     
-   **Device Management:**   
    + The Operating System communicates with the hardware and the attached devices and maintains a balance between them and the CPU. This is all the more important because the CPU processing speed is much higher than that of I/O devices. In order to optimize the CPU time, the operating system employs two techniques – Buffering and Spooling.  
     
-   **Buffering:**   
    + In this technique, input and output data are temporarily stored in Input Buffer and Output Buffer. Once the signal for input or output is sent to or from the CPU respectively, the operating system through the device controller moves the data from the input device to the input buffer and from the output buffer to the output device. In the case of input, if the buffer is full, the operating system sends a signal to the program which processes the data stored in the buffer. When the buffer becomes empty, the program informs the operating system which reloads the buffer and the input operation continues.  
     
-   **Spooling (Simultaneous Peripheral Operation On Line):**   
    + This is a device management technique used for processing different tasks on the same input/output device. When there are various users on a network sharing the same resource then it can be a possibility that more than one user might give it a command at the same point in time. So, the operating system temporarily stores the data of every user on the hard disk of the computer to which the resource is attached. The individual user need not wait for the execution process to be completed. Instead, the operating system sends the data from the hard disk to the resource one by one.   
      **Example:** printer  
     
-   **Memory management:**   
    + In a computer, both the CPU and the I/O devices interact with the memory. When a program needs to be executed it is loaded onto the main memory till the execution is completed. Thereafter that memory space is freed and is available for other programs. The common memory management techniques used by the operating system are Partitioning and Virtual Memory.  
     
-   **Partitioning:**   
    + The total memory is divided into various partitions of the same size or different sizes. This helps to accommodate a number of programs in the memory. The partition can be fixed i.e. remains the same for all the programs in the memory or variable i.e. memory is allocated when a program is loaded onto the memory. The latter approach causes less wastage of memory but in due course of time, it may become fragmented.  
     
-   **Virtual Memory:**
    + This is a technique used by the operating systems which allows the user can load programs that are larger than the main memory of the computer. In this technique, the program is executed even if the complete program can not be loaded inside the main memory leading to efficient memory utilization.  
     
-   **File Management:**   
    + The operating system manages the files, folders, and directory systems on a computer. Any data on a computer is stored in the form of files and the operating system keeps the information about all of them using the File Allocation Table (FAT), or a data structure called an inode in Linux. The FAT stores general information about files like filename, type (text or binary), size, starting address, and access mode (sequential/indexed sequential/direct/relative). 
    + The file manager of the operating system helps to create, edit, copy, allocate memory to the files and also updates the FAT. The operating system also takes care that files are opened with proper access rights to read or edit them.

## Operating System Services 

The main purpose of operating system is to provide environment for execution of programs. Thus, an operating system provides certain services to programs and the users of those programs.

**1. Program Execution**

-   Operating system provides a convenient environment where users can run their programs.
-   The operating system performs memory allocation to programs, load them into appropriate location so that they can execute. The users not to worry about all these tasks.

**2. I/O Operations**

-   In order to execute a program, it usually requires an I/O operations. For example, it may need to read a file and print the output.
-   When all these I/O operations are performed users cannot control I/O devices.
-   All I/O are performed under the control of operating system.

**3.  Communication**

-   The various processes executing on a system may need to communicate in-order to exchange data or information.
-   Operating system provides this communication by using a facility of _message passing._ In message passing packets of information are moved between processes by operating system.