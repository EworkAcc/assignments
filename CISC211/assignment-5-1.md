

Challenges

My main challenge was setting up the loop. When I originally set up the loop, I set the condition for the code ending to the register eax  being greater than the size of the array. The main issue of this  condition is that it didn't fit the initialization of eax. At the start of the code, eax was initialized to be the len of the list. These meant that the code would run forever and continue decreasing until the code threw an error. This was a huge issue that needed to be resolved. After this most of the code worked smoothly. 

```asm
section .text
    global _start
_start:
    mov eax, [list_len]
    mov ebx, 0
    mov ecx, list
loop:
    cmp eax, 0
    jle exit
    cmp ebx, [ecx]
    jl second
    add ecx, 4
    dec eax

second:
    mov ebx, [ecx]
    add ecx, 4
    dec eax
    jmp loop

exit:
    mov [largest], ebx
    mov eax, 1
    xor ebx, ebx
    int 0x80

section .data
    list dd 1,3,5,7,9,11,13,15,17,19
    list_len dd 10
section .bss
    largest resd 1
```
