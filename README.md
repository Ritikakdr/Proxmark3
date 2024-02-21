# Proxmark3
## Cloning
### Identify the card
Plug in the proxmark. Open a terminal  and start the Proxmark3 ,In the terminal type in 
>auto
 
This command will help you identify the type of card you are using


Or you can also use 
-  High frequency card
> hf search
- low frequecy card
> lf search
---
Once you've identified the correct reader, use the 
>hf 14a reader

 command to read the data from the RFID card.

After reading the card, you'll want to save the data to a file for later use. You can use the 
> hf mf dump

 command to dump the data to a file.


Use the
> hf mf eload
## BruteForce
An attempt to guess or crack cryptographic keys through an exhaustive search process.

- Select a Low frequency or an high frequency card 


for Low frequency:
> lf search

> lf select [reader]

> lf bruteforce


for High frequency:
>hf search

> hf select [reader]

> hf mf bruteforce

# Attacks

So before getting started , Let's know a bit about the  communication between RFID card, it's reader.
here's how it happens:
- **Intialization**:
The reader initiates the communication by sending out an electromagnetic signal or RF field.
- **Activation**: 
When an RFID card enters this RF field ,the card becomes activated , enabling it to respond to communication requests from the reader.
- **Anti-Collision**:
It's used to prevent signal collisions and ensure proper communication with each card.

- **Request-Response Protocol**:
The reader sends a request command to the RFID card, typically asking for specific data or identification.
RFID card processes the request and responds with the requested data, such as its unique identifier (UID), authentication information.

## Nested Attack


Get the uid of the card

![Screenshot from 2024-02-21 18-05-16](https://github.com/Ritikakdr/Proxmark3/assets/116477443/6833065a-a1e9-403b-b846-c58100e5fb9b)


-now that we have the UID , 
Lets check for some valid keys 
![Screenshot from 2024-02-21 18-05-34](https://github.com/Ritikakdr/Proxmark3/assets/116477443/ffcbd884-836d-445a-b4d2-0a42c211ee94)



-The following image illustrates this attack being executed with Proxmark3 on a victim card:
![Screenshot from 2024-02-21 18-08-00](https://github.com/Ritikakdr/Proxmark3/assets/116477443/dd236850-6238-44ba-97f4-610e5d8a538c)

## Darkside Attacks
The Darkside attack exploits a weakness in the authentication process of RFID cards, specifically the NACK response code. By brute-forcing the NACK code, attackers can decrypt part of the keystream used, potentially compromising the security of the card system.

Here's a breakdown of the steps involved in the attack:

1.  **Initiation**: The attacker sends multiple authentication attempts to the target card with different keys, trying to authenticate using each key. These authentication attempts are typically automated and can be performed rapidly.
    
2.  **Detection of NACK response**: When a wrong key is used, the card responds with a NACK code. This code is typically encrypted with a keystream.
    
3.  **Brute force attack**: The attacker performs a brute force attack to quickly discover the NACK code before it's encrypted. Since the NACK code is small, it's feasible to try all possible combinations in a reasonable amount of time.
    
4.  **Decryption of NACK code**: Once the NACK code is obtained in plaintext, it can be used to perform an XOR operation with the encrypted NACK code received from the card

- If you're not able to find *darkside*. You may need to update your firmware



## Hardnested Attacks


The Hardnested attack, a sophisticated method for cracking MIFARE Classic cards' encryption. It involves collecting a large number of encrypted nonces generated during authentication attempts, analyzing them to reduce the potential key space, and then conducting a brute-force attack to obtain the original encryption key.


Here's a breif explanation of how the attack happens
In the Hardnested attack:

   - The attacker collects 2000 to 4000 nonces generated during authentication.
   - Bit-by-bit analysis is conducted on the nonces to reduce the key space.
   -  A brute-force attack is then performed to obtain the original encryption key.


![Screenshot from 2024-02-21 18-49-08](https://github.com/Ritikakdr/Proxmark3/assets/116477443/32a7eb04-5a05-4d7f-8ad4-23c15dc88f2e)
