# flag leak
In this challenge we were given an instance to crack. The instance when runned in the Linux WSL thing took and input and kept printing out whatever we typed in, Like this:-

<img width="860" alt="image" src="https://github.com/user-attachments/assets/a8cede3d-077d-43c5-af04-e70fd6776dfa" />

I then proceeded to check the source file they gave for the c program to check for any vulnerabilities. From the hint given (Hint: Format Strings) i had a guess to check for
printf statements without a specific format string. In the source code there was one printf statement which printed out whatever was stored in the story variable without 
using a format string. This printf statement can be overflowed by using multiple %x statements:-

<img width="958" alt="image" src="https://github.com/user-attachments/assets/886f20e3-8d00-4726-8c20-dc19251c5b87" />

Here we can see scanf statement has a specified format string and cant be overflowed.....but if we look below it is being printed like printf(story)...(without format strings)
so we can overflow this, Like this:-

<img width="863" alt="image" src="https://github.com/user-attachments/assets/2c921568-7955-442c-b1a2-b24784706c17" />

After looking at the output it kind of looked like hexadecimal values so i used ":" to get the values:-

<img width="863" alt="Test 2" src="https://github.com/user-attachments/assets/7e5944ea-13fc-45c0-ba48-6b41943f9649" />

I checked individual values and to find the flag:-

<img width="946" alt="image" src="https://github.com/user-attachments/assets/067f4d74-7878-41d5-a627-516185abc51e" />

I found the starting part of the flag at '6f636970' (36th position):-

<img width="959" alt="image" src="https://github.com/user-attachments/assets/c732644d-abab-4d8c-bb87-45309c656602" />

So I got the values from 36 to 45 in this way (got a bit help from AI on how to get these specific values). Here is the picture of the hex values from 36 to 45:-

<img width="869" alt="image" src="https://github.com/user-attachments/assets/1fbde0bb-44ec-4bd0-8ee0-c89fe34733cb" />

I put these values in the converter to get a 4grp jumbled flag which I had to manually unscramble:-

<img width="958" alt="image" src="https://github.com/user-attachments/assets/79561519-c913-4d51-a64b-0f3213189fe5" />

## The flag for this challenge is:- picoCTF{L34k1ng_Fl4g_0ff_St4ck_95f60617}
