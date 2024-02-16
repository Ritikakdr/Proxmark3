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
