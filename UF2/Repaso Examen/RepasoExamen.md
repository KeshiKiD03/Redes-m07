# Repaso redes

# Ruta resumen se hace cuando tenemos una serie de dispositivos que están conectadas al mismo Router. Para hacer la ruta resumen:

1. El router R1 pot accedir a través de la seva interfície s0/0/0 a les següents 4 xarxes remotes:

185.14.25.0/24
185.14.26.0/24
185.14.27.0/24
185.14.28.0/24

Calcula'n si és possible la Ruta Resum.

1. Traducir sólo el 3er byte.

1   1   1  1 1 1 1 1
 
128 64 32 16 8 4 2 1

0 0 0 1 1 0 0 1 = 25

0 0 0 1 1 0 1 0 = 26

0 0 0 1 1 0 1 1 = 27

0 0 0 1 1 1 0 0 = 28

Ruta Resumen

0 0 0 1 1 0 0 0 = 24

Le restas al CIDR inicial 24 - 3 = /21

los 3 ceros se restan al cidr inicial.

__Este ejemplo es de un lado__.

----

2. El router R1 pot accedir a les següents 4 xarxes remotes:

185.14.25.0/24, a través de la seva interfície s0/0/0
185.14.26.0/24, a través de la seva interfície s0/0/0

185.14.27.0/24, a través de la seva interfície s0/0/1
185.14.28.0/24, a través de la seva interfície s0/0/1

s0/0/0

1   1   1  1 1 1 1 1
 
128 64 32 16 8 4 2 1


0 0 0 1 1 __0__ 0 1 = 25

0 0 0 1 1 __0__ 1 0 = 26


Ruta resum: x.x.24.0/22


s0/0/1

1   1   1  1 1 1 1 1
 
128 64 32 16 8 4 2 1


0 0 0 1 __1__ 0 1 1 = 27

0 0 0 1 __1__ 1 0 0 = 28

Ruta resum: x.x.24.0/21



3. El router R1 pot accedir a les següents xarxes remotes:

185.14.24.0/24, a través de la seva interfície s0/0/0
185.14.25.0/24, a través de la seva interfície s0/0/0

185.14.26.0/24, a través de la seva interfície s0/0/1
185.14.27.0/24, a través de la seva interfície s0/0/1

Calcula'n si és possible la Ruta Resum.


1   1   1  1 1 1 1 1
 
128 64 32 16 8 4 2 1


s0/0/0

1   1   1  1 1 1 1 1
 
128 64 32 16 8 4 2 1


0 0 0 1 1 0 0 0 = 24

0 0 0 1 1 0 0 1 = 25


Ruta resum: x.x.24.0/23






s0/0/1

1   1   1  1 1 1 1 1
 
128 64 32 16 8 4 2 1


0 0 0 1 1 0 1 0 = 26

0 0 0 1 1 0 1 1 = 27

Ruta resum: x.x.26.0/23

Si es pot

Lo que no es pot es la mateixa ip i la mateixa màscara.


_________________________________________


 4. Donada la Ruta Resum 102.17.15.48/28, indica quina de les xarxes remotes no esta inclosa en el resum:

102.17.15.48/30
102.17.15.52/30
102.17.15.56/30
102.17.15.60/30
102.17.15.64/30


1. Passar-ho a binari

veure lo que està en comú.


102.17.15.48/30
 X  X  X 00110000
102.17.15.52/30
X  X  X  00110100
102.17.15.56/30
X  X  X  00111000
102.17.15.60/30
X  X  X  00111100
102.17.15.64/30
X  X  X  01000000

la x.x.x.64 no està inclou en el resum.



-----

CLASSLESS

CLASSFUL = Adaptarà.