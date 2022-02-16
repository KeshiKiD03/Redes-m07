# M07 - Planificació i administració de xarxes
## Escola Del Treball
### 2HISX 2021-2022
### Aaron Andal

https://geekland.eu/aprender-markdown-en-minutos/ 

#### EMOJIS CHEATSHEET

👹 🤬  😍 🥰  🥺  👾  👽  👍  🔥  🌈 ☀️  🌤 ☄️  🚧 ☢️ 

☣️ ⛔️  💮  🆚 ❗️ ❗️ ❗️ ❓ ❓  💯 ❤️‍🔥  💛  🧡  💟 

#### TABLA ELEVACIONES Y MÁSCARA

| **2^7** | **2^6** | **2^5** | **2^4** | **2^3** | **2^2** | **2^1** | **2^0** | 
| --- | --- | --- |---- | --- | --- | --- | --- |
| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

| **/24** | **/25** | **/26** | **/27** | **/28** | **/29** | **/30** | **/31** | **/32** | 
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| 0 | .128 | .192 | .224 | .240 | .248 | .252 | .254 | .255 |

#### FÓRMULAS y TRUCOS

* 👹<span style="color:gold">**2^n**</span>👹 >= X Subredes

* 👹<span style="color:gold">**2^m - 2**</span>👹 >= X Hosts

* 👾<span style="color:gold">**CONSTANTE**:</span>👾 256 (Se resta con la máscara, para saber el próximo SALTO = Próxima RED)

* 👽<span style="color:gold">**BROADCAST**</span>👽 --> Siempre será UNO antes que la próxima **DIRECCIÓN DE RED**.

* 💯<span style="color:gold">**PRIMERA IP ASIGNABLE**</span>💯 --> Siempre es la primera IP asignable a NUESTRA HOST. (Suele ser para el ROUTER, etc..)

* 🧡<span style="color:gold">**ÚLTIMA IP ASIGNABLE**</span>🧡 --> Siguiendo la fórmula 2^n-2, 2 **HOSTS** antes de la **PRÓXIMA RED**

☢️<span style="color:gold">**NOTA: Se reservan 2 HOSTS para BROADCAST y RED**</span>☢️

#### ☣️ VLSM (CheatSheeet) ☣️

* VLSM: <span style="color:gold">**Variable Length Subnet Mask**</span> --> *Máscara de Red de Longitud Varaiable*.

* Las máscaras de red cambian por subred.

* Se aprovecha el mayor número de **HOST** en cada **SUBRED**.

* Evita el agotamiento de direcciones ipv4.

* Se divide una `red o subred` en redes más pequeñas, aprovechando la CANTIDAD DE HOST en cada SUBRED indicada.

#### ☣️ VLSM (Procedimiento) ☣️

* Se usa la <span style="color:gold">**FORMULA** = 👹**2^m - 2**</span>👹 >= X Hosts

* 👾<span style="color:gold">**CONSTANTE**</span>:👾 256 (Se resta con la máscara, para saber el próximo SALTO = Próxima RED)

* La <span style="color:gold">**MÁSCARA DE RED**</span> cambia en cada SUBRED.

* Para obtener el LA 💮<span style="color:gold">**PRÓXIMA SUBRED**</span>💮 hay que 👍**SUMAR el RESULTADO**👍 de la nueva **MÁSCARA** con la **DIRECCIÓN ACTUAL DE RED**.

* 👽<span style="color:gold">**BROADCAST**</span>👽 es SIEMPRE 1 anterior a la 💮<span style="color:gold">**PRÓXIMA SUBRED**</span>💮

--------------------------------------------------------------------------------------

1. Determinar la **MÁSCARA** de la **RED ACTUAL**.

    * Nos fijamos en la <span style="color:gold">**MÁSCARA ORIGINAL**</span>.

        * Ejemplo: Si tenemos /24:

            * **24 BITS** serán de **RED** y **8 BITS** de **HOST**.

|  <span style="color:gold">**/24**</span> |
| :-------------: |
|  <span style="color:gold">**11111111.11111111.11111111.**</span>00000000 |

2. Aplicar la  <span style="color:gold">**FÓRMULA**: **2^m - 2 >= X Hosts**</span>

    * Ejemplo: 2^7 -2 = 126 = 126 --> 126 >= **120 Hosts**

