I-	INTRODUCTION SUR LES ACL STANDARD ET ETANDUE.

    Une ACL (Access Control List) en anglais peut se traduire en français comme listes de contrôle d'accès qui a pour but de filtré l’accès à un réseau ou à des protocoles spécifiques. En parlants de filtrages d’accès à un réseau, nous voulons dire si le paquet destiné vers notre réseau est autorisé à entrer ou pas et les paquets qui sortent sont-ils autorisés ou pas aussi. Les ACL eux leur rôle est de contrôler les trafics entant ou sortants pour identifier les paquet interdit et les empêcher l’entrer ou la sortie de ces paquets.
EXEMPLE : 1 -les ACL sont comme des vigiles que nous voyons tous les jours. Si l’administration de l’ESMT dis aux vigiles de laisser entrer seulement les étudiants et le personnel de l’ESMT du lundi au samedi et laisser entrer seulement le personnel le dimanche. Donc une personne qui ne fais ni parties des étudiants ni partie du personnel n’aura jamais accès jusqu’à ce que l’administration charges d’avis (exemple de Deny explicite). Et tous les jour les vigiles vérifient qui entre.
2 -Et si l’administration ajoutes que les étudiants ne quitteront l’école qu’à partir de 17h et le personnel à partir de 14H alors les vigiles vérifieront qui sort et qui entre à l’ESMT. Tout de même les ACL fonctionnent de la même manière. C’est-à-dire ils reçoivent des instructions et ils les exécutent.
Les ACL sont configurées sur les interfaces des routeurs.

•	Les ACL STANDARD
Les ACL standard elles fonctionnent comme notre exemple 1. C’est-à-dire les ACL seront mises sur le routeur qui est pré de la destination pour empêcher les paquets d’entrées.
La syntaxe de l’écriture des ACL STANDARD :
Routeur(config)# Access-lits {numéro-de-acl} {DENY/PERMIT} {adresse-ip-destination} {masque-générique}
Ensuite on précise sur quelle interface sera
Configurer l’ACL avec :
Router(config)#int {ledit-interface}
Router (config-if) #ip access-groups {numero_de_acl} {out/in}

•	Les ACL ETANDUE
Les ACL ETANDUE eux ils fonctionnent comme l’Exemple 2 de notre exemple. Ce qui sous-entend qu’on doit mettre les ACL au pré de la source pour empêcher les paquets de quitter leur routeur.
La syntaxe de l’écriture des ACL ETANDUE :
Router(config)# Access-lits {numéro-de-acl} {DENY/PERMIT} {protocole}{adresse-IP-source} {masque-générique} {adresse-IP-destination} {masque-générique} eg {numéro-du-port-de-appli-a-interdire}
Ensuite on le configure sur l’interface concerné.
NB : les numéros des ACL STANDRD sont compris entre 1-99 et entre 1300 – 1999.
Et les numéros des ACL ETANDUE sont compris entre 100-199 et entre 2000-2699.


I.	Corrections des exercices sur les ACL STANDARD accompagner de leurs simulations sur cisco packet tracet.

•	EXERCICE N°1

Les adresses à filtrés :
	10.0.0.0/8
	172.26.0.0/12
	192.168.0.0/16

L’ACL (je nommer mon routeur RY):

SIMILATIONS DE L’EXERCICE N°1
La topologie :
 
Dans cet exercice, nous avions pris le réseaux 213.160.10.0/24 comme notre réseau Locale. Comme la topologie ci-haut le montre les autres réseaux sont les réseaux ou nous voulons filtrer les paquets hors mis les deux réseaux de liaisons qui sont le 213.160.11.0/24 et le 213.160.12.0/24. Notons que les routeurs sont configurés comme des server DHCP et le protocole de routage RIPV2 est configurer au niveaux de tous les routeurs. Nous allons pinger avant l’écriture de l’ACL et après.
Les pings avant l’écriture de l’ACL :
1.	Ping du pc (10.0.0.2/8) vers le pc (213.160.10.2/24) :
 

2.	Ping du pc (172.16.0.2/12) vers le pc (213.160.10.2/24) :

3.	Ping du pc (172.16.0.2/16) vers le pc (213.160.10.2/24) :

 
4.	L’écriture de l’ACL :

 
5.	Ping du pc (10.0.0.2/8) vers le pc (213.160.10.2/24) :

 
6.	Ping du pc (172.16.0.2/12) vers le pc (213.160.10.2/24) :

 

