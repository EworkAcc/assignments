Question 1
```assembly
; var1 result is 2 var 2 is 3 var 3 is 4 and var2 is 2
section .text
    global _start

_start:
    mov eax, [var1]
    add eax, 2
    mov ecx, [var3]
    sub ecx, [var2]
    div ecx

    mov [result], eax
    add eax, 48
    mov [msg], eax

    mov eax, 4
    mov ebx, 1
    mov ecx, msg
    mov edx, 1
    int 0x80

    mov eax, 1
    xor ebx, ebx
    int 0x80

section .data
    var1 dd 2
    var3 dd 4
    var2 dd 2
    msg db '0', 0xa

section .bss
    result resd 1
```
Table:

Register Name	Value
 	 eax          2
 	 edx          0

<img width="1919" height="1051" alt="Screenshot 2026-07-10 150615" src="https://github.com/user-attachments/assets/82da57a7-8478-4c04-8a25-480d87a3b0da" />



Question 2
```
Y = a + b
```
<img width="663" height="467" alt="WIN_20260710_15_24_21_Pro" src="https://github.com/user-attachments/assets/715d22ed-2353-4b6b-a255-6e91d752d7bc" />

Question 3 
```assembly
section .text
    global _start

_start:
    mov eax, [num]
    test eax, 1
    jz even
    jmp odd

even:
    mov eax, 4
    mov ebx, 1
    mov ecx, msg2
    mov edx, msg2_len
    int 0x80
    jmp exit

odd:
    mov eax, 4
    mov ebx, 1
    mov ecx, msg1
    mov edx, msg1_len
    int 0x80
    jmp exit

exit:
    mov eax, 1
    xor ebx, ebx
    int 0x80

section .data
    num dd 5
    msg1 db 'odd number', 0xa
    msg1_len equ $ - msg1

    msg2 db 'even number', 0xa
    msg2_len equ $ - msg2
```

