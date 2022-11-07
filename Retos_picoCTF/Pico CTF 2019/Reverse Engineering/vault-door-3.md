## Objetivo
This vault uses for-loops and byte arrays. The source code for this vault is here: [VaultDoor3.java](https://jupiter.challenges.picoctf.org/static/a648ca6dd275b9454c5d0de6d0f6efd3/VaultDoor3.java)

## Solución
1. Descargamos el código fuente y lo vemos.
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ cat VaultDoor3.java 
import java.util.*;

class VaultDoor3 {
    public static void main(String args[]) {
        VaultDoor3 vaultDoor = new VaultDoor3();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
        String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
        if (vaultDoor.checkPassword(input)) {
            System.out.println("Access granted.");
        } else {
            System.out.println("Access denied!");
        }
    }

    // Our security monitoring team has noticed some intrusions on some of the
    // less secure doors. Dr. Evil has asked me specifically to build a stronger
    // vault door to protect his Doomsday plans. I just *know* this door will
    // keep all of those nosy agents out of our business. Mwa ha!
    //
    // -Minion #2671
    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        char[] buffer = new char[32];
        int i;
        for (i=0; i<8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (; i<16; i++) {
            buffer[i] = password.charAt(23-i);
        }
        for (; i<32; i+=2) {
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) {
            buffer[i] = password.charAt(i);
        }
        String s = new String(buffer);
        return s.equals("jU5t_a_sna_3lpm18gb41_u_4_mfr340");
    }
}

```
El código lo que hace es que pregunta al usuario por una contraseña, luego el programa llama a la funcion checkPassword y modifica la contraseña original y la compara con jU5t_a_sna_3lpm18gb41_u_4_mfr340, entonces para obtener la contraseña original correcta tenemos que partir de jU5t_a_sna_3lpm18gb41_u_4_mfr340 y aplicar el proceso inverso aplicado en la función checkPassword. Vamos a aplicar el proceso inverso usando javaScript.

``` js
var password = "jU5t_a_sna_3lpm18gb41_u_4_mfr340"
var buffer = Array(32);

for (i=0; i<8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (; i<16; i++) {
            buffer[i] = password.charAt(23-i);
        }
        for (; i<32; i+=2) {
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) {
            buffer[i] = password.charAt(i);
        }

console.log(buffer.join(""));
```
El resultado de ejecutar el código de arriba es :jU5t_a_s1mpl3_an4gr4m_4_u_1fb380
FLAG: picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_1fb380}
## Notas