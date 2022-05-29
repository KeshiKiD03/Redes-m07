# Activitat 1.1 El Switch

## a) Què mostra la comanda “arp”? Prova a executar-la i analitza els resultats

La comanda arp fa refèrncia al protocol ARP (Address Resolution Protocol). 

Mostra les IPS de la nostra xarxa, permet cread, editar i mostrar les assignacions MAC a les IPs conegudes.

## b) Fes ara un ping a dos companys de classe. Què ha canviat del resultat de la comanda arp? Per què ha canviat?

Perquè esta en la nostra xarxa i s'afegeixen a la nostra taula ARP.

## c) Fes ara un ping a “google.com”. Ha canviat el resultat de la comanda “arp”? Justifica el resultat.

No ha canviat perquè no perteneix a la nostra xarxa. Ja que ARP treballa amb les MAC dels dispositius de la nostra xarxa. No té validesa a la d'una xarxa externa.

--------------------------

# Dominio de Colisión con HUB

## 4. Seguint amb el Packet Tracer, crea un petit diagrama de xarxa de quatre ordinadors interconnectats per un hub. Assigna als ordinadors les IP que creguis convenients, però que permetin que es puguin fer “PING” entre ells.

b) Fes una simulació on, a l’instant 0, el PC0 es comuniqui amb el PC1 i el PC2 amb el PC3. Digues quin és el resultat de la simulació i el motiu pel que això succeeix.

PC0 se puede comunicar con PC1, pero solo acepta PC0 y rechaza PC2 y PC3.
Se produce un dominio de colisión porque el mensaje se envia en diferentes destinos.

Con un SWITCH se soluciona este problema ya que segmenta el __dominio de colisiones__. Ahora todos se pueden comunicar a la vez.


## 

## 

## 

## 

## 

## 

## 

## 

## 

## 

## 

## 

## 

## 

## 

## 