7.	Ping du pc (192.168.0.2/16) vers le pc (213.160.10.2/24) :

EXERCICE N°2
Adresse réseau : 213.154.80.192
Masque : 255.255.255.192 ou /26
4ème Adresse sous réseau : 213.154.80.196
7ème Adresse sous réseau : 213.154.80.199

 
Ecrivons l’ACL:
R(config)# Access-list 1 deny  213.154.80.196   0.0.0.63
R(config)# Access-list 1  deny  213.154.80.199   0.0.0.63
R(config)# Access-list 1 permit any
R(config)# int E0(G0/0)
R(config-if) #ip access-group 1 out

 
•	Ping du pc autorisé ayant l’adresse : 213.154.80.197
•	Ping du pc non autorisé ayant l’adresse 213.154.80.196

EXERCICE N°3 :
Notre réseau : 223.10.55.0/24 et nous voulons le divisés 8 sous-réseaux 6 utilisables et les 4 premiers seront utilisés respectivement par la COMTABILITE, le MARKETING, les INGENIEURS et les CHERCHEURS.
o	223.10.55.0/27 utiliser par le service comptabilité.
o	223.10.55.32/27 utiliser par le service marketing.
o	223.10.55.64/27 utiliser par les ingénieurs.
o	223.10.55.96/27 utiliser par les chercheurs.
o	223.10.55.128/27 et 223.10.55.160/27 pour des extensions futures.
On nous demande :

	D’interdire le trafic provenant des ingénieurs et des chercheurs au niveau de marketing ;
	D’autoriser uniquement le trafic provenant du service marketing au niveau de comptabilité ;
	D’autoriser tout le trafic sauf celui provenant du service comptabilité au niveau des ingénieurs ;
	D’autoriser tout le trafic sauf celui provenant du service comptabilité au niveau des chercheurs ;

LES ACL :
1.	Router(config)# access-list 1 deny 223.10.55.64 0.0.0.31
Router(config)# access-list 1 deny 223.10.55.96 0.0.0.31
Router(config)# access-list 1 permit any
Router(config)#int E1
Router(config-if) #ip access-group 1 out

2.	Router(config)#access-list 2 permit 223.10.55.32 0.0.0.31
Router(config)#int E0
Router(config-if)# ip access-group 2 out

3.	Router(config)# access-list 3 deny 223/10.55.0 0.0.0.31
Router(config)#int E2
Router(config-if) #ip access-group 3 out

4.	Router(config)# access-list 4 deny 223.10.55.0 0.0.0.31
Router(config)#access-list 4 permit any
Router(config)#int E3
Router(config-if)# ip access-group 4 out

SIMILATION DE L’EXERCICE N°3:
 	La topologies:
 

Les 4 ports de ce routeur sont configurés comme des serveurs DHCP et le réseau fonctionnent correctement :

 	Ping de la machine qui a 223.10.55.02/27 vers la machine qui a 223.10.55.34/27 :
 

 	Ping de la machine qui a 223.10.55.02/27 vers la machine qui a 223.10.55.66/27 :
 

 	Ping de la machine qui a 223.10.55.02/27 vers la machine qui a 223.10.55.98/27 :
 


Comme le réseau fonctionne correctement, nous allons écrire les ACL pour filtrer le trafic au sein de ce réseau :
 	Acl n°1
 

 	Acl n°2
 
 	Acl n°3
 
 	Acl n°4
 
A présent nous allons vérifier si les ACL filtrent réellement le trafic :
	Le Ping de la machine qui a 223.10.55.78/27 vers la machine qui a 223.10.55.34/27 :
 

	Le Ping de la machine qui a 223.10.55.99/27 vers la machine qui a 223.10.55.39/27 :
 

	Le Ping de la machine qui a 223.10.55.100/27 vers la machine qui a 223.10.55.5/27 :
 

	Le Ping de la machine qui a 223.10.55.69/27 vers la machine qui a 223.10.55.10/27 :
 

	Le Ping de la machine qui a 223.10.55.45/27 vers la machine qui a 223.10.55.11/27 :
 

	Le Ping de la machine qui a 223.10.55.13/27 vers la machine qui a 223.10.55.68/27 :
 

	Le Ping de la machine qui a 223.10.55.98/27 vers la machine qui a 223.10.55.68/27
 
	Le Ping de la machine qui a 223.10.55. 46/27 vers la machine qui a 223.10.55.66/27 :
 

	Le Ping de la machine qui a 223.10.55.12/27 vers la machine qui a 223.10.55.98/27 :
 

	Le Ping de la machine qui a 223.10.55.78/27 vers la machine qui a 223.10.55.99/27 :
 

	Le Ping de la machine qui a 223.10.55.40/27 vers la machine qui a 223.10.55.100/27 :
 


