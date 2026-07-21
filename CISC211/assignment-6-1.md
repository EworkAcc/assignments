```assembly
section .text
    global _start
_start:
    jmp loop
loop:
    mov eax, [curr_loop]
    cmp eax, [loop_count]
    jge exit
    mov eax, 4
    mov ebx, 1
    mov ecx, print
    mov edx, 1
    int 0x80
    add BYTE [print], 1
    add DWORD [curr_loop], 1
    mov eax, 4
    mov ebx, 1
    mov ecx, newline
    mov edx, 1
    int 0x80
    jmp loop
exit:
    mov eax, 1
    xor ebx, ebx
    int 0x80
section .data
    loop_count dd 26
    curr_loop dd 0
    print db 'A'
    newline db 0xA
```
