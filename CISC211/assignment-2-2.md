<img width="241" height="1606" alt="Blank diagram" src="https://github.com/user-attachments/assets/8d996f88-9465-47bc-aa40-7169bd925976" />

Challenges I faced
```
Some challenges I faced included learning how to use assembly. Because I haven't worked with assembly in a while, it was a bit difficult to adjust. After that, I realized I had been writing assembly as if I was writing 64 bit assembly. This meant that when I finally moved to Juypter Lab, my program didn't compile because it was the wrong version. Luckily the fix was quite easy and I just had to swap the register names and change syscall to int 0x80. Overall, I didn't run into many challenges and I improved at assembly.
```

```assembly
section .data
  msg db "I came,",0xA
  msg_len equ $ - msg
  msg2 db "I saw,",0xA
  msg2_len equ $ - msg2
  msg3 db "I conquered.",0xA
  msg3_len equ $ - msg3

section .text
  global _start

_start:
  mov eax, 4
  mov ebx, 1
  mov ecx, msg
  mov edx, msg_len
  int 0x80

  mov eax, 4
  mov ebx, 1
  mov ecx, msg2
  mov edx, msg2_len
  int 0x80

  mov eax, 4
  mov ebx, 1
  mov ecx, msg3
  mov edx, msg3_len
  int 0x80

  mov eax, 1
  mov ebx, 0
  int 0x80
```
