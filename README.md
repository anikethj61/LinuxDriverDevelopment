# LinuxDriverDevelopment
This repo is about how to build drivers for Linux Kernel. This has been done by referring multiple tutorial videos, textbooks and forums

> Textbook: https://lwn.net/Kernel/LDD3/


In the chapter 2 of this textbook "Building and Running modules", its explained how to build modules and execute them in the kernel. 
Modules are lines of code that can be executed in the kernel. "module_init" and "module_exit" will have parameters as functions defined to be run at initialisation and exit or end of the program. 
The code is written as follows 

```
#include <linux/init.h>
#include <linux/module.h>
MODULE_LICENSE("Dual BSD/GPL");

static int hello_init(void)
{
    printk(KERN_ALERT "Hello, World\n");
    return 0;
}

static void hello_exit(void)
{
    printk(KERN_ALERT "Goodbye, cruel world\n");
}

module_init(hello_init);
module_exit(hello_exit);
```

> File Name: hello.c

The hello world module is coded as shown above. It has two functions one to be invoked when the module is loaded in to the kernel, another when the module is to be removed. 
"module_init" and "module_exit" are special macros used to indicate the role of these two functions.
module_license is a macro to describe the use of free license

> printk - a function similar to printf but for kernels

##Testing of the module: 


```make```


```insmod ./hello.ko```


```rmmod hello```