3. Obtener <span style="color:gold">**nueva máscara de RED**</span>, partiendo de la <span style="color:gold">**MÁSCARA ORIGINAL SIEMPRE**</span>.

    * Ejemplo: Tenemos **120 Host** de esta **SUBRED**.

        * Hemos calculado previamente el resultado de **2^7-2 = 126 >= 120**

        * La **nueva máscara** se calcula a partir de la **MÁSCARA ORIGINAL** y **RELLENANDO LOS BITS DE HOST** y el que sobre será de **RED**.

        * Entonces la nueva máscara será **/25**, ya que hemos encendido **1 BIT** de la parte de **HOST** a **RED**, partiendo de la **MÁSCARA ORIGINAL /24**.

|  <span style="color:gold">**/25**</span> |
| :-------------: |
|  <span style="color:gold">**11111111.11111111.11111111.1**</span>0000000 |

* Decimal punteado:

    * Sabiendo que hemos encendido **1 BIT** para la nueva **MÁSCARA**, observamos la tabla y vemos que equivale a **.128**. Quedaría como:

|  <span style="color:gold">**255.255.255.128**</span> |
| :-------------: |

4. Saber el próximo <span style="color:gold">**SALTO de RED**</span>:

    * Se usa la <span style="color:gold">**CONSTANTE (256)**</span> se RESTA el <span style="color:gold">**ÚLTIMO**</span> número generado por la <span style="color:gold">**NUEVA MÁSCARA DE RED**</span>.
    

#### ☣️ LA TABLA (Procedimiento) ☣️

| **N de RED** | **Número de HOSTS SOLICITADOS** | **Número de HOSTS ENCONTRADOS** | **Dirección de RED (AX)** | **Máscara (/X)** | **Máscara en Decimal Punteado** | **Primera IP Utilizable** | **Última IP Utilizable** | **Broadcast** | **Broadcast en BINARIO** | 
| --- | --- | --- |--- | --- | --- | --- | --- | --- | --- |


❤️‍🔥<span style="color:gold">**NOTA: CIDR:**</span>❤️‍🔥

❤️‍🔥<span style="color:gold">**NOTA: En BINARIO el BROADCAST siempre HAY QUE FIJARSE EN LA MÁSCARA ACTUAL, tendrá el BIT de RED encendido, se le pone a 0 Y EL RESTO A 1**</span>❤️‍🔥

#### ☣️ EJERCICIO PRÁCTICO VLSM 1 ☣️

1. Partiendo de la **RED 192.168.40.0/24**, necesitamos **CREAR** las siguientes **subredes**.

    * Tecnología: 10 hosts

    * Administració: 40 hosts

    * Vendes: 100 hosts

    * Compra: 22 hosts

    * Recursos humanos: 5 hosts

* ☄️<span style="color:gold">**192.168.40.0/24**</span>☄️

* ☄️<span style="color:gold">**11111111.11111111.11111111.00000000**</span>☄️

| **N de RED** | **Número de HOSTS SOLICITADOS** | **Número de HOSTS ENCONTRADOS** | **Dirección de RED (AX)** | **Máscara CIDR (/X)** | **Máscara en BINARIO** | **Máscara en Decimal Punteado** | **Primera IP Utilizable** | **Última IP Utilizable** | **Broadcast** | **Broadcast en BINARIO** | 
| --- | --- | --- |--- | --- | --- | --- | --- | --- | --- | --- |
| Vendes | 100 | **126** | 192.168.40.**0** | **/25** | 11111111.11111111.11111111.**1**0000000 | 255.255.255.**128** | 192.168.40.**1** | 192.168.40.**126**  | 192.168.40.**127** | 11000000.10101000.00101000.0**1111111** |
| Administracio | 40 | **62** | 192.168.40.**128** | **/26** | 11111111.11111111.11111111.**11**000000 | 255.255.255.**192** | 192.168.40.**129** | 192.168.40.**190** | 192.168.40.**191** | 11000000.10101000.00101000.10**111111** |
| Compra | 22 | **30** | 192.168.40.**192** | **/27** | 11111111.11111111.11111111.**111**00000 | 255.255.255.**224** | 192.168.40.**193** | 192.168.40.**222** | 192.168.40.**223** | 11000000.10101000.00101000.110**11111** |
| Tecnologia | 10 | **14** | 192.168.40.**224** | **/28** | 11111111.11111111.11111111.**1111**0000 | 255.255.255.**240** | 192.168.40.**225** | 192.168.40.**238** | 192.168.40.**239** |  11000000.10101000.00101000.1110**1111** |
| Recursos Humanos | 5 | **6** | 192.168.40.**240** | **/29** | 11111111.11111111.11111111.**11111**000  | 255.255.255.**248** | 192.168.40.**241** | 192.168.40.**246** | 192.168.40.**247** |  11000000.10101000.00101000.11110**111** |

