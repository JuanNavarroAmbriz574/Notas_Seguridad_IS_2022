
1. Primero obtenemos los factores primos de 10,403, que son 101 y 103 estos valores serán nuestros p y q respectivamente. Por último, con estos valores podemos decodificar el texto dado.
``` python
>>> from Crypto.Util.number import inverse
>>> p = 101
>>> q = 103
>>> c = 99
>>> n = p*q
>>> tn = (p-1)*(q-1)
>>> e = 8743
>>> d = inverse(e,tn)
>>> flag = pow(c,d,n)
>>> flag
9366
```

La badera es: 9366