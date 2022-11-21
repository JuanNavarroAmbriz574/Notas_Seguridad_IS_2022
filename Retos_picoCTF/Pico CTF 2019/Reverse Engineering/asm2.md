## Objetivo
What does asm2(0x4,0x21) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://jupiter.challenges.picoctf.org/static/7e3eb2f90200ac88126f62ceb4bc3948/test.S)

## Solución 
1. Descargamos el código fuente y vemos el contenido.
``` text
asm2:
	<+0>:	push   ebp
	<+1>:	mov    ebp,esp
	<+3>:	sub    esp,0x10
	<+6>:	mov    eax,DWORD PTR [ebp+0xc]
	<+9>:	mov    DWORD PTR [ebp-0x4],eax
	<+12>:	mov    eax,DWORD PTR [ebp+0x8]
	<+15>:	mov    DWORD PTR [ebp-0x8],eax
	<+18>:	jmp    0x509 <asm2+28>
	<+20>:	add    DWORD PTR [ebp-0x4],0x1
	<+24>:	add    DWORD PTR [ebp-0x8],0x74
	<+28>:	cmp    DWORD PTR [ebp-0x8],0xfb46
	<+35>:	jle    0x501 <asm2+20>
	<+37>:	mov    eax,DWORD PTR [ebp-0x4]
	<+40>:	leave  
	<+41>:	ret    

```

2. Pasamos correr el código a mano.


- Lo primero que hace la funcion es guardar los parámetros en la plia, en este caso es 0X4,0X21
Simulación de pila y guarda la direción de retorno
[return adress]
[0x4]
[0x21]
Pila de registros (eax)
[]

- Luego se crea un apuntador de la funcion que llama a la subrutina.
Simulación de pila y guarda la direción de retorno
[ebp] -> Apuntador a el main del código y tambien el apuntador esp que apunta al tope de la pila
[return adress]
[0x4]
[0x21]
Pila de registros
[]

- Reservamos 4 espacios de 4 bytes en la pila

Simulación de pila de ejecución
[   ] -> ESP
[   ]
[   ]
[   ]
[Main] -> EBP
[return adress]
[0x4]
[0x21]
Pila de registros (eax)
[]

- La siguiente instrucción lo que dice es que guardemos el primer parametro en eax o en la pila de registros.

Simulación de pila de ejecución
[   ] -> ESP
[   ]
[   ]
[   ]
[Main] -> EBP
[return adress]
[0x4]
[0x21]
Pila de registros (eax)
[0x21]

-  Luego dice que el valor en eax lo ponga en la posición ebp-0x4 de la pila de ejecución quedando de la sisguiente forma.

Simulación de pila de ejecución
[   ] -> ESP -> EBP - 0xC
[   ] -> EBP - 0x8
[   ] -> EBP - 0X4
[0x21]
[Main] -> EBP
[return adress] -> EBP + 0x4
[0x4] -> EBP + 0x8
[0x21] -> EBP + 0xc
Pila de registros (eax)
[0x21]


-  Luego la siguiente instrucción dice que copie el valor de eax a la posición EBP - 0X4 de la pila de ejecución.
Simulación de pila de ejecución
[   ] -> ESP -> EBP - 0xC
[   ] -> EBP - 0x8
[ 0x21  ] -> EBP - 0X4
[0x21]
[Main] -> EBP
[return adress] -> EBP + 0x4
[0x4] -> EBP + 0x8
[0x21] -> EBP + 0xc
Pila de registros (eax)
[0x21]

- Luego tomo el valor de EBP + 0x8 y lo coloco en eax.
Simulación de pila de ejecución
[   ] -> ESP -> EBP - 0xC
[   ] -> EBP - 0x8
[ 0x21  ] -> EBP - 0X4
[0x21]
[Main] -> EBP
[return adress] -> EBP + 0x4
[0x4] -> EBP + 0x8
[0x21] -> EBP + 0xc
Pila de registros (eax)
[0x4]

- La siguiente instrucción toma el valor de eax y lo coloca en la posición EBP - 0x8 de la pila de ejecución.
Simulación de pila de ejecución
[   ] -> ESP -> EBP - 0xC
[  0x4 ] -> EBP - 0x8
[ 0x21  ] -> EBP - 0X4
[0x21]
[Main] -> EBP
[return adress] -> EBP + 0x4
[0x4] -> EBP + 0x8
[0x21] -> EBP + 0xc
Pila de registros (eax)
[0x4]

- Luego pasamos a la linea 28, la cual nos pide una comparación de los valores ebp-0x8,0xfb46 y comparamos si el valor en la posición ebp-0x8 <= 0xfb46.
``` python
>>> 0x4 <= 0xfb46
True
```
 vemos que asi es, por lo que sallta a la línea 20.

si seguimos ejecutando el código veremos que se trata de un ciclo que lo que hace es imcrementar el valor de EBP - 0x8 en 0x78 y el valor de EBP-0x4 en 0x1 minetras EBP - 0x8 sea menor o igual 0xfb46
por lo que calculamos cual sera el valor final de  EBP-0x4.

```python
>>> 0xfb46 / 0x74
554.5344827586207
>>> hex(33+555)
'0x24c
```

Al final el valor de EBP-0x4 es el valor de retorno de la función, por lo que 0x24c es la bandera.
## Notas
