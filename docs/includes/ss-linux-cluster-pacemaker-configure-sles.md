2. Sur tous les nœuds du cluster, créez un fichier pour stocker le nom d’utilisateur et le mot de passe SQL Server du compte de connexion Pacemaker. La commande suivante a pour effet de créer et remplir ce fichier :

   ```bash
   sudo touch /var/opt/mssql/secrets/passwd
   sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
   sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd 
   sudo chmod 600 /var/opt/mssql/secrets/passwd    
   ```

3. Sur tous les nœuds du cluster, ouvrez les ports de pare-feu de Pacemaker. Pour ouvrir ces ports avec `firewalld`, exécutez la commande suivante :

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > Si vous utilisez un autre pare-feu qui n’intègre pas de configuration à haute disponibilité, les ports suivants doivent être ouverts pour permettre à Pacemaker de communiquer avec les autres nœuds du cluster.
   >
   > * TCP : ports 2224, 3121, 21064
   > * UDP : port 5405

1. Installez les packages Pacemaker sur chaque nœud.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```

   

2. Définissez le mot de passe pour l’utilisateur par défaut qui est créé pendant l’installation des packages Pacemaker et Corosync. Utilisez le même mot de passe sur tous les nœuds. 

   ```bash
   sudo passwd hacluster
   ```

   

3. Activez et démarrez le service `pcsd` et Pacemaker. Cela permettra aux nœuds de rejoindre le cluster après le redémarrage. Exécutez la commande suivante sur tous les nœuds.

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. Installez l’agent de ressources FCI pour SQL Server. Exécutez les commandes suivantes sur tous les nœuds. 

   ```bash
   sudo yum install mssql-server-ha
   ```
