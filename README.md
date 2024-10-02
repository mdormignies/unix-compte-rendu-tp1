# unix-compte-rendu-tp1
Cours M. Le Cocq - TP1


### 1-Installation Machine Virtuelle
Pour la partie installation, j'ai eu plusieurs problèmes : le plus compliqué était de chercher la bonne image (ISO) à travers toute l'arborescence. Au finale, le mini.iso de taille d'environ 62mo a été trouvée et lors de l'ajout d'une nouvelle VM sur VirtualBox il fallait bien indiqué la version 64-bit de debian.

Ensuite, j'ai été bloqué de nombreuse minutes sur la dernière étape de l'installation : celle de 'install grub [...]'. Pour régler ce problème, il fallait choisir oui pour demander à installer GRUB en tant que primary device.

### 2-Post Installation
# 2.1 configuration ssh

Pour changer la configuration de ssh pour permettre les connection root distante avec mot de passe j'ai tapé la commande :
  <pre>nano /etc/ssh/sshd_config</pre>. Ensuite j'ai cherché la ligne <pre>#PermitRootLogin prohibit-password</pre> et la remplacé par PermitRootLogin yes. Il ne reste plus qu'a tapé la commande <pre>systemctl restart ssh</pre>

# 2.3 Nombre de paquets 
  <p>La commande : <pre>dpkg -l | wc -l</pre>, fait installer 350 paquets</p>

# 2.4 Space Usage
  <p>La commande : <pre>df -h</pre>, envoie [image]
 </p>

# 2.5 Expliquer les commandes

<p>La commande <pre>echo $LANG</pre>, envoie [image]</p>

<p>La commande <pre>hostname</pre> envoie <pre>server1</pre></p>

<p>Pour trouver le domaine on utilise la commande <pre>hostname -d</pre> qui envoie <pre>ufr-info-p6.jussieu.fr</pre></p>

<p>La commande <pre>cat /etc/apt/sources.list | grep -v -E '^#|^$'</pre> sert à vérifier les dépôts qui sont activés pour l'installation de paquets et envoie [image]</p>

<p>La commande <pre>cat /etc/shadow | grep -vE ':\*:|:!\*:'</pre> sert à voir les comptes ayant un mot de passe configuré dans /etc/shadow et envoie [image]</p>

<p>La commande <pre>cat /etc/passwd | grep -vE 'nologin|sync'</pre> sert à afficher les comptes utilisateurs sauf ceux associés à des services ou qui ne peuvent pas se connecter directement et envoie [image]</p>

<p>La commande <pre>fdisk -l</pre> affiche la table des partitions et les informations sur le disque. La commande <pre>fdisk -x</pre> donne plus de détails sur la géométrie et les structures de disque. Cela permet d'examiner la structure des partitions. Elles envoient [image]</p>

<p>La commande <pre>df -h</pre> donne une vue d'ensemble de l'utilisation de l'espace disquew et envoie [image]</p>

### 3-Aller plus loin

<p>Le preseed est un fichier de configuration qui permet d'automatiser l'installation de Debian et dérivés. Cela sert à répondre automatiquement aux questions posées durant l'installation (comme les paramètres de partitionnement, la configuration réseau, etc.)</p>

<p>Rescue Mode : Si on oublie son mot de passe root, on peut redémarrer sa machine virtuelle en mode "rescue" ou "recovery" et suivre les étapes pour changer le mot de passe :

<pre>Redémarrer la machine.
Accèder au mode "rescue" dans GRUB.
Une fois dans le mode "rescue", on utilise la commande suivante pour réinitialiser le mot de passe root :
'passwd root'</pre></p>










