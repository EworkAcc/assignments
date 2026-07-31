```asm
section .text
global _start
_start:
    push dword [x]
    push dword [y]
    push dword [z]
    call add
    add ebp, 12
    jmp exit
add:
    push ebp
    mov ebp, esp
    mov eax, DWORD [ebp + 8]
    add eax, DWORD [ebp + 12]
    add eax, DWORD [ebp + 16] 
    mov [result], eax
    leave
    ret
exit:
    mov eax, 1
    xor ebx, ebx
    int 0x80
section .data
    x dd 10
    y dd 20
    z dd 30
section .bss
    result resd 1
```