Exercice 4 :
	Tableau d’adressage

Périphériques	Adresse IP	Masque
routeur	210.150.80.65	255.255.255.240
Serveur web	210.150.80.66	255.255.255.240
Serveur mess	210.150.80.67	255.255.255.240
Pc internet	@ paires	255.255.255.240
Machines internes	@ impaires	255.255.255.240

	Schéma de topologie

Option 2:
R(config)# access-list 20 permit host 210.150.80.66
R(config)# access-list 20 permit host 210.150.80.67
R(config)# access-list 20 permit 210.150.80.68 0.0.0.14
R(config)# access-list 20 deny any
R(config)# interface S0/0/0
R(config-if)# ip access-group 20 out

•	Ping d’un des pc internes

II.	Corrections des exercices sur les ACL ETANDUE accompagner de leurs simulations sur cisco packet tracet.
EXERCICE N°1 :
Notre réseau : 207.50.235.224/28
On nous demande d’écrire un acl qui interdit tout trafic de sortir de notre interface si le trafic n’est pas destiné à l’une des machines de notre réseau.
L’ACL :
Routeur(config)# access-list 102 permit ip any 207.50.235.224 0.0.0.15
Routeur(config)# access-list 102 deny any any
Routeur(config)# int E0
Routeur(config-if)# ip access-group 102 out

Simulation de l’exercice 1:
	La topologies du réseau:
 

Ce réseau est normalement configuré, tous les routeurs comme des serveurs DHCP avec le protocole de routage ripv2 :
	Ping de la machine (10.0.0.2/8) vers la machine (207.50.235.229) :
 

	Ping de la machine (128.128.0.3/8) vers la machine (207.50.235.233) :
 

	Ping de la machine (192.198.0.7/8) vers la machine (207.50.235.238) :

	L’écriture de l’ACL :
 
Après cela, tout trafic qui n’est pas destiné à un des machines appartenant au sous-réseau (207.50.235.244/28 c’est-à-dire de 207.50.235.225 jusqu’à 207.50.235.238), le trafic sera rejeté automatiquement si celui si désir entrer dans notre interface.

EXERCICE N°2 :
Nous avons deux sous réseaux :
	213.154.80.192/26 utiliser par les élèves de L’ESMT et
	213.154.80.128/26 utiliser par les formateurs de L’ESMT.
On nous demande :
•	D’interdire le trafic Telnet (23) à destination des formateurs,
•	D’interdire le trafic FTP (21) à destination des formateurs et
•	Interdire tout le trafic à destination du serveur d’impression.

L’ACL :
Routeur(config)# access-list 111 deny tcp 213.154.80.192 0.0.0.63 213.154.80.128 0.0.0.63 eq 23
Routeur(config)# access-list 111 deny tcp 213.154.80.192 0.0.0.63 213.154.80.128 0.0.0.63 eq 21
Routeur(config)# access-list 111 deny ip 213.154.80.192 0.0.0.63 host 213.154.80.145
Routeur(config)# access-list 111 permit ip any any
Routeur(config)#int E0
Routeur(config-if)# ip access-group 111 in

Simulation de l’exercice n°2:
	La topologies du reseau:
 
Les machines de tout ce réseau ont eu des adresses automatiquement via le routeur qui est configurer comme un serveur DHCP sauf les deux serveurs (le serveur FTP et L’Imprimante), le serveur FTP à l’adresse 213.154.80.137 et l’imprimante 213.154.80.145.
On va d’abord vérifier si le trafic Telnet, FTP et celui de l’imprimante sont fonctionnelle et communique correctement avec les machines de élèves.
	Test du trafic Telnet du machine (213.154.80.195/26) vers l’interface 213.145.80.129/26 :
 

	Test du trafic FTP du machine (213.154.80.201/26) vers le server 213.145.80.137/26 :
 

	Ping de la machine 213.154.80.200/26 vers l’imprimante 213.154.80.145/26
 

