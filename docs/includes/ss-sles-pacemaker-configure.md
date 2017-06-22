1. **Sur les deux nœuds du cluster, créez un fichier pour stocker le nom d’utilisateur et le mot de passe SQL Server du compte de connexion Pacemaker**. La commande suivante a pour effet de créer et remplir ce fichier :

    ```bash
    sudo touch /var/opt/mssql/secrets/passwd
    sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
    sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
    sudo chown root:root /var/opt/mssql/secrets/passwd 
    sudo chmod 600 /var/opt/mssql/secrets/passwd
    ```
2. **Tous les nœuds de cluster doivent pouvoir accéder aux uns et aux autres via SSH**. Certains outils, comme hb_report ou crm_report (pour le dépannage) et l’Explorateur d’historique de Hawk, exigent un accès SSH sans mot de passe entre les nœuds, sinon ils ne peuvent collecter que les données du nœud actif. Si vous utilisez un port SSH non standard, utilisez l’option -X (consultez le manuel). Par exemple, si votre port SSH est le 3479, appelez un hb_report avec :

    ```bash
    crm_report -X "-p 3479" [...]
    ```

    Pour plus d’informations, consultez la [configuration système requise et les recommandations dans la documentation de SUSE](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_requirements_other.html).

3. **Installez l’extension High Availability**. Pour installer cette extension, suivez les étapes décrites dans la rubrique SUSE suivante :
    
    [Installation and Setup Quick Start](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html) (Guide rapide d’installation et de configuration)

4. **Installez l’agent de ressources FCI pour SQL Server**. Exécutez les commandes suivantes sur les deux nœuds :

    ```bash
    sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server.repo
    sudo zypper --gpg-auto-import-keys refresh
    sudo zypper install mssql-server-ha
    ```

5. **Configurez automatiquement le premier nœud**. L’étape suivante consiste à configurer un cluster à un nœud en cours d’exécution en configurant le premier nœud, SLES1. Suivez les instructions de la rubrique SUSE, [Setting Up the First Node](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.1st-node) (Configuration du premier nœud).

    À la fin de la procédure, vérifiez l’état du cluster à l’aide de `crm status` :
    ```bash
    crm status
    ```

    Le résultat doit indiquer qu’un seul nœud est configuré : SLES1.

6. **Ajoutez des nœuds à un cluster existant**. Joignez ensuite le nœud SLES2 au cluster. Suivez les instructions de la rubrique SUSE, [Adding the Second Node](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.2nd-node) (Ajout du deuxième nœud).
    
    À la fin de la procédure, vérifiez l’état du cluster à l’aide de **crm status**. Si vous avez correctement ajouté le deuxième nœud, voici ce que vous obtenez en sortie :
        
    ```
    2 nodes configured
    1 resource configured
    Online: [ SLES1 SLES2 ]
    Full list of resources:
    admin_addr     (ocf::heartbeat:IPaddr2):       Started SLES1
    ```

    > [!NOTE]
    > **admin_addr** est la ressource de cluster IP virtuelle qui est configurée pendant l’installation initiale du cluster à un nœud.

7.  **Procédures de suppression**. Si vous devez supprimer un nœud du cluster, utilisez le script d’amorçage **ha-cluster-remove**. Pour plus d’informations, consultez [Overview of the Bootstrap Scripts](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.bootstrap) (Vue d’ensemble des scripts d’amorçage).  

