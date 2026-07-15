

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
