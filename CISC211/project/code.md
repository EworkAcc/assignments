```asm
section .text
global _start
_start:
    mov esi, wordlength
    mov ecx, 0
.loop:
    cmp esi, ecx
    jle exit
    mov al, [secretword + ecx]

    xor al, [secretcode + ecx]
    mov [encoded + ecx], al

    add ecx, 1
    jmp .loop
exit:
    mov eax, 8 
    mov ebx, filename
    mov ecx, 0711o
    int 0x80

    mov eax, 5
    mov ebx, filename
    mov ecx, 1
    mov edx, 0777o
    int 0x80
    mov [file], eax

    mov eax, 4
    mov ebx, [file]
    mov ecx, message1
    mov edx, message1_len
    int 0x80

    mov eax, 4
    mov ebx, [file]
    mov ecx, secretword
    mov edx, wordlength
    int 0x80

    mov eax, 4
    mov ebx, [file]
    mov ecx, newline
    mov edx, 1
    int 0x80

    mov eax, 4
    mov ebx, [file]
    mov ecx, message2
    mov edx, message2_len
    int 0x80

    mov eax, 4
    mov ebx, [file]
    mov ecx, secretcode
    mov edx, wordlength
    int 0x80

    mov eax, 4
    mov ebx, [file]
    mov ecx, newline
    mov edx, 1
    int 0x80

    mov eax, 4
    mov ebx, [file]
    mov ecx, message3
    mov edx, message3_len
    int 0x80

    mov eax, 4
    mov ebx, [file]
    mov ecx, encoded
    mov edx, wordlength
    int 0x80

    mov eax, 4
    mov ebx, [file]
    mov ecx, newline
    mov edx, 1
    int 0x80

    mov eax, 4
    mov ebx, [file]
    mov ecx, message4
    mov edx, message4_len
    int 0x80

    mov esi, wordlength
    mov ecx, 0
    .loop2:
        cmp esi, ecx
        jle exit2
        mov al, [encoded + ecx]
    
        xor al, [secretcode + ecx]
        mov [decoded + ecx], al
    
        add ecx, 1
        jmp .loop2

    exit2:

    mov eax, 4
    mov ebx, [file]
    mov ecx, decoded
    mov edx, wordlength
    int 0x80

    mov eax, 6
    mov ebx, [file]
    int 0x80

    mov eax, 1
    xor ebx, ebx
    int 0x80

section .data
    newline db 0xa
    filename db "output.txt", 0
    secretword db "HELLO"
    secretcode db "world"
    wordlength equ $ - secretcode
    message1 db "Plain text: "
    message1_len equ $ - message1
    message2 db "Key: "
    message2_len equ $ - message2
    message3 db "Encrypted text: "
    message3_len equ $ - message3
    message4 db "Decrypted text: "
    message4_len equ $ - message4

section .bss
    encoded resb wordlength
    decoded resb wordlength
    file resd 1
```
