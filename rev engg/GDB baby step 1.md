# GDB baby step 1
First, I needed to learn what GDB(GNU Debugger) is. I Googled it and learned that it is a tool that helps developers debug programs written in C, C++, and other languages.
So then I started gdb and set up a breakpoint at main, after this I disassembled main:-
```
(gdb) disassemble main
Dump of assembler code for function main:
   0x0000000000001129 <+0>:	endbr64
   0x000000000000112d <+4>:	push   %rbp
   0x000000000000112e <+5>:	mov    %rsp,%rbp
   0x0000000000001131 <+8>:	mov    %edi,-0x4(%rbp)
   0x0000000000001134 <+11>:	mov    %rsi,-0x10(%rbp)
   0x0000000000001138 <+15>:	mov    $0x86342,%eax
   0x000000000000113d <+20>:	pop    %rbp
   0x000000000000113e <+21>:	ret
End of assembler dump.
(gdb)
```
If we observe closely, we can see that 0x86342 is being moved to %eax(assuming mov is move). Then I searched up the command for printing in gdb(Which is p) and used it to print
the value of eax. Looking 0x86342 we can tell its a hex value. So I used an online converter to convert into decimal which gave the value "549698".

## The flag for this challenge is:- picoCTF{549698}

