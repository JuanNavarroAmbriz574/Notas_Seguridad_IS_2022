## Objetivo
What does asm1(0x6fa) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://jupiter.challenges.picoctf.org/static/b41e08fc19ceb9d0466ebd68d36c5630/test.S)

## Solución
1. Descargamos el código fuente en ensamblador y revisamos su contenido
``` text
asm1:
	<+0>:	push   ebp
	<+1>:	mov    ebp,esp
	<+3>:	cmp    DWORD PTR [ebp+0x8],0x3a2
	<+10>:	jg     0x512 <asm1+37>
	<+12>:	cmp    DWORD PTR [ebp+0x8],0x358
	<+19>:	jne    0x50a <asm1+29>
	<+21>:	mov    eax,DWORD PTR [ebp+0x8]
	<+24>:	add    eax,0x12
	<+27>:	jmp    0x529 <asm1+60>
	<+29>:	mov    eax,DWORD PTR [ebp+0x8]
	<+32>:	sub    eax,0x12
	<+35>:	jmp    0x529 <asm1+60>
	<+37>:	cmp    DWORD PTR [ebp+0x8],0x6fa
	<+44>:	jne    0x523 <asm1+54>
	<+46>:	mov    eax,DWORD PTR [ebp+0x8]
	<+49>:	sub    eax,0x12
	<+52>:	jmp    0x529 <asm1+60>
	<+54>:	mov    eax,DWORD PTR [ebp+0x8]
	<+57>:	add    eax,0x12
	<+60>:	pop    ebp
	<+61>:	ret    

```
2. Ejecutamos el código de arriba a mano

- Lo primero que hace la funcion es guardar los paramentros en la plia, en este caso es 0x6fa
Simulación de pila y guarda la direción de retorno
[return adress]
[0x6fa]
Pila de registros
[]

- Luego se crea un apuntador al main de la funcion.
Simulación de pila y guarda la direción de retorno
[Main] -> EBP
[return adress]
[0x6fa]
Pila de registros
[]

- Compara si [ebp+0x8] es mayor a 0x3a2, pero sabemos que ebp+0x8 hace referencia al priemr parámetro es deicr ebp+0x8 = 0X6fa por lo que vemos que si es cierto.
``` python
>>> 0X6fa > 0x3a2
True
```

- Como se cumplió la condición de arriba el programa se salta a la línea 37 del código, esta línea lo que nos hace es comparar estos 2 valores [ebp+0x8] = 0X6fa, 0x6fa y ver que no sean iguales, por lo que a simple vista se ve que son igauales por lo que sigue con la siguiente instrución.


- La siguiente instrucción me dice que guarde el valor del parametro 1 en eax o pila de registros
Simulación de pila y guarda la direción de retorno
[Main] -> EBP
[return adress]
[0x6fa]
Pila de registros
[0x6fa]

- La siguiente instrucción del código nos pide restar  a eax el valor de  0x12, el resultado de la operación es 0x6e8 y se guarda en la pila de registros

[Main] -> EBP
[return adress]
[0x6fa]
Pila de registros
[0x6e8]

- Luego saltamos a la línea 60, pero esta línea nos dice que retornenmos el valor resultante en eax por lo que la bandera es 0X6e8

## Notas
El lenguaje ensamblador o _assembler_ (en inglés: _assembler language_ y la abreviación _**asm**_) es un [lenguaje de programación](https://es.wikipedia.org/wiki/Lenguaje_de_programaci%C3%B3n "Lenguaje de programación") de [bajo nivel](https://es.wikipedia.org/wiki/Lenguaje_de_bajo_nivel "Lenguaje de bajo nivel"). Consiste en un conjunto de [mnemónicos](https://es.wikipedia.org/wiki/Mnem%C3%B3nico "Mnemónico") que representan instrucciones básicas para los [computadores](https://es.wikipedia.org/wiki/Computadora_electr%C3%B3nica "Computadora electrónica"), [microprocesadores](https://es.wikipedia.org/wiki/Microprocesador "Microprocesador"), [microcontroladores](https://es.wikipedia.org/wiki/Microcontrolador "Microcontrolador") y otros [circuitos integrados](https://es.wikipedia.org/wiki/Circuito_integrado "Circuito integrado") programables

El leguaje ensamblador cambia dependiendo de la arquitectura de la maquina.