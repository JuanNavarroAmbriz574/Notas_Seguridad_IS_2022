## Objetivo
This vault uses ASCII encoding for the password. The source code for this vault is here: [VaultDoor4.java](https://jupiter.challenges.picoctf.org/static/09d3002ae349631324a17e2255ae8df2/VaultDoor4.java)

## Solución
1. Descargamos el código fuente y lo vemos.
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ cat VaultDoor4.java 
import java.util.*;

class VaultDoor4 {
    public static void main(String args[]) {
        VaultDoor4 vaultDoor = new VaultDoor4();
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

    // I made myself dizzy converting all of these numbers into different bases,
    // so I just *know* that this vault will be impenetrable. This will make Dr.
    // Evil like me better than all of the other minions--especially Minion
    // #5620--I just know it!
    //
    //  .:::.   .:::.
    // :::::::.:::::::
    // :::::::::::::::
    // ':::::::::::::'
    //   ':::::::::'
    //     ':::::'
    //       ':'
    // -Minion #7781
    public boolean checkPassword(String password) {
        byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063 , 0163, 0137, 0143, 061 ,
            '9' , '4' , 'f' , '7' , '4' , '5' , '8' , 'e' ,
        };
        for (int i=0; i<32; i++) {
            if (passBytes[i] != myBytes[i]) {
                return false;
            }
        }
        return true;
    }
}

```

Vemos que el programa pide al usuario una contraseña para luego comparar la contraseña con el arreglo de myBytes, lo que podemos hacer es convertir el arreglo de bytes a ascii para obtener la bandera. por lo que modificamos nuestro archivo y lo dejamos de la siguiente forma.
``` java


class VaultDoor4 {
    public static void main(String args[]) {
        VaultDoor4 vaultDoor = new VaultDoor4();
        //Scanner scanner = new Scanner(System.in);
        //System.out.print("Enter vault password: ");
        //String userInput = scanner.next();
        //String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
        //if (vaultDoor.checkPassword(input)) {
            //System.out.println("Access granted.");
        //} else {
          //  System.out.println("Access denied!");
        //}
        vaultDoor.checkPassword("hola");
    }

    // I made myself dizzy converting all of these numbers into different bases,
    // so I just *know* that this vault will be impenetrable. This will make Dr.
    // Evil like me better than all of the other minions--especially Minion
    // #5620--I just know it!
    //
    //  .:::.   .:::.
    // :::::::.:::::::
    // :::::::::::::::
    // ':::::::::::::'
    //   ':::::::::'
    //     ':::::'
    //       ':'
    // -Minion #7781
    public boolean checkPassword(String password) {
        byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063 , 0163, 0137, 0143, 061 ,
            '9' , '4' , 'f' , '7' , '4' , '5' , '8' , 'e' ,
        };
	    /*
        for (int i=0; i<32; i++) {
            if (passBytes[i] != myBytes[i]) {
                return false;
            }
        }
        */
    String flag = new String(myBytes);
    System.out.println(flag);
        
        return true;
    }
}


```

Al ejecutar el programa anterior obtenemos la bandera.
``` sehll
C:\Users\juann\Downloads>javac VaultDoor4.java

C:\Users\juann\Downloads>java VaultDoor4
jU5t_4_bUnCh_0f_bYt3s_c194f7458e
```

## Notas