![hardware organization](graphs/hardwareOrganization.jpg)

# Buses

Running throughout the system is a collection of electrical conduits called *buses*. Buses are typically designed to transfer fixed-size chunks of bytes known as ***words***. The number of bytes in a word (the *word size*) is a fundamental system parameter that varies across systems. Most machines today have word sizes of eithe 4 bytes (32 bits) or 8 bytes (64 bits).

> The *central processing unit* (CPU), or simply *processor*, is the engine that interprets (or *executes*) instructions stored in main memory. At its core is a word-size storage device (or *register*) called the *program counter* (PC). At any point in time, the PC points at (contains the address of) some machine-language instruction in main memory

Every computer has a *word size*, indicating the nominal size of pointer data. Since a virtual address is encode by such a word, the most important system parameter determined by the word size is the maximum size of the virtual address space. That is, for a machine with a *w-bit* word size, the virtual address can range from 0 to `2^w - 1`, giving the program access to at most `2^w` bytes.

# data bus

# address bus