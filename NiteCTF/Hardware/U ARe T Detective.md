# U ARe T Detective 
This is my first ever hardware challenge/CTF. Disgustingly it's the only challenge I could solve in the Nite CTF challenges. Here is how I went about solving the
challenge.

First, when I opened the challenge, I was told it was a signal received by a detective, and we had to decode it. From this, I got a clue that we had something to do with decoding.
Also, the name of the challenge was a bit suspicious. I kept my suspicions in mind and proceeded with the challenge. We were given a file named signal.sr. This was the first time
I saw a .sr file. So naturally I did some research and got to know that and found the following information:-

A .sr file can refer to a few different types of files, including:
Structured report (SR): A type of DICOM file that's used to share clinical findings and information. SR files can be viewed as images or browsed as text. 
PulseView Sigrok Dump: A popular type of SR file. 
Srank Compressed Data: Another type of SR file.

Upon further research on .sr files, I got to know that we had to use software like PulseView to open files of this format. So I proceeded to download Pulseview.

After the download, I opened the .sr file to find a single line like this:-

![image](https://github.com/user-attachments/assets/458d7017-a480-4998-b536-6ca2ee5940bf)

But after zooming in I found the encryption I was looking for, which looked something like this:-

![image](https://github.com/user-attachments/assets/2e858183-d050-4c4d-a18f-9c5226b64501)

So now I somehow had to decrypt this encryption. So then I started exploring the software and found a button that said: "add protocol decoder". I clicked on it and 
started browsing different decoders. Upon scrolling, I found a decoder named UART. If we look at the name of the challenge only the letters U, A, R, and T were in capitals.
This was for sure the decoder we were supposed to use for this signal.

![image](https://github.com/user-attachments/assets/99b5b479-e77e-41c7-91a0-4914cb341d50)

I selected this decoder and routed D1 to the UART receive line:-

![image](https://github.com/user-attachments/assets/0fb3f023-ea27-4045-9a47-47b5e4ecc0e7)

But it was showing a Frame error. Upon research on the error, I got to know we get this error if the sample and decoder settings are not close enough. So now I had
mess with the decoder settings to get the flag. After a long session of trial and error, I landed on these settings:-
1) Baud rate:- 5500000
2) Data bits:- 8
3) Data Format:- ASCII

![image](https://github.com/user-attachments/assets/a9d5b829-3d9c-4b8b-8d2e-678eff649a5a)

From here on it was simple as it was just noting down the flag and submitting it.

<img width="959" alt="Flag pic" src="https://github.com/user-attachments/assets/576809ad-91dc-4e31-92e2-b1b7c09d2a67" />

<img width="959" alt="flag pic 2" src="https://github.com/user-attachments/assets/ac99ea2f-d0f0-4fbf-ad27-3f7ac0dab087" />

I had a roller-coaster ride trying to solve these challenges as they were extremely hard, but at the same time super fun and engaging. I wish to participate in more of these
types of challenges and learn more. Thank you so much for this opportunity Team Cryptonite.

## The flag for this challenge is:- nite{n0n_std_b4ud_r4t3s_ftw}
