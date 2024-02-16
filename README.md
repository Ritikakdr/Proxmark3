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
