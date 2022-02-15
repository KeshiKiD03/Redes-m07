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

* 👹<span style="color:gold">**2^n - 2**</span>👹 >= X Subredes

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

----------------------------------------------------------------------------------------------

0. AÑADIR LAS TABLAS Y LAS FÓRMULAS.

| **2^7** | **2^6** | **2^5** | **2^4** | **2^3** | **2^2** | **2^1** | **2^0** | 
| --- | --- | --- |---- | --- | --- | --- | --- |
| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

| **/24** | **/25** | **/26** | **/27** | **/28** | **/29** | **/30** | **/31** | **/32** | 
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| 0 | .128 | .192 | .224 | .240 | .248 | .252 | .254 | .255 |

* 👹<span style="color:gold">**2^n - 2**</span>👹 >= X Subredes (Para Subnetting Fijo)

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
| X2 | 700 | 1022 | 192.168.224.0 | 192.168.225.0 |  | | | | |
| X1 | 200 | | | | | | | | |
| X3 | 50 | | | | | | | | |
| WAN 1 | 2 | | | | | | | | |
| WAN 2 | 2 | | | | | | | | |

❤️‍🔥<span style="color:gold">**NOTA 1: SHORTCUT / HACK: SUMA DIRECCIÓN DE RED + HOSTS ENCONTRADOS</span> <span style="color:green">= ÚLTIMA IP DISPONIBLE --> OBTENEMOS LA BROADCAST Y LA SIGUIENTE RED**</span>❤️‍🔥

❤️‍🔥<span style="color:gold">**NOTA 2: USAR LA CONSTANTE Y CALCULAR EL PRÓXIMO SALTO Y OBTENEMOS</span><span style="color:green"> --> LA SIGUIENTE RED + BROADCAST Y ÚLTIMA RED DISPONIBLE**</span>❤️‍🔥

----------------------------------------------------------------------------------------------

0. AÑADIR LAS TABLAS Y LAS FÓRMULAS.

| **2^7** | **2^6** | **2^5** | **2^4** | **2^3** | **2^2** | **2^1** | **2^0** | 
| --- | --- | --- |---- | --- | --- | --- | --- |
| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

| **/24** | **/25** | **/26** | **/27** | **/28** | **/29** | **/30** | **/31** | **/32** | 
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| 0 | .128 | .192 | .224 | .240 | .248 | .252 | .254 | .255 |

* 👹<span style="color:gold">**2^n - 2**</span>👹 >= X Subredes (Para Subnetting Fijo)

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

<!-- 4. Saber el próximo SALTO DE RED con la CONSTANTE 256 o SUMAR HOSTS ENCONTRADOS + DIRECCIÓN DE RED.

    * El próximo **SALTO** es **256 - 128 = 128**. -->

5. Rellenar la TABLA y repetir el **PROCESO**.

#### ☣️ EJERCICIO PRÁCTICO VLSM 3 ☣️


1. Partiendo de la **RED 172.16.224.0/19**, necesitamos **CREAR** las siguientes **subredes**.

    * X1: 3040 hosts

    * X2: 6070 hosts

    * X3: 550 hosts

    * WAN 1: 2 hosts

    * WAN 2: 2 hosts

| **N de RED** | **Número de HOSTS SOLICITADOS** | **Número de HOSTS ENCONTRADOS** | **Dirección de RED (AX)** | **Máscara (/X)** | **Máscara en Decimal Punteado** | **Primera IP Utilizable** | **Última IP Utilizable** | **Broadcast** | **Broadcast en BINARIO** | 
| --- | --- | --- |--- | --- | --- | --- | --- | --- | --- |
| | | | | | | | | | |

----------------------------------------------------------------------------------------------

1. Ordenar de MAYOR a MENOR los HOSTS.

2. Empezar por el MAYOR y determinar LOS BITS de HOST y los BITS restantes para RED.

3. Aplicar la FÓRMULA para saber la NUEVA MÁSCARA DE RED.

4. Saber el próximo SALTO DE RED con la CONSTANTE 256.

5. Rellenar la TABLA.


#### ☣️ EJERCICIO PRÁCTICO VLSM 4 ☣️




#### ☣️ EJERCICIO PRÁCTICO VLSM 5 ☣️

#### ☣️ SUBNETTING (MÁSCARA FIJA) ☣️

#### ☣️ EJERCICIO PRÁCTICO SUBNETTING 1  ☣️

#### ☣️ EJERCICIO PRÁCTICO SUBNETTING 2  ☣️

#### ☣️ EJERCICIO PRÁCTICO SUBNETTING 3  ☣️

#### ☣️ EJERCICIO PRÁCTICO SUBNETTING 4  ☣️

#### ☣️ EJERCICIO PRÁCTICO SUBNETTING 5  ☣️
