Welcome to the tp4-gatillon_schmitt ! Etudiants : GATILLON Julien, SCHMITT Thomas ETI


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

* Nous _pouvons le retirer_ tant que groupe2 est son __groupe secondaire__ avec la commande : `sudo gpasswd -d u3 groupe2`, mais _nous ne pouvons pas retirer_ u3 complètement du groupe2 car c'est le __groupe primaire__ de cet utilisateur, pour pouvoir le retirer il faut tout d'abord changer le groupe primaire de l'utilisateur.


* Pour _modifier_ le compte de u4 de sorte que :

  * L'expiration de l'utilisateur soit le 1er juin 2019 : `sudo usermod --expiredate 2019-06-1 u4`.

  * Le mot de passe doit être changé avant 90 jours : `sudo chage -M 5 u4`.

  * Nous devons attendre 5 jours pour modifier un mot de passe : `sudo chage -m 5 u4`.

  * L'utilisateur est averti 14 jours avantl'expiration de sonmotde passe : `sudo chage -W 14 u4`.

  * Le comptese bloque 30 jours arèsl'expiration du mot de passe : `sudo chage -I 30 u4`.


* Pour _connaître l'interpréteur de commande (Shell)__ de l’utilisateur root nous tapons la commande : `eccho $SHELL`,qui nousdonne le résultat : __/bin/bash__ .

* Il existe un utilisateur __qui n'a aucun fichier__ et __qui n'appartient a aucun groupe__ c'est l'utilisateur *__nobody__*.

* Le mot de passe utilisateur est gardé en mémoire par la commande __sudo__ pendant __15 minutes__ par défaut. Pour _forcer_ __sudo__ à l'oublier nous pouvons taper la commande `sudo-k`.



# Exercice 2. Gestion des permissions

* Nous nous plaçons dans le dossier __/HOME__ et nous tapons la commande `sudo mkdir test` pour créer le dossier __test__.
Nous nous plaçons ensuite dans ce dernier dossier et nous tapons la commande : `touch fichier1` pour créer le fichier __fichier1__. Nous tapons ensuite la commande `ls -l` pour voir les droits du __fichier1__ qui sont : __rw-rw-r--__, on retourne dans le __/HOME__ et on voit les droits de __test__ : __rwxrwxr-x__ .

* Pour redirer tous les droits à tout le monde nous utilisons la commande : `chmod 000 fichier1`. En utilisant la commande __sudo__ nous _pouvons tout de même le modifier et l'afficher_. Pour _conclure_ en tant que root nous avons des droits __supérieurs__ au reste, ce qui semble normal pour avoir un __contrôle__ sur le système.

* Pour nous _redonner_ les droits en écriture et en exécution nous tapons la commande `chmod u+wx fichier1`. Nous exécutons ensuite la commande `echo "echo Hello" > fichier`. Nous avons pu _modifier et enregistrer_ le contenu du fichier mais il nous est impossible de _lire_ son contenu car nous n'en __avons pas le droit__. 

* Nous _ne pouvons pas exécuter_ le fichier. Nous avons pourtant la __permission d'exécuter mais pas celle de lire__, nous pouvons en _conclure_ qu'il est nécessaire d'avoir la __permission de lire pour exécuter__. Par contre l'exécution avec __sudo__ fonctionne normalement.

* 
