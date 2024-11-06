# Custom Encryption
This challenge was especially tricky as we had to read and understand the python code given. In this challenge we were given how the encryption works and an encrypted file which
needed to be deciphered. 
Here is what i got in my encrypted message thingy:-
a = 88
b = 26
cipher is: [97965, 185045, 740180, 946995, 1012305, 21770, 827260, 751065, 718410, 457170, 0, 903455, 228585, 54425, 740180, 0, 239470, 936110, 10885, 674870, 261240, 293895, 
65310, 65310, 185045, 65310, 283010, 555135, 348320, 533365, 283010, 76195, 130620, 185045]

I looked through the encryption python code trying to understand how it was encrypted. So basically it was generating a key, b_key and shared_key which are all same 
and are being used by the dynamic_xor_encrypt function to create a semi_cipher...which is being passed on to the encrypt function along with the shared_key to get the encrypted
message. The cypher function was multiplying the charecters in plain text(the text that is to be converted into a secret msg) with the key and the number 311.

Now I had to reverse engineer and work my way backwards to write the decryption algorithm....
So I copy pasted all the different generation variable stuff to agn generate the key and all...then i apply the reverse of the encryption, which is dividing every character of 
the cipher with key and 311, and then printing the result which then gave this as the output: "}c138c910_d6tp0rc2d_motsuc{FTCocip"

Here is my decryptor python script(I used help form google for syntax and other stuff....i dont know python oops):-
```
def generator(g, x, p):
  return pow(g, x) % p

def decrypt(cipher, key):
  decrypted_text = ""
  for number in cipher:
      decrypted_num = number // (key * 311)
      decrypted_text += chr(decrypted_num)
  return decrypted_text

def dynamic_xor_decrypt(ciphertext, text_key):
  decrypted_text = ""
  key_length = len(text_key)
  for i, char in enumerate(ciphertext):
    key_char = text_key[i % key_length]
    decrypted_char = chr(ord(char) ^ ord(key_char))
    decrypted_text += decrypted_char
  return decrypted_text

a = 88
b = 26
p = 97
g = 31
cipher = [97965, 185045, 740180, 946995, 1012305, 21770, 827260, 751065, 718410, 457170, 0, 903455, 228585, 54425, 740180, 0, 239470, 936110, 10885, 674870, 261240, 293895, 65310, 65310, 185045, 65310, 283010, 555135, 348320, 533365, 283010, 76195, 130620, 185045]
u = generator(g, a, p)
v = generator(g, b, p)
shared_key = generator(v, a, p)
ciphertext = decrypt(cipher, shared_key)
print(dynamic_xor_decrypt(ciphertext, "trudeau"))
```

Upon inspection it was pretty clear the output was the reverse of the flag....so I put it into an online reverse text decrptor which gave me the flag(which is given below).

## The flag for this challenge:- picoCTF{custom_d2cr0pt6d_019c831c}
