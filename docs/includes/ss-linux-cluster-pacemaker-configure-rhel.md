1. Sur tous les nœuds du cluster, ouvrez les ports de pare-feu de Pacemaker. Pour ouvrir ces ports avec `firewalld`, exécutez la commande suivante :

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > Si le pare-feu n’a pas de configuration de haute disponibilité intégrée, ouvrez les ports suivants pour Pacemaker.
   >
   > * TCP : ports 2224, 3121, 21064
   > * UDP : port 5405

1. Installez les packages Pacemaker sur tous les nœuds.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```

1. Définissez le mot de passe pour l’utilisateur par défaut qui est créé pendant l’installation des packages Pacemaker et Corosync. Utilisez le même mot de passe sur tous les nœuds. 

   ```bash
   sudo passwd hacluster
   ```

1. Pour autoriser les nœuds à rejoindre le cluster après le redémarrage, activez et démarrez le service `pcsd` et Pacemaker. Exécutez la commande suivante sur tous les nœuds.

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

1. Créez le cluster. Pour ce faire, exécutez la commande suivante :

   **RHEL 7** 

   ```bash
   sudo pcs cluster auth <node1> <node2> <node3> -u hacluster -p <password for hacluster>
   sudo pcs cluster setup --name <clusterName> <node1> <node2> <node3> 
   sudo pcs cluster start --all
   sudo pcs cluster enable --all
   ```

   **RHEL8**

   Pour RHEL 8, vous devez authentifier les nœuds séparément. Entrez manuellement le nom d’utilisateur et le mot de passe pour hacluster lorsque vous y êtes invité.

   ```bash
   sudo pcs host auth <node1> <node2> <node3>
   sudo pcs cluster setup <clusterName> <node1> <node2> <node3>
   sudo pcs cluster start --all
   sudo pcs cluster enable --all
   ```
   
   >[!NOTE]
   >Si vous avez précédemment configuré un cluster sur les mêmes nœuds, vous devez utiliser l’option `--force` pendant l’exécution de `pcs cluster setup`. Cette option revient à exécuter `pcs cluster destroy`. Pour réactiver Pacemaker, exécutez `sudo systemctl enable pacemaker`.

1. Installez l’agent de ressources SQL Server pour SQL Server. Exécutez les commandes suivantes sur tous les nœuds. 

   ```bash
   sudo yum install mssql-server-ha
   ```
