## Laboratoire 802.11 Sécurité WPA Entreprise.

Auteurs : Crescence Yimnaing && Francine Youndzo

Date : 22 Mai 2019


#### 1. Capture et analyse d’une authentification WPA Entreprise

###### Requête et réponse d’authentification système ouvert

*Requête d'authentification*

![](capture/Capture1.PNG)

Le client envoie une trame d'authentification contenant son adresse à l'access point.

*Réponse d'authentification*

![](capture/Capture2.PNG)

L'acces point accepte la trame.

###### Requête et réponse d’association

*Requête d'associaton*

![](capture/Capture3.PNG)


Elle est utilisée par l'acces point pour sauvegarder les informations propres à chaque client. 


*Réponse d'associaton*

![](capture/Capture4.PNG)

le client est associé à l'acces point.


###### Phase d’initiation.

*Requete d'identité*

![](capture/Capture5.PNG)
L'access point demande au client son identité.

*Réponse d'identité*

![](capture/Capture6.PNG)


*Arrivez-vous à voir l’identité du client ?*
    ```oui on arrive à voir l'identité du client.```
    
###### Selection de la méthode d'authentification :

*   *proposition*

![](capture/Capture7.PNG)

*   *selection*

![](capture/Capture8.PNG)
Le client supporte la méthode d'authentification désirée, comme indiqué sur la capture ci dessous.
![](capture/Capture9.PNG)

###### Phase hello 

* *Version TLS*
![](capture/Capture10.PNG)
    
* *Suites cryptographiques et méthodes de compression proposées par le client et acceptées par l’AP.*

* *==>proposition du client*
![](capture/Capture11.PNG)

* *==> Celles acceptée par le serveur*
![](capture/Capture12.PNG)

![](capture/Capture13.PNG)


* *Nonces*

* *==> envoyé par l'acces point au client*
![](capture/Capture14.PNG)

* *==> envoyé par le client au serveur*
![](capture/Capture15.PNG)

* *Session ID*
![](capture/Capture16.PNG)


###### Phase de transmission de certificats

* *Certificat serveur*
![](capture/Capture17.PNG)


* *transmission des certificats*
![](capture/Capture18.PNG)


* *Change cipher spec(Client ==> serveur)*¨

![](capture/Capture19.PNG)


* *Change cipher spec(serveur ==> Client)*
![](capture/Capture20.PNG)


###### Authentification interne et transmission de la clé WPA (échange chiffré, vu comme « Application data »)
![](capture/Capture21.PNG)


###### 4-way hadshake
![](capture/Capture22.PNG)


L'access point demande l'identité du client.

*Réponse aux questions:*

###### Quelle ou quelles méthode(s) d’authentification est/sont proposé(s) au client ?*

*Les méthodes d’authentification est proposées : TLS, EAP(EAP-TLS)*
![](capture/Capture23.PNG)



###### Quelle méthode d’authentification est utilisée ?
*La méthode d’authentification utilisée est : EAP(EAP-TLS)* 

![](capture/Capture24.PNG)


###### Lors de l’échange de certificats entre le serveur d’authentification et le client :

Le serveur envoie-t-il un certificat au client ? Pourquoi oui ou non ?
*Oui le serveur envoie un certificat au client*

Le client envoie-t-il un certificat au serveur ? Pourquoi oui ou non ?
*Oui, le client envoie un certificat au serveur (TLS client key), contenant la pre master secret chiffré avec la clé publique du serveur d'authentiﬁcation*
    

    
## 2. Attaque WPA Entreprise


###### Quelles modifications sont nécessaires dans la configuration de hostapd-wpe pour cette attaque ?


*il est nécessaire de modifier le ﬁchier de conﬁguration qui se trouve à /etc/hostapdwpe/hostapd-wpe.conf.*

* *Interface du réseau sans ﬁl dans notre cas Wlan0* 
* *ssid du réseaux canal à utiliser: canal 1*
* *Paramètre wpa = 2*
* *eap_server = 1*

###### Quel type de hash doit-on indiquer à john pour craquer le handshake ?

*NETNTLM*

###### Quelles méthodes d’authentification sont supportées par hostapd-wpe 
*PEAP*, *EAP-TTLS*


