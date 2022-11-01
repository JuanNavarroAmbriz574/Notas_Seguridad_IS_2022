## Objetivo
Download this image file and find the flag.
-   [Download image file](https://artifacts.picoctf.net/c/137/drawing.flag.svg)


## Solución
1. Descargar la imagen.
2. Aplicar strings a la imagen y vemos los ultimos renglones.
``` bash
d="tspan3764">F { 3 n h 4 n </tspan><tspan
         sodipodi:role="line"
         x="107.43014"
         y="132.11588"
         style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;"
         id="tspan3752">c 3 d _ 2 4 3 7 4 6 7 5 }</tspan></text>

```

3. Concatenamos las partes entre corchetes y obtenemos {3nh4nc3d_24374675} y agregamos picoCTF al inicio y obtenemos la bandera.
## Notas