Comme tous les services sont en marche, nous allons procéder à l’écriture de l’ACL :
 
Nous allons revérifier si les élèves auront toujours le privilège d’utiliser les services précités ?
	Vérification Telnet avec la machine 213.154.80.199 vers 213.154.80.129 :
 
	Vérification Telnet avec la machine 213.154.80.201 vers 213.154.80.137 :
 

	Le Ping de la machine 213.154.80.196 vers l’imprimante 213.154.80.145/26
 
Donc l’acl prend toutes les conditions en charge.

EXERCICE N°3 :
Notre réseau : 223.10.55.0/24 et nous voulons le divisés 8 sous-réseaux 6 utilisables et les 4 premiers seront utilisés respectivement par la COMTABILITE, le MARKETING, les INGENIEURS et les CHERCHEURS.
•	223.10.55.0/27 utiliser par le service comptabilité.
•	223.10.55.32/27 utiliser par le service marketing.
•	223.10.55.64/27 utiliser par les ingénieurs.
•	223.10.55.96/27 utiliser par les chercheurs.
•	223.10.55.128/27 et 223.10.55.160/27 pour des extensions futures.
On nous demande :
	D’interdire le trafic tout le trafic vers la comptabilité ;
	D’autoriser uniquement le trafic demande (established) au niveau du service marketing ;
	D’interdire uniquement le trafic vers les >1024 vers les ingénieurs ;
	D’interdire uniquement le trafic vers les >1024 vers les chercheurs ;
	D’interdire tout le trafic vers les deux deniers sous-réseaux.
NB : Dans l’exercice on a dit d’interdire uniquement le trafic vers les >1024 vers chez les formateurs, nous avions considérés les chercheurs et les formateurs comme des formateurs comme ce n’était pas bien énumérer qui était le formateur.
Les acl :
1.	Routeur(config)# access-list 101 deny ip any 223.10.55.0 0.0.0.31
Routeur(config)# INT G0/0
Routeur(config-if)# ip access-group 101 in

2.	Routeur(config)# access-list 102 permit tcp  any 223.10.55.32 0.0.0.31 established
Routeur(config)# INT G0/1
Routeur(config-if)# ip access-group 102 in

3.	Routeur(config)# access-list 103 deny tcp  any 223.10.55.64 0.0.0.31 gt 1024
Routeur(config)# access-list 103 deny udp  any 223.10.55.64 0.0.0.31 gt 1024
Routeur(config)# access-list 103 permit ip  any 223.10.55.64 0.0.0.31
Routeur(config)# INT G0/2
Routeur(config-if)# ip access-group 103 in

4.	Routeur(config)# access-list 104 deny tcp  any 223.10.55.96 0.0.0.31 gt 1024
Routeur(config)# access-list 104 deny udp  any 223.10.55.96 0.0.0.31 gt 1024
Routeur(config)# access-list 104 permit ip  any 223.10.55.96 0.0.0.31
Routeur(config)# INT VLAN 1
Routeur(config-if)# ip access-group 104 in

5.	Routeur(config)# access-list 105 deny IP any 223.10.55.128 0.0.0.31
Routeur(config)# INT VLAN 2
Routeur(config-if)# ip access-group 105 in

6.	Routeur(config)# access-list 106 deny IP any 223.10.55.160 0.0.0.31
Routeur(config)# INT VLAN 3
Routeur(config-if)# ip access-group 106 in

SIMILATION DE L’EXERCICE 3:
	LA TOPOLOGIE:

Comme le montre la topologie, les parties colorées et entourées sont les sous-réseaux qu’on veut les filtrer et de l’autre cote, on le routeur, le serveur et les machines sont considérés ici comme l’internet (223.10.55.224/27).
Vous allez vous demander surement quel routeur pourrait avoir 6 interface physique pour interconnecter tous ses sous-réseaux ? mais sachez qu’ici les 3 premiers sous-réseaux ont des interface (gigabit Ethernet) et les trois second ont des interfaces du switch et ont les a configurées comme des vlan donc tout est fonctionnel. Et les machines ont des adosses reçus via des serveurs DHCP (le routeur est configuré comme un serveurs DHCP avec plusieurs pools) en plus les deux routeurs ont aussi le protocole de routage ripv2.
A présent nous allons passer au test de connectivité à travers des Ping avant l’écriture des acl.

	Les Ping :
	Ping de 223.10.55.3/27 vers 223.10.55.226/27 (test de connexion entre la compta et internet) :
 

	Ping de 223.10.55.34/27 vers 223.10.55.227/27 (test de connexion entre la marketing et internet) :
 

	Ping de 223.10.55.66/27 vers 223.10.55.228/27 (test de connexion entre Les ingénieurs et internet) :
 
	Ping de 223.10.55.104/27 vers 223.10.55.227/27 (test de connexion entre Les
Chercheurs et internet) :

	Ping de 223.10.55.136/27 vers 223.10.55.228/27 (test de connexion entre le SRX 223.10.55.128/27 et internet) :
 
	Ping de 223.10.55.168/27 vers 223.10.55.227/27 (test de connexion entre le SRX 223.10.55.160/27 et internet) :