❤️‍🔥<span style="color:gold">**NOTA 1: SHORTCUT / HACK: SUMA DIRECCIÓN DE RED + HOSTS ENCONTRADOS</span> <span style="color:green">= ÚLTIMA IP DISPONIBLE --> OBTENEMOS LA BROADCAST Y LA SIGUIENTE RED**</span>❤️‍🔥

❤️‍🔥<span style="color:gold">**NOTA 2: USAR LA CONSTANTE Y CALCULAR EL PRÓXIMO SALTO Y OBTENEMOS</span><span style="color:green"> --> LA SIGUIENTE RED + BROADCAST Y ÚLTIMA RED DISPONIBLE**</span>❤️‍🔥


❤️‍🔥<span style="color:gold">**NOTA 3: SHORTCUT / HACK: PARA ENCONTRAR LA BROADCAST =  HOSTS ENCONTRADOS + PRIMERA IP DISPONIBLE</span> <span style="color:green">SALE BROADBAST**</span>❤️‍🔥

----------------------------------------------------------------------------------------------

0. AÑADIR LAS TABLAS Y LAS FÓRMULAS.

| **2^7** | **2^6** | **2^5** | **2^4** | **2^3** | **2^2** | **2^1** | **2^0** | 
| --- | --- | --- |---- | --- | --- | --- | --- |
| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

| **/24** | **/25** | **/26** | **/27** | **/28** | **/29** | **/30** | **/31** | **/32** | 
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| 0 | .128 | .192 | .224 | .240 | .248 | .252 | .254 | .255 |

* 👹<span style="color:gold">**2^n**</span>👹 >= X Subredes (Para Subnetting Fijo)

* 👹<span style="color:gold">**2^m - 2**</span>👹 >= X Hosts (Para VLSM primero)

1. Ordenar de MAYOR a MENOR los HOSTS.

    * Vendes: 100 hosts

    * Administració: 40 hosts

    * Compra: 22 hosts    

    * Tecnología: 10 hosts

    * Recursos humanos: 5 hosts

2. Empezar por el MAYOR y determinar LOS BITS de HOST y los BITS restantes para RED.

    * **FORMULA --> 2^m - 2 >= 100**

        * La que se acerca es **2^7 = 128**.

            * Quedaría: **2^7 - 2  = 126**.

3. Aplicar la FÓRMULA para saber la NUEVA MÁSCARA DE RED.

    * Tenemos **7 BITS** para la parte de **HOST**.

    * Por lo tanto tenemos **1 BIT** para la parte de **RED**.

    *   La máscara sería **/25**

4. Saber el próximo SALTO DE RED con la CONSTANTE 256 o SUMAR HOSTS ENCONTRADOS + DIRECCIÓN DE RED.

    * El próximo **SALTO** es **256 - 128 = 128**.

5. Rellenar la TABLA y repetir el **PROCESO**.



#### ☣️ EJERCICIO PRÁCTICO VLSM 2 ☣️

**Es una clase B**

1. Partiendo de la **RED 192.168.224.0/20**, necesitamos **CREAR** las siguientes **subredes**.

    * X1: 200 hosts

    * X2: 700 hosts

    * X3: 50 hosts

    * WAN 1: 2 hosts

    * WAN 2: 2 hosts


* ☄️<span style="color:gold">**192.168.224.0/20**</span>☄️

* ☄️<span style="color:gold">**11111111.11111111.11110000.00000000**</span>☄️

