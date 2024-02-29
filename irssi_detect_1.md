Affected Version:
irssi 1.4.5 b3f6ed0b11c96b06e4e211c3187b4f194d70ce00

Vulnerability Description:
The vulnerability is a memory leak bug located at line 259 of the file /irssi/src/fe-text/mainwindows.c. This vulnerability could potentially be exploited maliciously to cause resource exhaustion and denial of service attacks.

irssi download address:
https://github.com/irssi/irssi.git

Detailed Description of the Defect:

1.A pointer variable named rec is defined at line 213 in the file /irssi/src/fe-text/mainwindows.c. This pointer variable is allocated a block of dynamic memory using the function g_new0 at line 216. g_new0 is a macro that points to the memory allocation function g_malloc0_n. When the conditional statement at line 258 evaluates to true, the program returns NULL at line 259. During this process, the pointer rec is neither returned like at line 279, nor is it freed, thereby constituting a memory leak defect, as illustrated in the following diagram:

![image](https://github.com/LuMingYinDetect/irssi_defects/blob/main/irssi_1.png)
