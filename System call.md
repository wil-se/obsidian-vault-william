# System call
#### Way for programs to access kernel services

In computing, a system call (commonly abbreviated to syscall) is the programmatic way in which a computer program requests a service from the kernel of the operating system on which it is executed. This may include hardware-related services (for example, accessing a hard disk drive or accessing the device's camera), creation and execution of new processes, and communication with integral kernel services such as process scheduling.  System calls provide an essential interface between a process and the operating system.
In most systems, system calls can only be made from userspace processes, while in some systems, OS/360 and successors for example, privileged system code also issues system calls.
The architecture of most modern processors, with the exception of some embedded systems, involves a security model. For example, the rings model specifies multiple privilege levels under which software may be executed: a program is usually limited to its own address space so that it cannot access or modify other running programs or the operating system itself, and is usually prevented from directly manipulating hardware devices (e.g. the frame buffer or network devices).

[[Computer program]]
[[Operating system]]
[[Computer network]]
[[Interrupt]]
[[Assembly language]]
[[Processor register]]
[[C (programming language)]]
[[Linux]]
[[Microsoft Windows]]