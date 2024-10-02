# unix-compte-rendu-tp1
Cours M. Le Cocq - TP1


<h3>Installation Machine Virtuelle</h3>
<p> Pour la partie installation, j'ai eu plusieurs problèmes : le plus compliqué était de chercher la bonne image (ISO) à travers toute l'arborescence. Au finale, le mini.iso de taille d'environ 62mo a été trouvée et lors de l'ajout d'une nouvelle VM sur VirtualBox il fallait bien indiqué la version 64-bit de debian.</p>

<p>Ensuite, j'ai été bloqué de nombreuse minutes sur la dernière étape de l'installation : celle de 'install grub [...]'. Pour régler ce problème, il fallait choisir oui pour demander à installer GRUB en tant que primary device.</p>

<h3>Post Installation</h3>
<h5>2.1 configuration ssh</h5>

<p>Pour changer la configuration de ssh pour permettre les connection root distante avec mot de passe j'ai tapé la commande :
  <strong>nano /etc/ssh/sshd_config</strong>. Ensuite j'ai cherché la ligne <strong>#PermitRootLogin prohibit-password</strong> et la remplacé par PermitRootLogin       yes. Il ne reste plus qu'a tapé la commande systemctl restart ssh.</p>

<h5>2.3 Nombre de paquets</h5>
  <p>La commande : <strong>dpkg -l | wc -l</strong>, fait installer 350 paquets</p>

<h5>2.4 Space Usage</h5>
  <p>La commande : <strong>df -h</strong>, envoie ![Capture d'écran 2024-10-02 143823](https://github.com/user-attachments/assets/1609b461-dafc-4da4-b7f2-602c0ead99dd)
 </p>

 <h5>2.5 Expliquer les commandes</h5>

<p>La commande <strong>echo $LANG</strong>, envoie ![image](https://github.com/user-attachments/assets/a51c8efe-7d44-47b1-85ef-f649f2271ea4)
<></p>

<p>La commande <strong>hostname</strong> envoie </p>
