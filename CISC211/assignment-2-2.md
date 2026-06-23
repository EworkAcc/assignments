
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
  mov rax, 1
  mov rdi, 1
  mov rsi, msg
  mov rdx, msg_len
  syscall

  mov rax, 1
  mov rdi, 1
  mov rsi, msg2
  mov rdx, msg2_len
  syscall

  mov rax, 1
  mov rdi, 1
  mov rsi, msg3
  mov rdx, msg3_len
  syscall

  mov rax, 60
  mov rdi, 0
  syscall

```
