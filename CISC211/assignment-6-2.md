<img width="493" height="857" alt="Blank diagram" src="https://github.com/user-attachments/assets/268c2b71-8e5d-4fba-845c-db79ad543658" />

In this one I didn't have too many challenges. The main issue I faced was learning how to use functions. When writing this program, I had to refer to the lesson to remember how to write functions and take arguments. Afer that there wasn't very many issues. One issue I had that I caused myself was due to me calling add esp, 4 after calling the function. This was an issue because it updates the zero flag, therfore causing the code to check if the number from check was odd or even. So instead, I put the add esp, 4 within the odd and even functions so that it doesn't update the zero flag to early. After this there weren't too many issues. 

```assembly
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
```
