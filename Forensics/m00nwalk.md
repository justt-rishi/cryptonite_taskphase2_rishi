# m00nwalk
In this challenge we were supposed to decrypt an audio file that was sent from the moon. Upon listening to the audio file....I coulndt understand anything and dint know what to
do. I then went and looked at the hints section and saw the 1st hint. It said "How did pictures from the moon landing get sent back to Earth?".

I opened google and some research on the topic gave light to the information that the images from the moon were converted to audio files and sent back to earth using this thing called SSTV....."Slow Scan 
television (SSTV) is a picture transmission method used mainly by amateur radio operators, to transmit and receive static pictures via radio in monochrome or color. The 
Apollo TV cameras used SSTV to transmit images from inside Apollo 7, Apollo 8, and Apollo 9, as well as the Apollo 11 Lunar Module television from the Moon.". 
Thats when it struck to me....I had to convert the audiofile into a picture to get the flag. Then I opened the internet once again and researched on how to use the SSTV 
encrypter thing. 

I stumbled upon this website which gave me the steps to convert the audio to an image...."https://ourcodeworld.com/articles/read/956/how-to-convert-decode-a-slow-scan-
television-transmissions-sstv-audio-file-to-images-using-qsstv-in-ubuntu-18-04". I followed the steps in the tutorial and tried converting the audio....thats when the second 
hint came into play....."What is the CMU mascot?, that might help select a RX option". The CMU mascot is Scotty the Scottie Dog. This hinted that we should select "Scottie 1" 
as QSSTV's "Mode". I also had to select "Auto Slant" via trial and error. I then proceeded to hit the play button and then got this image:- 

![m00nwalk final image](https://github.com/user-attachments/assets/df43e5ae-840b-42a0-b084-3efff90d1971)


Looking at the image we can clearly see the flag is upside down.

## The Flag for this challenge is:-picoCTF{beep_boop_im_in_space}
