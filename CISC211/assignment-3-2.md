<img width="641" height="1012" alt="Blank diagram (1)" src="https://github.com/user-attachments/assets/88c741b1-f037-4e7a-8d9a-57dd70f98a59" />

Challenges
For me, xor what quite easy to understand. I already understand bitwise operations so xor was very easy. On the other hand, TEST was a little bit more difficult to understand. Although I quickly understood the usage of the and operation, it took me a bit to understand where the result went and the purpose. After this, it also took me a bit to figure out a practical manor of demonstrating both the TEST and XOR instructions, but after I figred that out, the coding process was relatively simple. 

```assembly
global _start

section .text

_start:
    mov eax, [data]

    test eax, eax ;test is basically and so 4 and 4 is 4, but if we did test using 4 and 0 it would return 0 because 4 in binary is 0100 while 0 is 0000 leading to test setting zf to 0 this then leads to the jz and jnz commands which will handle when the result of test is zero or not zero. 
    jz handle_zero

    test eax, 1
    jz handle_even
    jnz handle_odd ;extra line which could be just replaced with jump in order to demonstrate jnz and jz
    jmp exit

handle_zero:
    mov eax, 4
    mov ebx, 1
    mov ecx, msg_zero
    mov edx, msg3
    int 0x80
    jmp exit

handle_odd:
    mov eax, 4
    mov ebx, 1
    mov ecx, msg_odd
    mov edx, msg2
    int 0x80
    jmp exit

handle_even:
    mov eax, 4
    mov ebx, 1
    mov ecx, msg_even
    mov edx, msg1
    int 0x80
    jmp exit

;in this exit method, xor is used to change ebx to 0 in order to tell the system that the program exits with no errors using ebx, the first argument.
exit:
    mov eax, 1
    xor ebx, ebx
    int 0x80


section .data
    msg_even db "The value is even", 0xA
    msg1 equ $ - msg_even
    msg_odd db "The value is odd", 0xA
    msg2 equ $ - msg_odd
    msg_zero db "The value is zero", 0xA
    msg3 equ $ - msg_zero

    data db 4
```
