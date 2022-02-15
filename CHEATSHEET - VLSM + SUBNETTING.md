# M07 - Planificació i administració de xarxes
## Escola Del Treball
### 2HISX 2021-2022
### Aaron Andal

#### EMOJIS CHEATSHEET

👹 🤬  😍 🥰  🥺  👾  👽  👍  🔥  🌈 ☀️  🌤 ☄️  🚧 ☢️ 

☣️ ⛔️  💮  🆚 ❗️ ❗️ ❗️ ❓ ❓  💯 ❤️‍🔥  💛  🧡  💟 

#### TABLA ELEVACIONES Y MÁSCARA

| **2^7** | **2^6** | **2^5** | **2^4** | **2^3** | **2^2** | **2^1** | **2^0** | 
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

| **/24** | **/25** | **/26** | **/27** | **/28** | **/29** | **/30** | **/31** | **/32** | 
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| 0 | .128 | .192 | .224 | .240 | .248 | .252 | .254 | .255 |

#### FÓRMULAS y TRUCOS

* 👹**2^n - 2**👹 >= X Subredes

* 👹**2^m - 2**👹 >= X Hosts

* 👾**CONSTANTE**:👾 256 (Se resta con la máscara, para saber el próximo SALTO = Próxima RED)

* 👽**BROADCAST**👽 --> Siempre será UNO antes que la próxima **DIRECCIÓN DE RED**.

* 💯**PRIMERA IP ASIGNABLE**💯 --> Siempre es la primera IP asignable a NUESTRA HOST. (Suele ser para el ROUTER, etc..)

* 🧡**ÚLTIMA IP ASIGNABLE**🧡 --> Siguiendo la fórmula 2^n-2, 2 **HOSTS** antes de la **PRÓXIMA RED**

☢️**NOTA: Se reservan 2 HOSTS para BROADCAST y RED**☢️

#### ☣️ VLSM (CheatSheeet) ☣️

* VLSM: **Variable Length Subnet Mask** --> *Máscara de Red de Longitud Varaiable*.

* Las máscaras de red cambian por subred.

* Se aprovecha el mayor número de **HOST** en cada **SUBRED**.

* Evita el agotamiento de direcciones ipv4.

* Se divide una red o subred en redes más pequeñas, aprovechando la CANTIDAD DE HOST en cada SUBRED indicada.

#### ☣️ VLSM (Procedimiento) ☣️

* Se usa la **FORMULA** = 👹**2^m - 2**👹 >= X Hosts

* 👾**CONSTANTE**:👾 256 (Se resta con la máscara, para saber el próximo SALTO = Próxima RED)

* La **MÁSCARA DE RED** cambia en cada SUBRED.

* Para obtener el LA 💮**PRÓXIMA SUBRED**💮 hay que 👍**SUMAR el RESULTADO**👍 de la nueva **MÁSCARA** con la **DIRECCIÓN ACTUAL DE RED**.

* 👽**BROADCAST**👽 es SIEMPRE 1 anterior a la 💮**PRÓXIMA SUBRED**💮

--------------------------------------------------------------------------------------

1. Determinar la MÁSCARA de la RED ACTUAL.

