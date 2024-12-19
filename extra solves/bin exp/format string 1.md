# format string 1.md
This challenge said, "Patrick and Sponge Bob were really happy with those orders you made for them, but now they're curious about the secret menu. Find it, and along the way, 
maybe you'll find something else of interest!" and we were given a source and binary file. I opened the source code and found it had the same bug as format string 0.

![image](https://github.com/user-attachments/assets/73653b68-fd12-4a9e-8bd3-d2e0079e9164)

So I ran the instance in wsl and used the %x exploit, which gave hex output. I put in the hex decoder and it was unreadable text:-

![image](https://github.com/user-attachments/assets/ff17f941-9597-4b64-84d8-09ccb0d4bfbb)

![image](https://github.com/user-attachments/assets/6fbcc4ea-20dc-4b08-9315-e0cd9092cc1c)

So then I decided to look at the hints. The first clue gave me a link to a reading material on format strings and the second clue said, "Is this a 32-bit or 64-bit binary?" 
As I was reading through the material in the exploits sections I saw that, %x is used for 32-bit binary and %lx is used for 64-bit binary.

![image](https://github.com/user-attachments/assets/d42e0eb9-10f8-4e17-a8b0-0943d82e978c)

so then I returned to wsl and used %lx instead of %x.

![image](https://github.com/user-attachments/assets/f6fa1606-e6f7-4c39-bf4a-9d986f033f69)

I took the new hex dump and put it in the converter to get a flag which was inverted every 8 characters (which I manually had to invert):-

![image](https://github.com/user-attachments/assets/b31830ed-0e46-42bd-9a71-d6aefba54c0d)

## The flag for this challenge is:- picoCTF{4n1m41_57y13_4x4_f14g_9135fd4e}




