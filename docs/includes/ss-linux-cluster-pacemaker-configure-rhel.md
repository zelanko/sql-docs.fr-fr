
3. Sur les deux nœuds de cluster, ouvrez les ports de pare-feu Pacemaker. Pour ouvrir ces ports avec `firewalld`, exécutez la commande suivante :

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

   

2. Définissez le mot de passe pour l’utilisateur par défaut qui est créé pendant l’installation des packages Pacemaker et Corosync. Utilisez le même mot de passe sur les deux nœuds. 

   ```bash
   sudo passwd hacluster
   ```

   

3. Activez et démarrez le service `pcsd` et Pacemaker. Cela permettra aux nœuds de rejoindre le cluster après le redémarrage. Exécutez la commande suivante sur les deux nœuds :

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. Créez le cluster. Pour ce faire, exécutez la commande suivante :

   ```bash
   sudo pcs cluster auth <nodeName1> <nodeName2…> -u hacluster -p <password for hacluster>
   sudo pcs cluster setup --name <clusterName> <nodeName1> <nodeName2…> 
   sudo pcs cluster start --all
   ```
   
   >[!NOTE]
   >Si vous avez configuré un cluster sur les mêmes nœuds, vous devez utiliser l’option « --force » pendant l’exécution de « pcs cluster setup ». Notez que cela revient à exécuter « pcs cluster destroy » et que le service Pacemaker doit être réactivé à l’aide de « sudo systemctl enable pacemaker ».

5. Installez l’agent de ressources SQL Server pour SQL Server. Exécutez les commandes suivantes sur les deux nœuds : 

   ```bash
   sudo yum install mssql-server-ha
   ```
