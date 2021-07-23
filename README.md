# Examine Variables - from "How Computers Really Work" book, by Matthew Justice

Compile source code with GNU C Compiler (gcc)
```bash
gcc -o vars vars.c
```

Run the executable file
```bash
./vars
```

Examine the variables memory addresses and values stored in those addresses
```bash
gdb vars
```

```
GNU gdb (Raspbian 8.2.1-2) 8.2.1
Copyright (C) 2018 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "arm-linux-gnueabihf".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from vars...(no debugging symbols found)...done.
(gdb) run
Starting program: /home/pi/source/examine-variables/vars
points is 27 and is stored at 0xbefff4fc
year is 2020 and is stored at 0xbefff4f8

Program received signal SIGINT, Interrupt.
__GI_raise (sig=2) at ../sysdeps/unix/sysv/linux/raise.c:50
50	../sysdeps/unix/sysv/linux/raise.c: No such file or directory.
(gdb) x/3xw 0xbefff4f8
0xbefff4f8:	0x000007e4	0x0000001b	0x00000000
```

`years` = 0x000007e4 = 2020 (in decimal)  
`points` = 0x0000001b = 27 (in decimal)

Same thing, this time printing the values in decimal format
```
(gdb) x/3dw 0xbefff4f8
0xbefff4f8:	2020	27	0
```

Same thing, this time in series of bytes (in little-endian data storage)
```
(gdb) x/12xb 0xbefff4f8
0xbefff4f8:	0xe4	0x07	0x00	0x00	0x1b	0x00	0x00	0x00
0xbefff500:	0x00	0x00	0x00	0x00
```