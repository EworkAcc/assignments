section .text
    global _start
_start:
    push 15
    call check
    jz even 
    jnz odd
    jmp exit
odd:
    mov eax, 4
    mov ebx, 1
    mov ecx, msg1
    mov edx, msg1_len
    int 0x80    
    jmp enter
even:
    add esp, 4 ;uneeded because theres no more calls, but its good habbit to clear the stack
    mov eax, 4
    mov ebx, 1
    mov ecx, msg2
    mov edx, msg2_len
    int 0x80    
    jmp enter
enter:
    add esp, 4
    mov eax, 4
    mov ebx, 1
    mov ecx, newline
    mov edx, 1
    int 0x80
    jmp exit
check:
    push ebp
    mov ebp, esp
    mov eax, DWORD [ebp + 8]
    test eax, 1
    leave
    ret
exit:
    mov eax, 1
    xor ebx, ebx
    int 0x80
section .data
    msg1 db "odd"
    msg1_len equ $ - msg1
    msg2 db "even"
    msg2_len equ $ - msg2
    newline db 0xa