Comme tous les 6 sous-réseaux communique correctement avec internet, a présent nous allons écrire les acl.

	L’écriture des acl
	ACL n°1
 

	ACL N°2
 
	ACL n°3
 

	ACL n°4
 

	ACL n°5
 

	ACL n°6
 

Après l’écriture des ACL, nous allons maintenant tester la connectivité entre les réseaux et l’internet.
	Le Ping du 223.10.55.6/27 vers 223.10.55.226/27 (test de connexion entre la compta et l’internet) :
 

	Le Ping du 223.10.55.41/27 vers 223.10.55.228/27 (test de connexion entre Le marketing et l’internet) :
 

	Le Ping du 223.10.55.73/27 vers 223.10.55.227/27 (test de connexion entre Les ingénieurs et l’internet) :
 

	Le Ping du 223.10.55.101/27 vers 223.10.55.228/27 (test de connexion entre Les Chercheurs et l’internet) :
 

	Le Ping du 223.10.55.137/27 vers 223.10.55.228/27 (test de connexion entre SRX 223.10.55.128/27 et l’internet) :
 

	Le Ping du 223.10.55.166/27 vers 223.10.55.227/27 (test de connexion entre SRX 223.10.55.160/27 et l’internet) :

EXERCICE N°4 :
1.	PRÉSENTATION DE L’EXERCICE
Dans cet exercice, nous disposons d’un cybercafé composé de dix (10) postes clients, de deux (2) serveurs et d’un routeur relié à Internet.
Le réseau utilisé est 210.150.80.64/28.
L’objectif est de mettre en place une access-list étendue afin de filtrer le trafic sortant du réseau local et ainsi contrôler l’utilisation de la bande passante.
2.	TOPOLOGIE DU RÉSEAU

Figure 4 : Topologie Cybercafé

La topologie est constituée d’un seul réseau local (LAN) dans lequel tous les postes clients et les serveurs sont connectés à un switch central. Le switch est relié à un routeur assurant l’accès vers Internet.
3.	PLAN D’ADRESSAGE IP
Le réseau 210.150.80.64/28 fournit 14 adresses IP utilisables.
Equipement	Adresse IP	Masque	Rôle
Routeur (LAN)	210.150.80.65	255.255.255.240	Passerelle
Serveur web	210.150.80.66	255.255.255.240	http
Serveur mail	210.150.80.67	255.255.255.240	SMTP/ POP3/IMAP
PC a IP paires	210.150.80.68 à 210.150.80.76	255.255.255.240	Web
PC a IP impaires	210.150.80.69 à 210.150.80.77	255.255.255.240	VoIP

Tous les équipements utilisent comme passerelle par défaut l’adresse IP du routeur : 210.150.80.65.
4.	CHOIX DU TYPE D’ACL
Une ACL étendue est utilisée car le filtrage repose à la fois sur :
•	L’adresse IP source,
•	Le type de protocole,
•	Le numéro de port.
Ce type d’ACL permet un contrôle précis du trafic réseau.
L’utilisation d’une ACL standard n’aurait pas permis de répondre aux contraintes de l’exercice, car elle ne filtre que sur l’adresse IP source et ne prend pas en compte les numéros de ports ni les protocoles.
5.	PLACEMENT DE L’ACL
L’ACL est appliquée :
•	Sur le routeur du cybercafé,
•	En entrée (IN) de l’interface LAN.
Ce choix permet de filtrer le trafic dès sa sortie du réseau local, avant qu’il n’atteigne Internet, ce qui permet d’économiser la bande passante.
Le sens IN est choisi afin de bloquer les paquets dès leur arrivée sur l’interface LAN du routeur, ce qui évite qu’un trafic non autorisé ne soit routé inutilement vers l’extérieur.
6.	RÈGLES DE FILTRAGE APPLIQUÉES
•	Le serveur WEB est autorisé à utiliser HTTP et ICMP.
•	Le serveur MAIL est autorisé à utiliser les services de messagerie et ICMP.
•	Les postes à adresses IP paires sont autorisés uniquement à accéder au Web (HTTP).
•	Les postes à adresses IP impaires sont autorisés uniquement à utiliser la VoIP (port 20012).
•	Tout autre trafic est bloqué.
Les ports utilisés correspondent aux services standards : HTTP (80) pour le Web, SMTP (25), POP3 (110) et IMAP (143) pour la messagerie électronique, et le port 20012 pour la VoIP, conformément à l’énoncé.

