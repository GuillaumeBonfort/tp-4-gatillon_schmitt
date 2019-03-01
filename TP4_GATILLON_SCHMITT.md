Welcome to the tp4-gatillon_schmitt wiki! Etudiants : GATILLON Julien, SCHMITT Thomas ETI


# Exercice 1. Gestion des utilisateurs et des groupes

* Afin de _créer_ __les deux groupes__ nous tapons les commandes suivantes : `sudo groupadd groupe1` et `sudo groupadd groupe2`.

* Ensuite pour _créer_ __des users__ nous rentrons la commande suivante pour chacun des u1, u2, u3, u4 : `sudo useradd u1`.

* Pour ensuite _ajouter_ __un utilisateur__ dans un autre groupe nous rentrons la commande suivante : `sudo gpasswd -a u1 groupe1`

* Pour _vérifier_ dans __quel(s) groupe(s) se situe__ l'utilisateur nous pouvons taper : `groups u4`. 

* Pour _afficher_ le __contenu des groupes__ nous pouvons utiliser les différentes commandes suivantes : `cat /etc/group | grep groupe2` ou `grep -w groupe2 /etc/group`

* Pour _faire_ __du groupe1__ le groupe __propriétaire__ de __/home/u1__ nous utilisons la commande suivante : `sudo chown -R u1:groupe1 /home/u1`.

* Pour _remplacer_ le __groupe primaire__ des utilisateurs nous rentrons la commande suivante : `sudo usermod u4 -g groupe2`. Pour _vérifier_ nous pouvons taper la commande `ls -l` dans le dossier /home pour _voir_ __le groupe propriétaire__ de chacun des users.

* Pour _créer_ les __deux répertoires__ nous rentrons les commandes suivantes en se plaçant tout d'abord dans le répertoire __/home__ : `sudo mkdir groupe1` et `sudo mkdir groupe2`.
Pour _mettre en place_ __les permissions__ permettat aux membres de chaque groupe d'écrire dans le dossier associé nous utilisons las commandes : `sudo chmod g+w groupe1` et `sudo chmod g+w groupe2`.

* Pour _retirer_ __les droits__ aux autres ormis le propriétaire du fichier nous tapons la commande : `sudo chmod go-rwx groupe1`.

* Nous __ne pouvons pas nous connecter en tant que u1__, en effet lorque l'on essait on nécessite un password que nous n'avons pas.

* Il faut alors faire une __manipulation__ afin de faire un __nouveau mot de passe__ à u1 : nous tapons la  commande `passwd u1` puis nous définissons un nouveau mot de passe.

* Pour _accéder_ à l'__uid et le gid__ de u1 nous tapons la commande : `id u1`, l'__uid = 1001(u1)__ et le __gid = 1001(groupe1)__.

* L'utilisateur qui à pour __uid = 1003__ est __u3__, pour le retrouver nous utilisons la commande : `cat /etc/passwd | grep 1003`.

* L'__id__ du groupe 1 est __1001__ qui correspond à la valeur : `groups=1001(groupe1)`.

* Pour _obtenir_ le groupe qui a pour __guid = 1002__, nous tapons la commande suivante qui nous permet de trouver que c'est le __groupe 2__ : `cat /etc/group |grep ':1002:'`, cette commande recherche le string __':1002:'__ dans le fichier __/etc/group__. Nous prenons les ':' pour éviter de tomber sur un fichier ou dossier qui aurait pour nom '1002'.

* Nous _pouvons le retirer_ tant que groupe2 est son __groupe secondaire__ mais _nous ne pouvons pas retirer_ u3 complètement du groupe2 car c'est le __groupe primaire__ de cet utilisateur, pour pouvoir le retirer il faut tout d'abord changer le groupe primaire de l'utilisateur.



