## Objetive
asm3(0xd2c26416,0xe6cf51f0,0xe54409d5) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://jupiter.challenges.picoctf.org/static/df999527eaecf46f259c4337a820856c/test.S)

## Solution

1. Descargamos el código funete en ensamblador y le damos un vistaso.
``` text
asm3:
	<+0>:	push   ebp
	<+1>:	mov    ebp,esp
	<+3>:	xor    eax,eax
	<+5>:	mov    ah,BYTE PTR [ebp+0x9]
	<+8>:	shl    ax,0x10
	<+12>:	sub    al,BYTE PTR [ebp+0xe]
	<+15>:	add    ah,BYTE PTR [ebp+0xf]
	<+18>:	xor    ax,WORD PTR [ebp+0x12]
	<+22>:	nop
	<+23>:	pop    ebp
	<+24>:	ret    

```
Para completar este reto podriamos correr el código a mano, pero esta vez vamos a utilizar un emulador de amebler.

2. Nos dirigimos al siguiente sitio web https://carlosrafaelgn.com.br/Asm86/
3. Copiamos el código funete y lo pegamos, pero eliminamos los números de línea, ademas de agregar los parametros a la pila, quedaría algo así.
```
start:
	push 0xe54409d5
	push 0xe6cf51f0
	push 0xd2c26416
	call asm3

asm3:
	push   ebp
	mov    ebp,esp
	xor    eax,eax
	mov    ah,BYTE PTR [ebp+0x9]
	shl    ax,0x10
	sub    al,BYTE PTR [ebp+0xe]
	add    ah,BYTE PTR [ebp+0xf]
	xor    ax,WORD PTR [ebp+0x12]
	nop
	pop    ebp
	ret 
	
```

4. Ahora damos click en windows->register y ejecutamos elcódigo hasta llegar a la instrucción nop, y la bandera es el valor que queda en EAX que  en mi caso es 0x375
## Notas