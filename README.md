# unix-compte-rendu-tp1
Cours M. Le Cocq - TP1


### 1-Installation Machine Virtuelle
Pour la partie installation, j'ai eu plusieurs problèmes : le plus compliqué était de chercher la bonne image (ISO) à travers toute l'arborescence. Au finale, le mini.iso de taille d'environ 62mo a été trouvée et lors de l'ajout d'une nouvelle VM sur VirtualBox il fallait bien indiqué la version 64-bit de debian.

Ensuite, j'ai été bloqué de nombreuse minutes sur la dernière étape de l'installation : celle de 'install grub [...]'. Pour régler ce problème, il fallait choisir oui pour demander à installer GRUB en tant que primary device.

### 2-Post Installation
# 2.1 configuration ssh

Pour changer la configuration de ssh pour permettre les connection root distante avec mot de passe j'ai tapé la commande :
  <pre>nano /etc/ssh/sshd_config</pre> Ensuite j'ai cherché la ligne <pre>#PermitRootLogin prohibit-password</pre> et la remplacé par PermitRootLogin yes. Il ne reste plus qu'a tapé la commande <pre>systemctl restart ssh</pre>

# 2.3 Nombre de paquets 
  <p>Cette commande fait installer 350 paquets : <pre>dpkg -l | wc -l</pre></p>

# 2.4 Space Usage
  <p>Cette commande : <pre>df -h</pre> envoie 
  <pre>Filesystem      Size  Used Avail Use% Mounted on
udev            5.1G     0  5.1G   0% /dev
tmpfs           1.1G  568K  1.1G   1% /run
/dev/sda1       9.1G  1.2G  7.5G  14% /
tmpfs           5.1G     0  5.1G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
/dev/sda2       3.6G   40K  3.4G   1% /tmp
/dev/sda3       921M   54M  804M   7% /var/log
tmpfs           1.1G     0  1.1G   0% /run/user/0</pre>
 </p>

# 2.5 Expliquer les commandes

<p>La commande <pre>echo $LANG</pre> envoie <pre>en_US.UTF-8</pre></p><hr>

<p>La commande <pre>hostname</pre> envoie <pre>server1</pre></p><hr>

<p>Pour trouver le domaine on utilise la commande <pre>hostname -d</pre> qui envoie <pre>ufr-info-p6.jussieu.fr</pre></p><hr>

<p>La commande <pre>cat /etc/apt/sources.list | grep -v -E '^#|^$'</pre> sert à vérifier les dépôts qui sont activés pour l'installation de paquets et envoie 
<pre>deb http://ftp.lip6.fr/pub/linux/distributions/debian/ bookworm main
deb http://security.debian.org/debian-security bookworm-security main
deb http://ftp.lip6.fr/pub/linux/distributions/debian/ bookworm-updates main</pre></p><hr>

<p>La commande <pre>cat /etc/shadow | grep -vE ':\*:|:!\*:'</pre> sert à voir les comptes ayant un mot de passe configuré dans /etc/shadow et envoie 
<pre>root:$y$j9T$VaI99/9MweJT8CdE0qNzO0$SP38nMIyGjjl7ZWrVu9PcaL0wzJoUTkT56V.toOG3u8:19998:0:99999:7:::
messagebus:!:19998::::::
avahi-autoipd:!:19998::::::
sshd:!:19998::::::</pre></p><hr>

<p>La commande <pre>cat /etc/passwd | grep -vE 'nologin|sync'</pre> sert à afficher les comptes utilisateurs sauf ceux associés à des services ou qui ne peuvent pas se connecter directement et envoie 
<pre>root:x:0:0:root:/root:/bin/bash</pre></p><hr>

<p>La commande <pre>fdisk -l</pre> affiche la table des partitions et les informations sur le disque. La commande <pre>fdisk -x</pre> donne plus de détails sur la géométrie et les structures de disque. Cela permet d'examiner la structure des partitions. Elles envoient 
<pre>Disk /dev/sda: 20 GiB, 21474836480 bytes, 41943040 sectors
Disk model: VBOX HARDDISK
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A52FF51D-72CA-4A08-87E0-3CF7DC38D99B

Device        Start      End  Sectors  Size Type
/dev/sda1      2048 19531775 19529728  9.3G Linux filesystem
/dev/sda2  19531776 27344895  7813120  3.7G Linux filesystem
/dev/sda3  27344896 29298687  1953792  954M Linux filesystem
/dev/sda4  29298688 41940991 12642304    6G Linux swap</pre>
<pre>Disk /dev/sda: 20 GiB, 21474836480 bytes, 41943040 sectors
Disk model: VBOX HARDDISK
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A52FF51D-72CA-4A08-87E0-3CF7DC38D99B
First usable LBA: 34
Last usable LBA: 41943006
Alternative LBA: 41943039
Partition entries starting LBA: 2
Allocated partition entries: 128
Partition entries ending LBA: 33

Device        Start      End  Sectors Type-UUID                            UUID                                 Name Attrs
/dev/sda1      2048 19531775 19529728 0FC63DAF-8483-4772-8E79-3D69D8477DE4 419798AB-91A9-4D1D-89FA-3FB99082761C la racine

/dev/sda2  19531776 27344895  7813120 0FC63DAF-8483-4772-8E79-3D69D8477DE4 70F664B3-40E8-49FE-81AF-B0FF5A0A0DE7 espace tempo

/dev/sda3  27344896 29298687  1953792 0FC63DAF-8483-4772-8E79-3D69D8477DE4 DAEC92D7-F93C-4D12-84D8-A4EC1ABD142D les logs

/dev/sda4  29298688 41940991 12642304 0657FD6D-A4AB-43C4-84E5-0933C84B4F4F E2C5658F-FAFA-47CB-934E-3CA4BDE50E77 ma swap</p><hr>

<p>La commande <pre>df -h</pre> donne une vue d'ensemble de l'utilisation de l'espace disquew et envoie 
  <pre>Filesystem      Size  Used Avail Use% Mounted on
udev            5.1G     0  5.1G   0% /dev
tmpfs           1.1G  568K  1.1G   1% /run
/dev/sda1       9.1G  1.2G  7.5G  14% /
tmpfs           5.1G     0  5.1G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
/dev/sda2       3.6G   40K  3.4G   1% /tmp
/dev/sda3       921M   54M  804M   7% /var/log
tmpfs           1.1G     0  1.1G   0% /run/user/0</pre></p><hr>

### 3-Aller plus loin

<p>Le preseed est un fichier de configuration qui permet d'automatiser l'installation de Debian et dérivés. Cela sert à répondre automatiquement aux questions posées durant l'installation (comme les paramètres de partitionnement, la configuration réseau, etc.)</p>

<p>Rescue Mode : Si on oublie son mot de passe root, on peut redémarrer sa machine virtuelle en mode "rescue" ou "recovery" et suivre les étapes pour changer le mot de passe :

<pre>Redémarrer la machine.
Accèder au mode "rescue" dans GRUB.
Une fois dans le mode "rescue", on utilise la commande suivante pour réinitialiser le mot de passe root :
'passwd root'</pre></p>










