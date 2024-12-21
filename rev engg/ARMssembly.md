# ARMssembly
In this challenge, we were given a chall file which has some code in it and was asked to find the argument for which the program prints "You win". From the code we can see that
for w0=0, the program prints the winning statement:-

![image](https://github.com/user-attachments/assets/2eeb21d1-d3e7-4e77-acea-bf6fd8294570)

![image](https://github.com/user-attachments/assets/f8172f99-a9b2-47b7-8c85-8edd27709e97)

If we look at the func part we can see how the value of w0 is being set. From that we can see which argument is required to set it to 0. Here I wrote the func in readable text
and found the required value/argument (x):-

![image](https://github.com/user-attachments/assets/746e8853-a902-4210-8bf9-18ce89197355)

we can see to set the value to 0 the argument(x) should be equal to 27.
27 in hex is 0x1B.

##The Flag for this challenge is:- picoCTF{0000001B}

