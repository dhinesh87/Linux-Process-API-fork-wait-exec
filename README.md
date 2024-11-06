# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls

```c
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }
```














##OUTPUT:
```c
$ ./pidcheck.o 
The process id: 2382
The process id of parent function: 2258
```
![Screenshot 2024-09-11 112810](https://github.com/user-attachments/assets/7b212865-37d9-4b36-aaf4-d5d045aa6f38)















## C Program to create new process using Linux API system calls fork() and exit():

# PROGRAM:
```c
#include <stdio.h>
#include<stdlib.h>
int main()
{ int pid; 
pid=fork(); 
if(pid == 0) 
{ printf("Iam child my pid is %d\n",getpid()); 
printf("My parent pid is:%d\n",getppid()); 
exit(0); } 
else{ 
printf("I am parent, my pid is %d\n",getpid()); 
sleep(100); 
exit(0);} 
}
```

##OUTPUT:



![Screenshot 2024-09-11 114554](https://github.com/user-attachments/assets/1bf7a385-202f-49af-99cc-44ddd59d6b43)








## C Program to execute Linux system commands using Linux API system calls exec() family:

# PROGRAM:
```c
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);}
```


























##OUTPUT:


![Screenshot 2024-09-11 210236](https://github.com/user-attachments/assets/d72c442c-c284-48fe-ad3f-d191250343d2)



















# RESULT:
The programs are executed successfully.
