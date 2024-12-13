# buffer overflow 0
In this challenge we were given a source code. In the code we can see that our input is being stored in the buf2 variable by copying the input into buf2. But buf2 can only store
16 charecters as shown below:-

<img width="154" alt="image" src="https://github.com/user-attachments/assets/57dd76fc-a88e-4215-9d03-e020c5a90c12" />

so to overflow we have to input someting bigger than 16 chars for it to overflow and trigger the flag. Here is a picture to show the flag output:- 

<img width="865" alt="image" src="https://github.com/user-attachments/assets/b1041680-a10c-4db2-9124-13ca36d849a6" />

## The Flag for this challenge is:- picoCTF{ov3rfl0ws_ar3nt_that_bad_c5ca6248}