| **N de RED** | **Número de HOSTS SOLICITADOS** | **Número de HOSTS ENCONTRADOS** | **Dirección de RED (AX)** | **Máscara CIDR (/X)** | **Máscara en BINARIO** | **Máscara en Decimal Punteado** | **Primera IP Utilizable** | **Última IP Utilizable** | **Broadcast** |
| --- | --- | --- |--- | --- | --- | --- | --- | --- | --- |
| X2 | 700 | 1022 | 192.168.224.0 | /22 | 11111111.11111111.11111100.00000000 | 255.255.252.0 | 192.168.224.1 | 192.168.247.254 | 192.168.247.255 |
| X1 | 200 | 510 | 192.168.228.0 | /23 | 11111111.11111111.11111110.00000000 | 255.255.254.0 | 192.168.228.1 | 192.168.228.254 | 192.168.228.255 |
| X3 | 50 | 62 | 192.168.229.0 | /26 | 11111111.11111111.11111111.11000000 | 255.255.255.192 | 192.168.229.1 | 192.168.229.62 | 192.168.229.63 |
| WAN 1 | 2 | 2 | 192.168.229.64 | /30 | 11111111.11111111.11111111.11111100 | 255.255.255.252 | 192.168.229.65 | 192.168.229.67 |
| WAN 2 | 2 | 2 | 192.168.229.68 | /30 | 11111111.11111111.11111111.11111100 | 255.255.255.252 | 192.168.229.69 | 192.168.229.71 |

❤️‍🔥<span style="color:gold">**NOTA IMPORTANTE: Al ser una CLASE B hay que PRIORIZAR LA NOTA 2 - PARA LOS SALTOS</span> <span style="color:green">= ÚLTIMA IP DISPONIBLE --> OBTENEMOS LA BROADCAST Y LA SIGUIENTE RED**</span>❤️‍🔥

❤️‍🔥<span style="color:gold">**NOTA 1: SHORTCUT / HACK: SUMA DIRECCIÓN DE RED + HOSTS ENCONTRADOS</span> <span style="color:green">= ÚLTIMA IP DISPONIBLE --> OBTENEMOS LA BROADCAST Y LA SIGUIENTE RED**</span>❤️‍🔥

❤️‍🔥<span style="color:gold">**NOTA 2: USAR LA CONSTANTE Y CALCULAR EL PRÓXIMO SALTO Y OBTENEMOS</span><span style="color:green"> --> LA SIGUIENTE RED + BROADCAST Y ÚLTIMA RED DISPONIBLE**</span>❤️‍🔥

❤️‍🔥<span style="color:gold">**NOTA 3: SHORTCUT / HACK: PARA ENCONTRAR LA BROADCAST =  HOSTS ENCONTRADOS + PRIMERA IP DISPONIBLE</span> <span style="color:green">SALE BROADBAST**</span>❤️‍🔥


----------------------------------------------------------------------------------------------

0. AÑADIR LAS TABLAS Y LAS FÓRMULAS.

| **2^7** | **2^6** | **2^5** | **2^4** | **2^3** | **2^2** | **2^1** | **2^0** | 
| --- | --- | --- |---- | --- | --- | --- | --- |
| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

| **/24** | **/25** | **/26** | **/27** | **/28** | **/29** | **/30** | **/31** | **/32** | 
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| 0 | .128 | .192 | .224 | .240 | .248 | .252 | .254 | .255 |

* 👹<span style="color:gold">**2^n**</span>👹 >= X Subredes (Para Subnetting Fijo)

* 👹<span style="color:gold">**2^m - 2**</span>👹 >= X Hosts (Para VLSM primero)

1. Ordenar de MAYOR a MENOR los HOSTS.

    * X2: 700 hosts

    * X1: 200 hosts

    * X3: 50 hosts    

    * WAN 1: 2 hosts

    * WAN 2: 2 hosts

2. Empezar por el MAYOR y determinar LOS BITS de HOST y los BITS restantes para RED.

    * **FORMULA --> 2^m - 2 >= 700**

        * La que se acerca es **2^10 = 1024**.

            * Quedaría: **2^10 - 2  = 1022**.

3. Aplicar la FÓRMULA para saber la NUEVA MÁSCARA DE RED.

    * Tenemos **10 BITS** para la parte de **HOST**.

    * Por lo tanto tenemos **2 BIT** para la parte de **RED**.

    *   La máscara sería **/22**

