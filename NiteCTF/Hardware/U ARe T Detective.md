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

<img width="959" alt="image" src="https://github.com/user-attachments/assets/cf7fcf72-8225-4077-8c14-36ed9d7ed1ff" />

But after zooming in I found the encryption I was looking for, which looked something like this:-

<img width="959" alt="image" src="https://github.com/user-attachments/assets/897a5a25-ab15-471b-8d08-359dc2b3299c" />

So now I somehow had to decrypt this encryption. So then I started exploring the software and found a button that said: "add protocol decoder". I clicked on it and 
started browsing different decoders. Upon scrolling, I found a decoder named UART. If we look at the name of the challenge only the letters U, A, R, and T were in capitals.
This was for sure the decoder we were supposed to use for this signal.

![image](https://github.com/user-attachments/assets/241be481-9bae-47e4-bcbf-6bc9c6477fd9)

I selected this decoder and routed D1 to the UART receive line:-

<img width="959" alt="image" src="https://github.com/user-attachments/assets/02cb7efb-5609-45ba-a2b6-ca814a0e5067" />

But it was showing a Frame error. Upon research on the error, I got to know we get this error if the sample and decoder settings are not close enough. So now I had
mess with the decoder settings to get the flag. After a long session of trial and error, I landed on these settings:-
1) Baud rate:- 5500000
2) Data bits:- 8
3) Data Format:- ASCII

<img width="395" alt="image" src="https://github.com/user-attachments/assets/ba0b16e2-6ccf-41d4-9a6d-048c4c9c6dcb" />

From here on it was simple as it was just noting down the flag and submitting it.

<img width="959" alt="Flag pic" src="https://github.com/user-attachments/assets/576809ad-91dc-4e31-92e2-b1b7c09d2a67" />

<img width="959" alt="flag pic 2" src="https://github.com/user-attachments/assets/ac99ea2f-d0f0-4fbf-ad27-3f7ac0dab087" />

I had a roller-coaster ride trying to solve these challenges as they were extremely hard, but at the same time super fun and engaging. I wish to participate in more of these
types of challenges and learn more. Thank you so much for this opportunity Team Cryptonite.

## The flag for this challenge is:- nite{n0n_std_b4ud_r4t3s_ftw}
