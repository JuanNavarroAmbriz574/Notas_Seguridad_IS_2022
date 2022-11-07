## Objetivo
**A type of transposition cipher is the rail fence cipher, which is described [here](https://en.wikipedia.org/wiki/Rail_fence_cipher). Here is one such cipher encrypted using the rail fence with 4 rails. Can you decrypt it?Download the message [here](https://artifacts.picoctf.net/c/273/message.txt).Put the decoded message in the picoCTF flag format, `picoCTF{decoded_message}`.**

## Solución
1. Descargamos el mensaje encriptado.
``` shell
Ta _7N6D8Dhlg:W3D_H3C31N__387ef sHR053F38N43DFD i33___N6                                                                                                                                                                      
```
2. Usamos una herramienta decodificadora de rail fence y establecemos los rails a 4 y obtenemos la bandera. Puedes usar la siguiente herramienta https://www.boxentriq.com/code-breaking/rail-fence-cipher#:~:text=Rail%20Fence%20Cipher%20%2D%20Decoder%20and%20Encoder&text=In%20a%20rail%20fence%20cipher,place%20for%20the%20first%20letter.
FLAG: WH3R3_D035_7H3_F3NC3_8361N_4ND_3ND_83F6D8D7

## Notas