# tunn3l v1s10n

In this challenge, I guess the file is probably a correct file but with a malformed header or something. I try to find what kind of file it is by checking it in the exiftool.
From this I got to know it was a BMP file:-

<img width="326" alt="image" src="https://github.com/user-attachments/assets/19627ff0-43b4-43d6-9c94-ca4b3216a47a" />

So I have a BMP image with a broken header.

After searching on web for the specifications I found this table:-

![BMP header](https://www.dynamsoft.com/codepool/img/2016/12/BMP-file-structure.PNG)

Now I have to edit the bmp file so it can be opened, so I load my file to HexEdit:-
![image](https://github.com/user-attachments/assets/7948a583-300b-4f48-bf14-3e6a858d148c)

So here in my file I have the magic bytes `42 4D` then a size of 0x2c268e bytes, and the offset for the pixel array is 0xd0ba.

Then goes the DIB header, and here it seems off, as it also indicates a size of 0xd0ba for the header, while it should only be 40 bytes! So let's change it, and replace 
`BA D0` by `28 00`, and save the image with a BMP extension.

With these changes I was able to open the bmp file.
I get a weird image, so probably I also need to modify the offset of where the pixel array can be found, so I change it to 54 bytes like in the specification. I get an image
saying "not the flag":-

![image](https://github.com/user-attachments/assets/c753769e-fb2d-4082-a965-f14dcd0ac50b)

It looks like this is not the flag... And here I remark that the image I got before changing the offset was slightly different (there was more image above the `notaflag` part). 
This means my image must be bigger.

This means if I change the height of the image we can probably find the flag.
I just needed to find the height of my image. Recall that there are 0x2c268e bytes in total, a 54 bytes header and 1134 pixels width, with 3 bytes per pixel. Thus my height 
is:

```python
(0x2c268e - 54) // (3*1134) = 850
```

So I input 850 = 0x352 in the header.

![image](https://github.com/user-attachments/assets/c60344ad-6cc4-4310-a859-a62b6810c764)

And here is the flag:

![image](https://github.com/user-attachments/assets/e2ab5c3a-19d3-4358-8df9-c071793b98bd)

## The Flag for this challenge is:- picoCTF{qu1t3_a_v13w_2020}
