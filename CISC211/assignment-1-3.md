Secret Word

```assembly
neovim
```

```assembly
01101110 01100101 01101111 01110110 01101001 01101101
```

Secret Key Word

```assembly
binary
```

```assembly
01100010 01101001 01101110 01100001 01110010 01111001
```

XOR result

```assembly
00001100 00001100 00000001 00010111 00011011 00010100
```

```assembly
0C 0C 01 17 1B 14
```

Using XOR to do decryption

```assembly
00001100 00001100 00000001 00010111 00011011 00010100 ^ 01100010 01101001 01101110 01100001 01110010 01111001 = 01101110 01100101 01101111 01110110 01101001 01101101
```

Explanation of XOR encryption with different length text and keys

```
XOR encryption works when you have different length text and keys by either shortening or repeating keys.
When a text is shorter than a key, the key can be cut off to be the same length as the text.
On the other hand, if the text is longer than the key, the key can be repeated until it is the same length as the text. 
```

Flowchart

<img width="467" height="930" alt="Blank diagram" src="https://github.com/user-attachments/assets/445b0d04-f8e9-4b31-ae2a-c96fbac1e3c5" />

Challenges

```
I faced a few challenges. To start, I struggled to figure out what words to use.
I chose neovim and binary, because I think they are quite related to programming and this assignment.
This other issue I had was figuring out how to use code blocks in github.
This was an issue because I mistakenly forgot to make the file a markdown and instead just left it without the file extension.
This left the file unable to make code blocks, which was an issue I sat with for quite along period of time. 
```
