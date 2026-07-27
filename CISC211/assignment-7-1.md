```asm
section .text
global _start
_start:
    mov eax, 8
    mov ebx, filename
    mov ecx, 0711o
    int 0x80

    mov eax, 5
    mov ebx, filename
    mov ecx, 2
    mov edx, 0777o
    int 0x80
    mov [file], eax

    mov eax, 4
    mov ebx, [file]
    mov ecx, quote1
    mov edx, quote1_len
    int 0x80

    mov eax, 19 ;included this because its in the directions, but I believe because you're just writing directly after the previous line of text it'll be the same thing. 
    mov ebx, [file]
    xor ecx, ecx
    mov edx, 1
    int 0x80

    mov eax, 4
    mov ebx, [file]
    mov ecx, quote2
    mov edx, quote2_len
    int 0x80

    mov eax, 56
    mov ebx, [file]
    int 0x80

    mov eax, 1
    xor ebx, ebx
    int 0x80

section .data
    quote1 db "To be, or not to be, that is the question", 0xA, "A fool thinks himself to be wise, but a wise man knows himself to be a fool.", 0xA
    quote1_len equ $ - quote1
    quote2 db "Better three hours too soon than a minute too late.", 0xA, "No legacy is so rich as honesty.", 0
    quote2_len equ $ - quote2
    filename db "quotes.txt"
section .bss
    file resb 1
```
