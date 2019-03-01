Welcome to the tp4-gatillon_schmitt wiki! Etudiants : GATILLON Julien, SCHMITT Thomas ETI


# Exercice 1. Gestion des utilisateurs et des groupes

* Afin de _créer_ les deux groupes nous tapons les commandes suivantes : `sudo groupadd groupe1` et `sudo groupadd groupe2`.

* Ensuite pour _créer_ des users nous rentrons la commande suivante pour chacun des u1, u2, u3, u4 : `sudo useradd u1`.

* Pour ensuite _ajouter_ un utilisateur dans un autre groupe nous rentrons la commande suivante : `sudo gpasswd -a u1 groupe1`

* Pour _vérifier_ dans quel(s) groupe(s) est l'utilisateur nous pouvons taper : `groups u4`. 

* Pour _afficher_ le contenu des groupes nous pouvons utiliser les différentes commandes suivantes : `cat /etc/group | grep groupe2` ou `grep -w groupe2 /etc/group`

* Pour _déplacer_ les utilisateurs de __groupe primaire__ nous rentrons la commande suivante : `sudo usermod u4 -g groupe2`. Pour _vérifier_ nouspouvonstaper la commande `ls -l` dans le dossier /home pour voir le groupe propriétaire de chacun des users.
