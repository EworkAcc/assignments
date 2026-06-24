



```assembly
section .text
global _start

section .bss
	result: resd 1

section .data
	var1 dd 10
	var2 dd 15

_start:
	mov eax, [var1]
	add eax, [var2]
	mov [result], eax

	mov eax, 1 
	mov ebx, 0
	int 0x80
```
