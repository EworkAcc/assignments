<img width="514" height="700" alt="Blank diagram" src="https://github.com/user-attachments/assets/f414286d-52db-423c-9374-15d080a0c49c" />

Challenges
I faced a few challenges during this assignment. The main two were division and multiplication. I often use the add and sub commands in assembly so it wasn't that hard for me to remember how to use them, but for multiplication and division, I don't often use them. This mean that I had to relearn how to use them. For multiplication, it was pretty simple, I just had to use the imul instruction. I used imul instead of just mul because many of the instances where multiplcation was used included negative numbers. This mean, that unlike when division was used, a signed operation was needed. In this instance, division was a little harder. Although I didn't use negative numbers, so a signed division was unneeded, I still didn't remember how to use division. After a bit of studying, I was able to figure out that the numerator had to be in eax while the denominator could be in a variable or register that you called div with. After this, running it was quite easy. Overall, this program wasn't extremely challenging, but it was quite helpful in allowing me to relearn some asm operations.

1.
```assembly
global _start

section .texta

_start:
    mov eax, [var1]
    neg eax
    imul eax, 10
    mov [result], eax

    mov eax, 1
    mov ebx, 0
    int 0x80

section .data
    var1 dd 5
    var2 dd 5
    var3 dd 5
    var4 dd 5

section .bss
    result: resd 1
```    
2.
```
global _start

section .text

_start:
    mov eax, [var1]
    add eax, [var2]
    add eax, [var3]
    add eax, [var4]
    mov [result], eax

    mov eax, 1
    mov ebx, 0
    int 0x80

section .data
    var1 dd 5
    var2 dd 5
    var3 dd 5
    var4 dd 5

section .bss
    result: resd 1
```
3.
```
global _start

section .text

_start:
    mov eax, [var1]
    neg eax
    imul eax, [var2]
    add eax, [var3]
    mov [result], eax

    mov eax, 1
    mov ebx, 0
    int 0x80

section .data
    var1 dd 5
    var2 dd 5
    var3 dd 5
    var4 dd 5

section .bss
    result: resd 1
```
4.
```
global _start

section .text

_start:
    mov eax, [var1]
    imul eax, 2
    mov ebx, [var2]
    sub ebx, 3

    mov edx, 0

    div ebx
    mov [result], eax

    mov eax, 1
    mov ebx, 0
    int 0x80

section .data
    var1 dd 5
    var2 dd 5
    var3 dd 5
    var4 dd 5

section .bss
    result: resd 1
```