4. Saber el próximo SALTO DE RED con la CONSTANTE 256 o SUMAR HOSTS ENCONTRADOS + DIRECCIÓN DE RED.

    * El próximo **SALTO** es **256 - 252 = 4**. --> El próximo SALTO empezará en **.248.0**.


5. Rellenar la TABLA y repetir el **PROCESO**.


#### ☣️ SUBNETTING (MÁSCARA FIJA) ☣️

* Máscara FIJA.


0. AÑADIR LAS TABLAS Y LAS FÓRMULAS.

| **2^7** | **2^6** | **2^5** | **2^4** | **2^3** | **2^2** | **2^1** | **2^0** | 
| --- | --- | --- |---- | --- | --- | --- | --- |
| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

| **/24** | **/25** | **/26** | **/27** | **/28** | **/29** | **/30** | **/31** | **/32** | 
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| 0 | .128 | .192 | .224 | .240 | .248 | .252 | .254 | .255 |



**Ejemplo: 192.168.1.0 / 24**

**255.255.255.0**

**11111111.11111111.11111111.00000000**

1. Nos dan el número de SUBREDES.

    * Tenemos que hacer 4 subredes partiendo de una IP.

    * **N DE HOST POR SUBRED ?**

2. Usar la FÓRMULA PARA SABER SI ES MAYOR O IGUAL a LA SUBRED ESTIPULADA.

    * **2^n - 2** >= 4 --> 2^3 - 2 = 6 --> 6 es mayor que 4

        * Se procederán a encander **X BITS** para RED --> 2^**3** - 2

3. Con el resultado, podemos hacer **6 SUBREDES**

4. En SUBNETTING FIJO, se **ENCIENDEN** **3 BITS** en la **PARTE de RED**.

    * 11111111.11111111.11111111.**111**00000.

5. Obtenemos una nueva máscara **/27**.

6. La nueva dirección de RED con la **MÁSCARA CAMBIADA** es **192.168.1.0/27**.

7. Cada **SALTO es 2^5**.

    * Se calcula con una RESTA de 256 - **(La nueva máscara)**.

8. Procedemos a **CREAR CADA SUBRED** con **2^5 - 2 HOSTS** por SUBRED. 

9. **REPETIR EL PROCESO**.



#### ☣️ SUBNETTING (MÁSCARA FIJA) / RESUMEN ☣️

1. Determinar la nueva máscara.

    *** Necesitamos 4 subredes --> 2^3 - 2 = 6 SUBREDES.**

2. Tomamos 3 BITS de red para la nueva máscara de nuestra SUBRED. Tendrá la misma máscara.

    11111111.11111111.11111111.**111**00000

3. Calculamos el Número de HOSTS por SUBRED.

    * **2^m - 2 = H --> 2^5 - 2 = 30 HOST x SUBRED.**

4. Determinar los SALTOS de RED

    **256 - 224 (Máscara Nueva) = 32 --> Tendrá 32 DISPOSITIVOS por SUBRED**

5. Rellenar la TABLA.

| **SUBRED** | **PRIMERA IP ASIGNABLE** | **ÚLTIMA IP ASIGNABLE** | **BROADCAST** |
| --- | --- | --- |--- |
| | | | |



#### ☣️ EJERCICIO PRÁCTICO SUBNETTING 1  ☣️

* Donada la xarxa 192.168.0.0/24, volem crear 3 subxarxes que tinguin 33 dispositius cadascuna d'elles.

| **SUBRED** | **PRIMERA IP ASIGNABLE** | **ÚLTIMA IP ASIGNABLE** | **BROADCAST** |
| --- | --- | --- |--- |
| 192.168.0.0/26 | 192.168.0.1/26 | 192.168.0.62 | 192.168.0.63 |
| 192.168.0.64/26 | 192.168.0.65/26 | 192.168.0.126 | 192.168.0.127 |
| 192.168.0.128/26 | 192.168.0.129/26 | 192.168.0.190 | 192.168.0.191 |


1. Formula SUBREDES.

    * 2^n - 2 >= 3

        * 2^3 = 8 --> 8 es MAYOR que 3

