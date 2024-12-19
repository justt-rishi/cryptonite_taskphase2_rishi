# findme
We were given the login details for the website which were test and test!.

![image](https://github.com/user-attachments/assets/14b1b33b-46e1-4461-950b-b8fd4c1c30a5)

This was what opened up after typing in the passwords:- 

![image](https://github.com/user-attachments/assets/6a222772-ad54-445d-8de6-681d81f3ec46)

After messing around with the website a bit I realized the website had literally nothing to offer, so I decided to look at the clues. The clue said "any redirections".
So then I restarted the instance and this time I had the inspector tool open (in the network tab which showed all the traffic). 

![image](https://github.com/user-attachments/assets/594a1f36-5c2b-4e68-a340-8ce9c587b7f7)

The website is being redirected to these two links before showing the search for flags page. So now I just had to use Burp Suite to intercept between the redirection.
I opened Burp Suite software and used its browser and intercepted each of the redirections. Here is a screenshot of the Burp Suite intercepts.
Redirection 1:-

![image](https://github.com/user-attachments/assets/bef1a798-c423-4ba0-a3f9-ba76452ec166)

Redirection 2:-

![image](https://github.com/user-attachments/assets/5d8316a0-9d48-44c5-bce7-d0806ee361c0)

From the link it was redirection we can see it is a base64 encryption, and the flag is split into these two links. After putting them in a base64 decoder I got the flag:-

![image](https://github.com/user-attachments/assets/b0966264-c832-4b3c-8b13-66950de93658)

## The flag for this challenge is:-picoCTF{proxies_all_the_way_d1c0b112}