7.	CONFIGURATION DE L’ACL ÉTENDUE
Routeur(config)# access-list 105 ip access-list extended ACL_CYBER_SORTIE
Routeur(config)# access-list 105 Permit tcp host 210.150.80.66 any eq www
Routeur(config)# access-list 105 Permit icmp host 210.150.80.66 any
Routeur(config)# access-list 105 Permit tcp host 210.150.80.67 any eq SMTP
Routeur(config)# access-list 105 Permit tcp host 210.150.80.67 any eq pop3
Routeur(config)# access-list 105 Permit tcp host 210.150.80.67 any eq 143
Routeur(config)# access-list 105 Permit icmp host 210.150.80.67 any
Routeur(config)# access-list 105 permit tcp host 210.150.80.68 any eq www
Routeur(config)# access-list 105 permit tcp host 210.150.80.70 any eq www
Routeur(config)# access-list 105 permit tcp host 210.150.80.72 any eq www
Routeur(config)# access-list 105 permit tcp host 210.150.80.74 any eq www
Routeur(config)# access-list 105 permit tcp host 210.150.80.76 any eq www
Routeur(config)# access-list 105 permit tcp host 210.150.80.69 any eq 20012
Routeur(config)# access-list 105 permit tcp host 210.150.80.71 any eq 20012
Routeur(config)# access-list 105 permit tcp host 210.150.80.73 any eq 20012
Routeur(config)# access-list 105 permit tcp host 210.150.80.75 any eq 20012
Routeur(config)# access-list 105 permit tcp host 210.150.80.77 any eq 20012
Routeur(config)# access-list 105 deny ip any any
8.	APPLICATION DE L’ACL
Routeur(config)#interface gigabitEthernet0/0
Routeur(config-if)# ip access-group 105 in
9.	TEST DE VALIDATION

Poste	Test effectué	Résultat
PC a IP paire	Ping vers Internet	Echec
PC a IP pair	Accès web	Succès
PC a IP impair	Accès web	Echec
PC a IP impaire	VoIP	Succès
Server WEB	Ping/HTTP	Succès
Server MAIL	Mail/Ping	Succès

Les résultats confirment le bon fonctionnement de l’ACL.
L’Access List étendue mise en place permet de contrôler efficacement le trafic sortant du cybercafé. Les règles définies sont respectées et l’objectif de limitation de la bande passante est atteint.
L’utilisation d’une ACL étendue permet un filtrage précis basé sur les adresses IP et les ports, garantissant une meilleure gestion du trafic réseau.
Cette configuration améliore la sécurité et l’efficacité du réseau en limitant les usages non autorisés tout en garantissant le fonctionnement normal des services essentiels.

CONCLUSION

Les ACL (Listes de Contrôle d’Accès) sont des mécanismes essentiels de la sécurité et de la gestion du trafic dans les réseaux informatiques. Elles permettent de filtrer les paquets en autorisant ou en refusant le trafic selon des critères précis tels que l’adresse IP source ou destination, le protocole et les ports.
Grâce aux ACL, l’administrateur réseau peut protéger les ressources, contrôler l’accès aux services et optimiser la circulation du trafic en appliquant des règles adaptées aux besoins de l’organisation. On distingue principalement les ACL standards, qui filtrent uniquement sur l’adresse source, et les ACL étendues, plus complètes et plus précises.
Une bonne conception et un bon positionnement des ACL sont indispensables pour éviter les erreurs de configuration et garantir un réseau sécurisé, performant et fiable. En résumé, les ACL constituent un outil fondamental pour assurer la sécurité, le contrôle et la stabilité d’un réseau.



