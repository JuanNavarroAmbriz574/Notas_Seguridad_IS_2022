## Objetivo
We made a lot of substitutions to encrypt this. Can you decrypt it? Connect with `nc jupiter.challenges.picoctf.org 43522`.

## Solución
1. Ejecutamos el comando que nos da la descripción del problema `jupiter.challenges.picoctf.org 43522` y obtenemos lo siguiente.
``` bash

┌──(kali㉿kali)-[~/pico]
└─$ nc jupiter.challenges.picoctf.org 43522
-------------------------------------------------------------------------------
qhjmdpay fudu by whed ozpm - odugeujqw_by_q_hxud_zpinkp_hmoipejdpo
-------------------------------------------------------------------------------
nuaruuj ey afudu rpy, py b fpxu pzdupkw ypbk yhiurfudu, afu nhjk ho afu yup. nuybkuy fhzkbjm hed fupday ahmuafud afdhemf zhjm tudbhky ho yutpdpabhj, ba fpk afu uoouqa ho ipsbjm ey ahzudpja ho upqf hafud'y wpdjypjk uxuj qhjxbqabhjy. afu zprwudafu nuya ho hzk ouzzhryfpk, nuqpeyu ho fby ipjw wupdy pjk ipjw xbdaeuy, afu hjzw qeyfbhj hj kuqs, pjk rpy zwbjm hj afu hjzw dem. afu pqqhejapja fpk ndhemfa hea pzdupkw p nhv ho khibjhuy, pjk rpy ahwbjm pdqfbauqaedpzzw rbaf afu nhjuy. ipdzhr ypa qdhyy-zummuk dbmfa poa, zupjbjm pmpbjya afu ibccuj-ipya. fu fpk yejsuj qfuusy, p wuzzhr qhitzuvbhj, p yadpbmfa npqs, pj pyquabq pytuqa, pjk, rbaf fby pdiy kdhttuk, afu tpziy ho fpjky hearpdky, duyuinzuk pj bkhz. afu kbduqahd, ypabyobuk afu pjqfhd fpk mhhk fhzk, ipku fby rpw poa pjk ypa khrj pihjmya ey. ru uvqfpjmuk p our rhdky zpcbzw. poaudrpdky afudu rpy ybzujqu hj nhpdk afu wpqfa. ohd yhiu dupyhj hd hafud ru kbk jha numbj afpa mpiu ho khibjhuy. ru ouza iukbapabxu, pjk oba ohd jhafbjm nea tzpqbk yapdbjm. afu kpw rpy ujkbjm bj p yudujbaw ho yabzz pjk uvgebybau ndbzzbpjqu. afu rpaud yfhju tpqbobqpzzw; afu ysw, rbafhea p ytuqs, rpy p nujbmj biiujybaw ho ejyapbjuk zbmfa; afu xudw ibya hj afu uyyuv ipdyf rpy zbsu p mpecw pjk dpkbpja opndbq, fejm odhi afu rhhkuk dbyuy bjzpjk, pjk kdptbjm afu zhr yfhduy bj kbptfpjhey ohzky. hjzw afu mzhhi ah afu ruya, ndhhkbjm hxud afu ettud dupqfuy, nuqpiu ihdu yhindu uxudw ibjeau, py bo pjmuduk nw afu pttdhpqf ho afu yej.

```
Nos damos cuenta que esta codificado usando sustitución monoalfabética por lo que usamos una herramienta como https://www.dcode.fr/monoalphabetic-substitution y obtenemos el siguiente texto.

``` text

------------------------------------------------------------------------------- CONGRATS HERE IS YOUR FLAG - FREQUENCY_IS_C_OVER_LAMBDA_OGFMAUNRAF ------------------------------------------------------------------------------- BETWEEN US THERE WAS, AS I HAVE ALREADY SAID SOMEWHERE, THE BOND OF THE SEA. BESIDES HOLDING OUR HEARTS TOGETHER THROUGH LONG PERIODS OF SEPARATION, IT HAD THE EFFECT OF MAKING US TOLERANT OF EACH OTHER'S YARNSAND EVEN CONVICTIONS. THE LAWYERTHE BEST OF OLD FELLOWSHAD, BECAUSE OF HIS MANY YEARS AND MANY VIRTUES, THE ONLY CUSHION ON DECK, AND WAS LYING ON THE ONLY RUG. THE ACCOUNTANT HAD BROUGHT OUT ALREADY A BOJ OF DOMINOES, AND WAS TOYING ARCHITECTURALLY WITH THE BONES. MARLOW SAT CROSS-LEGGED RIGHT AFT, LEANING AGAINST THE MIXXEN-MAST. HE HAD SUNKEN CHEEKS, A YELLOW COMPLEJION, A STRAIGHT BACK, AN ASCETIC ASPECT, AND, WITH HIS ARMS DROPPED, THE PALMS OF HANDS OUTWARDS, RESEMBLED AN IDOL. THE DIRECTOR, SATISFIED THE ANCHOR HAD GOOD HOLD, MADE HIS WAY AFT AND SAT DOWN AMONGST US. WE EJCHANGED A FEW WORDS LAXILY. AFTERWARDS THERE WAS SILENCE ON BOARD THE YACHT. FOR SOME REASON OR OTHER WE DID NOT BEGIN THAT GAME OF DOMINOES. WE FELT MEDITATIVE, AND FIT FOR NOTHING BUT PLACID STARING. THE DAY WAS ENDING IN A SERENITY OF STILL AND EJQUISITE BRILLIANCE. THE WATER SHONE PACIFICALLY; THE SKY, WITHOUT A SPECK, WAS A BENIGN IMMENSITY OF UNSTAINED LIGHT; THE VERY MIST ON THE ESSEJ MARSH WAS LIKE A GAUXY AND RADIANT FABRIC, HUNG FROM THE WOODED RISES INLAND, AND DRAPING THE LOW SHORES IN DIAPHANOUS FOLDS. ONLY THE GLOOM TO THE WEST, BROODING OVER THE UPPER REACHES, BECAME MORE SOMBRE EVERY MINUTE, AS IF ANGERED BY THE APPROACH OF THE SUN.

```

la bandera es: FREQUENCY_IS_C_OVER_LAMBDA_OGFMAUNRAF
## Notas