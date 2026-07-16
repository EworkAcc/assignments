




```asm
section .text
    global _start
_start: 
    mov eax, [loop_count] ; loop
    sub eax, 2
    mov ebx, 0 ; num 1
    mov ecx, 1 ; num 2
    mov edx, 0 ; tmp store
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
