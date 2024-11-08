# Trivial Flag Transfer Protocol
The main goal of this challenge is to figure out how they moved the flag and using that somehow come to the flag. In the description, we were also given a file. After i downloaded
the file and opened it on my file explorer....I came to find out it was a pcapng file. Upon browsing the topic I got to know that a pcapng file is a file format for captured 
packets, looking more into the topic I learned that we had to use the Wireshark application to open files of such format and proceeded to download it.

After the download was complete I opened the pcap file in wireshark and extracted the files with TFTP, which gave me 6 more files (2 text, 3 bmp and 1 deb files). "A BMP file, 
or Bitmap Image File, is a raster-based file format that stores digital images in color or black and white." was the definition for bmp files. This is where i was able to get 
the meaning of the only hint given "What are some other ways to hide data?". It was pretty clear the the flag was most likely hidden in one of those 3 bmp files.

A .deb file is an installation file, which 7zip can open, for some reason. Inside, we find archive named data.tar. We can open this with tar -xvf data.tar. This extracts a 
directory. Searching through it we find a folder usr/share/doc/steghide. The flag is likely encrypted in one of the bmps with the steghide program, which needs a password.

Now we need to find the password and my first approach was to look for clues in the 2 txt files....Instructions.txt and plan were the 2 text files we extracted. both text files 
with a bunch of letters that are all capitals. It was safe for me to assume it was a cipher and the only cipher Ive heard of was the a caesar cipher.Using a caesar cipher solver, 
we get these 2 messages from the files:

Instructions.txt: TFTPDOESNTENCRYPTOURTRAFFICSOWEMUSTDISGUISEOURFLAGTRANSFER.FIGUREOUTAWAYTOHIDETHEFLAGANDIWILLCHECKBACKFORTHEPLAN

plan: IUSEDTHEPROGRAMANDHIDITWITH-DUEDILIGENCE.CHECKOUTTHEPHOTOS

(The shift for both the files was 13 btw)

The author of the plan used "the program", likely referring to steghide, with the password DUEDILIGENCE


Then I tried using the steghide (learnt how to use it from the manual) program on wsl with the password as the argument but it said I had to download the steghide program 
to my pc doing:-
```
root@Lucky:~$ apt install steghide
```

After the installation I was properly able to use the program and this is how i got the flag:- 
```
root@Lucky:~$ steghide extract -sf picture1.bmp -p DUEDILIGENCE
steghide: could not extract any data with that passphrase!
root@Lucky:~$ steghide extract -sf picture2.bmp -p DUEDILIGENCE
steghide: could not extract any data with that passphrase!
root@Lucky:~$ steghide extract -sf picture3.bmp -p DUEDILIGENCE
wrote extracted data to "flag.txt".
root@Lucky:~$ cat flag.txt
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
root@Lucky:~$
```
## The Flag for this challenge is picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
 

