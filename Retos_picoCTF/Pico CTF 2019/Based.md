## Objetivo
To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337? Connect with `nc jupiter.challenges.picoctf.org 29221`.

## Solución
La primera codificación estaba en binario, se pasó de binario a ASCII
La segunda códificación estaba en octal, se pasó de ocatal a ASCII
La tercera codificación estaba en hexadecimal, se pasó de hexadecimal a ASCII.

``` bash

juan574-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 29221
Let us see how data is stored
sludge
Please give the 01110011 01101100 01110101 01100100 01100111 01100101 as a word.
...
you have 45 seconds.....

Input:
sludge
Please give me the  163 157 143 153 145 164 as a word.
Input:
socket
Please give me the 6c616d70 as a word.
Input:
lamp
You've beaten the challenge
Flag: picoCTF{learning_about_converting_values_00a975ff}

```

## Notas