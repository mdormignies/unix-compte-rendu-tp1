# unix-compte-rendu-tp1
Cours M. Le Cocq - TP1


### 1-Installation Machine Virtuelle
Pour la partie installation, j'ai eu plusieurs problèmes : le plus compliqué était de chercher la bonne image (ISO) à travers toute l'arborescence. Au finale, le mini.iso de taille d'environ 62mo a été trouvée et lors de l'ajout d'une nouvelle VM sur VirtualBox il fallait bien indiqué la version 64-bit de debian.

<p>Ensuite, j'ai été bloqué de nombreuse minutes sur la dernière étape de l'installation : celle de 'install grub [...]'. Pour régler ce problème, il fallait choisir oui pour demander à installer GRUB en tant que primary device.</p>

### 2-Post Installation
<h5>2.1 configuration ssh</h5>

<p>Pour changer la configuration de ssh pour permettre les connection root distante avec mot de passe j'ai tapé la commande :
  <strong>nano /etc/ssh/sshd_config</strong>. Ensuite j'ai cherché la ligne <strong>#PermitRootLogin prohibit-password</strong> et la remplacé par PermitRootLogin       yes. Il ne reste plus qu'a tapé la commande systemctl restart ssh.</p>

<h5>2.3 Nombre de paquets</h5>
  <p>La commande : <strong>dpkg -l | wc -l</strong>, fait installer 350 paquets</p>

<h5>2.4 Space Usage</h5>
  <p>La commande : <strong>df -h</strong>, envoie [image]
 </p>

 <h5>2.5 Expliquer les commandes</h5>

<p>La commande <strong>echo $LANG</strong>, envoie [image]</p>

<p>La commande <strong>hostname</strong> envoie <strong>server1</strong></p>

<p>Pour trouver le domaine on utilise la commande <strong>hostname -d</strong> qui envoie <strong>ufr-info-p6.jussieu.fr</strong></p>

<p>La commande <strong>cat /etc/apt/sources.list | grep -v -E '^#|^$'</strong> sert à vérifier les dépôts qui sont activés pour l'installation de paquets et envoie [image]</p>

<p>La commande <strong>cat /etc/shadow | grep -vE ':\*:|:!\*:'</strong> sert à voir les comptes ayant un mot de passe configuré dans /etc/shadow et envoie [image]</p>

<p>La commande <strong>cat /etc/passwd | grep -vE 'nologin|sync'</strong> sert à afficher les comptes utilisateurs sauf ceux associés à des services ou qui ne peuvent pas se connecter directement et envoie [image]</p>

<p>La commande <strong>fdisk -l</strong> affiche la table des partitions et les informations sur le disque. La commande <strong>fdisk -x</strong> donne plus de détails sur la géométrie et les structures de disque. Cela permet d'examiner la structure des partitions. Elles envoient [image]</p>

<p>La commande <strong>df -h</strong> donne une vue d'ensemble de l'utilisation de l'espace disquew et envoie [image]</p>

### 3-Aller plus loin

<p>Le preseed est un fichier de configuration qui permet d'automatiser l'installation de Debian et dérivés. Cela sert à répondre automatiquement aux questions posées durant l'installation (comme les paramètres de partitionnement, la configuration réseau, etc.)</p>

<p>Rescue Mode : Si on oublie son mot de passe root, on peut redémarrer sa machine virtuelle en mode "rescue" ou "recovery" et suivre les étapes pour changer le mot de passe :

<pre>Redémarrer la machine.
Accèder au mode "rescue" dans GRUB.
Une fois dans le mode "rescue", on utilise la commande suivante pour réinitialiser le mot de passe root :
'passwd root'</pre></p>










