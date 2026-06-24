<img width="241" height="1606" alt="Blank diagram" src="https://github.com/user-attachments/assets/8d996f88-9465-47bc-aa40-7169bd925976" />

Challenges I faced
```
Some challenges I faced included learni nghow to use assembly. Because I haven't worked with assembly in a while, it was a bit difficult to adjust. In addition relearning took a while. After that, one other issue I ran into was running the file. My pc runs windows and it was quite annoying to setup mingw to correctly work and run my assembly files. The caused me to utilize my laptop instead. I ended up setting up keymappings to run simple assembly files with Neovim. Overall these were the main issues I ran into.  
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
