Welcome to the tp4-gatillon_schmitt wiki! Etudiants : GATILLON Julien, SCHMITT Thomas ETI


# Exercice 1. Gestion des utilisateurs et des groupes

* Afin de _créer_ __les deux groupes__ nous tapons les commandes suivantes : `sudo groupadd groupe1` et `sudo groupadd groupe2`.

* Ensuite pour _créer_ __des users__ nous rentrons la commande suivante pour chacun des u1, u2, u3, u4 : `sudo useradd u1`.

* Pour ensuite _ajouter_ __un utilisateur__ dans un autre groupe nous rentrons la commande suivante : `sudo gpasswd -a u1 groupe1`

* Pour _vérifier_ dans __quel(s) groupe(s) se situe__ l'utilisateur nous pouvons taper : `groups u4`. 

* Pour _afficher_ le __contenu des groupes__ nous pouvons utiliser les différentes commandes suivantes : `cat /etc/group | grep groupe2` ou `grep -w groupe2 /etc/group`

* Pour _faire_ __du groupe1__ le groupe __propriétaire__ de __/home/u1__ nous utilisons la commande suivante : `sudo chown -R u1:groupe1 /home/u1`.

* Pour _remplacer_ le __groupe primaire__ des utilisateurs nous rentrons la commande suivante : `sudo usermod u4 -g groupe2`. Pour _vérifier_ nous pouvons taper la commande `ls -l` dans le dossier /home pour _voir_ __le groupe propriétaire__ de chacun des users.

