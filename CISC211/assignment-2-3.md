<img width="596" height="915" alt="Blank diagram" src="https://github.com/user-attachments/assets/0e71bcb9-e70e-4a06-8eaf-4d8ab0108887" />

Challenges I faced

When I was doing this assignment, I felt confident in my code, but after finishing I realized I had made some mistakes. First of all, in my original code I had incorrectly decllared the _start method in the .data section. This led to the debugger being unable to find the entry point and caused an error. I quickly noticed this and fixed it. Following this, I also incorrectly used, resb and db. This meant that when trying to move the variables into and out of the 4 byte register eax, the program would not correctly work. I was able to fix this by changing resb and db to resd and dd. This works because resd and dd both work with double words which are four bytes and correctly fit the size of the registers. After this I was able to correctly and smoothly run my code. 

```assembly
section .text
	global _start

_start:
	mov eax, [var1]
	add eax, [var2]
	mov [result], eax

	mov eax, 1 
	mov ebx, 0
	int 0x80

section .bss
	result: resd 1

section .data
	var1 dd 10
	var2 dd 15
```
