# Heap Memory Manager

This project is about designing a Heap memory manager which will handle the memory requests of the user space processes. It also takes care of the problems of internal fragmentation, external fragmentation, and boost performance of the process by preventing unnecessary system calls for allocating/releasing the memory.

The memory manager can display the statistics regarding the memory usage by each structure of the process. From this stats, application memory usage can be analyzed and can provide hints to further optimize the memory requirements of the process.

The memory manager requests and releases memmory from kernel space on behalf of application in units of Virtual Memory Pages. It uses mmap() and munmap() system calls for this purpose. It caches the VM pages and use it as reservoir for future memory requests issued by the application, until the VM page is fully exhausted. VM page is released back to kernel if application has freed enough Memory such that VM page has no region occupied/allocated to the application for use.

Main tasks: 
- Block Splitting and Merging
- Doubly linked list for maintaining free and allocated blocks 
- Memory allocation techniques for allocating memory to the processes

Compilations:
- gcc -g -c testapp.c -o testapp.o
- gcc -g -c memoryManager.c -o mm.o
- gcc -g -c glthreads/glthread.c -o glthreads/glthread.o
- gcc -g testapp.o mm.o glthreads/glthread.o -o exe

Execution: ./exe
