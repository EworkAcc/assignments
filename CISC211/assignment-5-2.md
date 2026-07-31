<img width="477" height="900" alt="Blank diagram" src="https://github.com/user-attachments/assets/6de58b24-e526-4bfe-a379-fb432e8b5cc6" />

Challenges 

I faced few challenges while coding this. The main problem I faced was when finally running the code. This happened because I started by initializing the first two numbers in the Fibonacci sequence. This meant when I made the loop loop 10 times, instead of getting the 10th number it would get the 12th number. Because of this, I had to add a statement that would deduct two from the total loops to make sure it would get the correct number in the Fibonacci sequence. And after using GDB to check the value of result, it worked.

Counter
```asm
section .text
        global _start

_start:
        mov ecx, 10
        .loop:
        loop .loop

        mov eax,1
        xor ebx, ebx
        int 0x80
```

Findings for Counter

I found that the counter is similar to the non optimized code, but instead of incrementing eax, it decrements ecx. 

Fibonacci

```asm
section .text
    global _start
_start: 
    mov eax, [loop_count] ; loop
    sub eax, 2
    mov ebx, 0 ; num 1
    mov ecx, 1 ; num 2
    mov edx, 0 ; tmp store<img width="477" height="900" alt="Blank diagram" src="https://github.com/user-attachments/assets/dd519f66-690e-4101-b0a6-1611038eed3f" />

loop:
    cmp eax, 0 
    jle quit
    mov edx, ecx
    add ecx, ebx
    mov ebx, edx
    dec eax
    jmp loop
quit:
    mov [result], ecx
    mov eax, 1
    xor ebx, ebx
    int 0x80
section .data
    loop_count dd 10
    result dd 0
```

Array

```asm
section .text
global _start
_start:
    mov ebx, array
    mov ecx, 3
    mov eax, [ebx]
    mov [biggest], eax
    loop:
    cmp ecx, 0
    jle exit
    mov eax, [ebx]
    cmp eax, [biggest]
    jle next
    mov [biggest], eax
next:
    add ebx, 4
    dec ecx
    jmp loop
less:
    mov [biggest], eax
    add ecx, 4
    cmp ecx, 1
    jle exit 
exit:
    mov eax, 1
    xor ebx, ebx
    int 0x80
section .data
    array dd 10, 20, 30
section .bss
    biggest resd 1
```
