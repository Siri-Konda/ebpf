# KConnect-Core
## IET Systems SMP Final Boss
### Deadline is 7th July
* Kudos to all of you for making it so far.
* But now is the time for the final project implementation.
* The kernel-side eBPF C code has been given; go through it and write the corresponding bpftrace script. 
* Your output should look something like this:
 ![output](./final_output.png)
* Fork this repo, and start getting your hands dirty.
#### Execution Instructions:
* Compile the display program: `gcc -o kconnectcore kconnectcore.c`
* Run the pipeline: `sudo bpftrace kconnectcore.bt | ./kconnectcore`

  
#### Best of Luck !!!!

---

## Screenshot

<img width="502" height="334" alt="image" src="https://github.com/user-attachments/assets/6c63c097-ee9f-4a18-bb68-d905d3229ea8" />

Ran into some issues with the virtual machine; it kept hanging, and hence, I used a Linux terminal on OrbStack.
Ran the curl command a few times for the screenshot.

The code from previous commits fails because the uservaddr (or the args1) parameter is a user-space pointer, and when bpftrace intercepts the system call at the entry threshold, the kernel hasn't always fully swapped or pinned the application's memory page. When bpftrace attempts an implicit fast-read, it sometimes fetches uninitialized or partially loaded bytes. Thus, it prints out incorrect DEST IPs and PORTS. And it wasn't possible to get the source ports without complicating the code further (Should've checked in the beginning).