2. En este **CASO** nos pide 33 DISPOSITIVOS, engaña un poco. Por lo cuál empezaremos por el **HOST**.

    * 2^m - 2 >= 33 

        * 2^5 - 2 = 30 --> 30 NO LLEGA A 33. POR LO CUAL NO NOS SIRVE LA MÁSCARA /27

    
##### SOLUCIÓN:

1. Empezar por la fórmula de HOST.

    * 2^6 - 2 = 62 host x subred.

        * 62 es MAYOR o IGUAL que 33.

2. Por lo tanto de la MÁSCARA /24, cogeremos 6 bits para HOST y el RESTO para RED.

    * 11111111.11111111.11111111.11000000 --> **/26**

3. La nueva máscara es **/26**.

4. Por lo tanto:

    * /26 --> 2^6 - 2 hosts x subred.

    * 4 subredes.

* **NOTA: FIJARSE EN SI HAY HOSTS DE POR MEDIO**

5. Calculamos el próximo SALTO.

    * 256 - 192 = 64

6. Rellenamos la TABLA


a) Quina màscara de xarxa haurem d'utilitzar?

`La màscara que hauríem d’utilitzar es la /26 ja que segons
la formula (2^n* (*n = numero de bits que necessiten per a
la xarxa)), el mínim de 3 xarxes es 2^2 = 4 xarxes, però per
poder limitar-ho a 33 xarxes, hauríem d’utilitzar la /26. Amb
aquesta màscara fixa per a la subxarxa tenim:`

    a. 2^6-2 = Numero de hosts disponibles per a cada subxarxa = 62

b) Quines seran les adreces de cada una de les xarxes?

`a. 192.168.0.0/26`

`b. 192.168.0.64/26`

`c. 192.168.0.128/26`


#### ☣️ EJERCICIO PRÁCTICO SUBNETTING 2  ☣️

Donada la xarxa 10.192.172.0/22, volem fer 5 subxarxes.

a. Quants bits necessites per ampliar la Màscara de Xarxa (MX) per tal de poder fer aquestes 5 subxarxes?

`i. Necessitem com a mínim 2^3 = 8 subxarxes per poder dur a terme 5 subxarxes.`

`ii. Tenim la màscara /22 però per a fer la nova subxarxa /25.`


b. Dóna la nova MX, tant en format decimal com en binari.

    i. Binari IP: 00001010.11000000.10101100.00000000

    ii. Binari MX: 11111111.11111111.11111100.00000000

    iii. Decimal: 255.255.252.0

    iv. Binari NOU MX:
    11111111.11111111.11111111.10000000

    v. Decimal: 255.255.252.128

    vi. Subxarxa1: 00001010.11000000.10101100.00000000

    vii. Subxarxa2: 00001010.11000000.10101100.10000000

    viii. Subxarxa3: 00001010.11000000.10101101.00000000

    ix. Subxarxa4: 00001010.11000000.10101101.10000000

    x. Subxarxa5: 00001010.11000000.10101110.00000000

    xi. Subxarxa6: 00001010.11000000.10101110.10000000

    xii. Subxarxa7: 00001010.11000000.10101111.00000000

    xiii. Subxarxa8: 00001010.11000000.10101111.10000000



c. Per cada subxarxa nova que has de crear, indica

     L'adreça de xarxa, en format decimal i en binari
     L'adreça de broadcast extern, en format decimal i en binari
     El rang d'IPs per a dispositius

```    
Adreça de Xarxa

Adreça de Broadcast Extern

Rang IPs per a Dispositius

Xarxa 1

10.192.172.0/25
10.192.172.127/25 10.192.172.1 -
10.192.172.126/25

Xarxa 2

10.192.172.128/25
10.192.172.255/25 10.192.172.129 -
10.192.172.254/25

Xarxa 3

10.192.173.0/25
10.192.173.127/25 10.192.173.1 -
10.192.173.126/25

Xarxa 4

10.192.173.128/25
10.192.173.255/25 10.192.172.129 -
10.192.172.254/25

Xarxa 5

10.192.174.0/25
10.192.174.127/25 10.192.174.1 -
10.192.174.126/25
```

d. Tenint en compte el número de bits que has indicat en l'apartat a),
quantes subxarxes podríem fer, realment? Dóna'n la fórmula que
s'utilitza per calcular aquesta dada

`Segons la fórmula (2^n). Podem fer 8 subxarxes amb la
nova mascara de xarxa.`

e. Segons la MX que has calculat als apartats a) i b), quants
dispositius pot tenir cada subxarxa? Dóna'n la fórmula que s'utilitza per calcular aquesta dada.
`Cada subxarxa pot tenir 2^7-2 dispositius per connectar,
reservant-se 2 per xarxa i broadcast.`


##### OTRO MÁS

Donada la xarxa 192.0.2.0/24

a. Quants dispositius pot adreçar?
`1. Els dispositius que adreçarem a la xarxa es 254 hosts = 2^8-2.`

b. Quantes subxarxes podrem fer, com a màxim, si volem que
cadascuna d'elles tingui 45 dispositius?

`1. Necesitem que 2^n-2 >= 45 dispositius. Llavors obtenim que els bits destinats a hosts son 6 per als dispositus connectats en cada subxarxa = 2^6-2.`

`2. En quant a la subxarxa, partim de /24 i necessitem 45 dispositus per xarxa, llavors obtenim la nova CIDR /26 com a nova MX de les subxarxes.`

`3. Podem crear 2^2 subxarxes noves. Segons la formula 2^n. Haurem d’agafar 2 bits més per a la nova màscara de subxarxa.`

c. Calcula la nova MX en decimal i binari

`1. Binari IP: 11000000.00000000.00000010.00000000`

`2. Binari MX: 11111111.11111111.11111111.00000000`

`3. Decimal: 255.255.255.0`

`4. Binari NOU MX:`
`11111111.11111111.1111111.11000000`

`5. Decimal: 255.255.255.192`


`6. Subxarxa1: 11000000.00000000.00000010.00000000`

`7. Subxarxa2: 11000000.00000000.00000010.01000000`

`8. Subxarxa3: 11000000.00000000.00000010.10000000`

`9. Subxarxa4: 11000000.00000000.00000010.11000000`


Calcula l'adreça de xarxa i de broadcast extern de les subxarxes

```
Adreça de Xarxa
Adreça de Broadcast Extern
Rang IPs per a Dispositius

Xarxa 1
192.0.2.0/26 
192.0.2.63/26 
192.0.2.1/26 -
192.0.2.62/26

Xarxa 2
192.0.2.64/26
192.0.2.127/26
192.0.2.65/26 -
192.0.2.126/26

Xarxa 3
192.0.2.128/26
192.0.2.191/26 
192.0.2.129/26 -
192.0.2.190/26

Xarxa 4
192.0.2.192/26
192.0.2.253/26 
192.0.2.193/26 -
192.0.2.252/26
```
#### ☣️ ÚLTIMA, CLASE A  ☣️

* Donada l'adreça 11.27.0.0/16

a) Tenint en compte la IP 11.27.0.0, a quina classe pertany l'adreça?

`Pertany d’una classe A, llavors aquesta es una subxarxa amb una mascara nova /16.`

`La clase A es defineix desde 0.0.0.0 a 127.255.255.255.`

`Pertany a la Clase B nova segons (128.0.0.0 – 191.255.255.255)`

b) Tenint en compte la màscara de xarxa d'aquesta classe, quantes subxarxes hem fet amb la MX=/16?

`Hem fet 2^16 subxaxes diferents.`

c) Fent servir l'adreça de xarxa 11.27.0.0/16 com la nostra AXmare, calculeu la MX que necessitem per poder fer tantes subxarxes com sigui possible de 512 dispositius.

`**Necesitem que 2^n-2 >= 512 dispositius.**`

`Provem amb 2^9-2 = 510, no arriba als 512 llavors haurem d’agafar 1 bit més per host.`

`Llavors obtenim que els bits destinats a hosts son (Si partim per /16) 10 per als dispositus connectats en cada subxarxa = 2^10-2.`

`MX: 11111111.11111111.00000000.0000000 /16`

`Nova MX: 11111111.11111111.11111100.0000000 /22`

`Hem d’agafar 2^6 bits de xarxa més per poder dur a terme els 512 dispositius per subxarxa.`

`Per lo tant ens queda que 2^10-2 = 1022 > 512. Podem fer 2^6 noves subxarxes.`
