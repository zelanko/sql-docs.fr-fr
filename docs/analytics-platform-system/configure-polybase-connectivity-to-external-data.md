---
title: Configurer la connectivité PolyBase - Analytique Platform System | Microsoft Docs
description: Explique comment configurer PolyBase dans Parallel Data Warehouse pour se connecter à Hadoop ou Microsoft Azure storage blob sources de données externes. Utilisez PolyBase pour exécuter des requêtes qui intègrent des données provenant de plusieurs sources, dont Hadoop, stockage blob Azure et Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 26eeffb1d2a27ee49f01114b015ab4051b145d64
ms.sourcegitcommit: 731c5aed039607a8df34c63e780d23a8fac937e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909869"
---
# <a name="configure-polybase-connectivity-to-external-data"></a>Configurer la connectivité de PolyBase pour données externes
Explique comment configurer PolyBase dans Parallel Data Warehouse pour se connecter à Hadoop ou Microsoft Azure storage blob sources de données externes. Utilisez PolyBase pour exécuter des requêtes qui intègrent des données provenant de plusieurs sources, dont Hadoop, stockage blob Azure et Parallel Data Warehouse.  
  
### <a name="to-configure-connectivity"></a>Pour configurer la connectivité  
  
1.  Ouvrez un outil de requête, tels que sqlcmd ou SQL Server Data Tools (SSDT) et exécutez sp_configure pour afficher les paramètres de 'connectivité hadoop' en cours.  
  
    ![paramètre de connectivité Hadoop](./media/configure-polybase-connectivity-to-external-data/APS_PDW_sp_configure.png "APS_PDW_sp_configure")  
  
2.  Décider lequel paramètre nécessaire et s’il faut modifier le paramètre actuel de la connectivité Hadoop. Cette option s’applique à la région entière de SQL Server PDW. Pour obtenir une liste complète des paramètres de configuration et des versions, consultez [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
3.  Pour modifier le paramètre 'connectivité hadoop', exécutez sp_configure avec l’instruction RECONFIGURE. Voici quelques exemples.  
  
    ```sql  
    --Enable connectivity to Hortonworks Data Platform for Windows Server (HDP) or HDInsight’s Microsoft Azure blob storage  
    EXEC sp_configure 'hadoop connectivity', 4;   
    RECONFIGURE;  
  
    -- Enable connectivity to Hortonworks Data Platform (HDP)for Linux   
    EXEC sp_configure 'hadoop connectivity', 5;   
    RECONFIGURE;  
  
    -- Enable connectivity to Cloudera CDH for Linux   
    EXEC sp_configure 'hadoop connectivity', 3;   
    RECONFIGURE;  
  
    -- Disable the Hadoop connectivity option   
    EXEC sp_configure 'hadoop connectivity', 0;  
    RECONFIGURE;  
    ```  
  
    En cours d’exécution sp_configure avec RECONFIGURE définit la valeur de configuration. Le redémarrage de la région est nécessaire pour définir la valeur d’exécution. Dans la mesure où un redémarrage est nécessaire après l’arrêt suivant également, vous n’avez pas besoin de faire le redémarrage jusqu'à ce que l’étape suivante, ce qui modifie core-site.Xml.  
  
4.  Pour activer le stockage d’objets blob Microsoft Azure en tant que source de données externe, ajoutez un ou plusieurs clés d’accès de compte de stockage Microsoft Azure pour le fichier core-site.XML PDW. Pour ajouter une clé :  
  
    1.  Rechercher le nom de votre compte de stockage Microsoft Azure. Pour afficher vos comptes de stockage, connectez-vous à la[Azure portal](https://portal.azure.com) et cliquez sur **comptes de stockage (classiques)**.  
  
        ![Nom de compte de stockage Windows Azure](./media/configure-polybase-connectivity-to-external-data/APS_PDW_AzureStorageAccountName.png "APS_PDW_AzureStorageAccountName")  
  
    2.  Trouver votre clé d’accès de compte stockage Azure. Pour ce faire, cliquez sur le nom de votre compte de stockage, puis dans le panneau paramètres **clés**. Cela vous montre les clés de stockage et le nom de votre compte.  
  
        ![Accéder aux clés de stockage Windows Azure](./media/configure-polybase-connectivity-to-external-data/APS_PDW_AzureStorageAccountAccessKey.png "APS_PDW_AzureStorageAccountAccessKey")  
  
    3.  Ouvrez une connexion Bureau à distance au nœud de contrôle de PDW.  
  
    4.  Ouvrez le fichier C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\core-site.xml.  
  
    5.  Ajoutez la propriété suivante avec des attributs de nom et la valeur à core-site.Xml.  
  
        ```xml  
        <property>  
          <name>fs.azure.account.key.<your storage account name>.blob.core.windows.net</name>  
          <value><your storage account access key></value>  
        </property>  
        ```  
  
        Cet exemple utilise la clé d’accès et le nom compte indiquée précédemment.  
  
        ```xml  
        <property>  
          <name>fs.azure.account.key.CustomerX.blob.core.windows.net</name>  
          <value>yyeTfCxxxxxxxxQ5WdnapXw77W+FwzHUhX/p/f26fIpnNFGtewzyRN90e1/qmTOl1xxxxxxxxa0goG71LsNcw==</value>  
        </property>  
        ```  
  
        > [!CAUTION]  
        > Prenez des précautions de sécurité avant de stocker la clé d’accès dans core-site.Xml. Tout utilisateur qui possède l’autorisation CONTROL SERVER ou ALTER ANY EXTERNAL DATA SOURCE peut créer une source de données externe qui accède à ce compte. Une fois la source de données externe est créée, tous les utilisateurs de SQL Server PDW avec des autorisations CREATE TABLE peuvent créer une table externe qui accède à ce compte de stockage. Les utilisateurs peuvent ensuite accéder aux données de compte et consomment des ressources dans le compte.  
  
    6.  Enregistrez les modifications dans core-site.Xml.  
  
5.  Ajoutez yarn.application.classpath valeurs de propriété et au fichier yarn-site.Xml.  
  
    Ignorez cette étape si vous vous connectez à un 1.3 Hadoop externe.  
  
    À partir de Hadoop 2.0, le fichier d’yarn-site.XML contient des paramètres de configuration pour le framework de Hadoop YARN. Ce fichier se trouve sur le nœud de contrôle sous **C:\program files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\\**.  
  
    Pour exécuter des requêtes PolyBase sur un Cluster de 2.0 Hadoop externe sur Windows ou Linux, vous devez configurer la propriété de yarn.application.classpath et les valeurs pour être cohérent avec les paramètres d’yarn-site.XML sur votre Hadoop Cluster externe. Cette configuration est nécessaire même si votre Hadoop Cluster externe utilise les paramètres par défaut.  
  
    Exemple de paramètres par défaut :  
  
    ```xml  
    <property>  
        <name>yarn.application.classpath</name>  
        <value>  
          %HADOOP_CONF_DIR%,  
          %HADOOP_COMMON_HOME%/share/hadoop/common/*,  
          %HADOOP_COMMON_HOME%/share/hadoop/common/lib/*,  
          %HADOOP_HDFS_HOME%/share/hadoop/hdfs/*,  
          %HADOOP_HDFS_HOME%/share/hadoop/hdfs/lib/*,  
          %HADOOP_YARN_HOME%/share/hadoop/yarn/*,  
          %HADOOP_YARN_HOME%/share/hadoop/yarn/lib/*  
         </value>  
      </property>  
    ```  
  
    Une fois que n’importe quelle propriété est définie dans yarn-site.XML, PolyBase utilise ces paramètres de propriété quand il exécute des requêtes sur la Hadoop. Si vous projetez d’exécuter des requêtes PolyBase sur l’objet Blob de stockage Azure et un Cluster de 2.0 externe Hadoop sur Windows, il doit y avoir de la cohérence entre tous les fichiers yarn-site.XML, sans quoi les requêtes PolyBase échoue.  
   
6.  Redémarrez la région PDW. Pour ce faire, utilisez l’outil de Configuration Manager. Consultez [lancer le Gestionnaire de Configuration &#40;Analytique Platform System&#41;](launch-the-configuration-manager.md).  
  
7.  Vérifiez les paramètres de sécurité pour les connexions de Hadoop. Si le **une authentification faible** sur Hadoop côté est activée à l’aide de `dfs.permission = true`, vous devez créer un utilisateur Hadoop **pdw_user** et accorder lecture totale et les autorisations en écriture à cet utilisateur. SQL Server PDW et les appels correspondants à partir de SQL Server PDW sont toujours émis en tant que **pdw_user**.  Ceci est un nom d’utilisateur fixe et ne peut pas être modifié dans cette version de la connectivité Hadoop et la version de SQL Server PDW. Si la sécurité sur Hadoop est désactivée à l’aide de `dfs.permission = false`, puis, aucune action supplémentaire ne doit être effectuées.  
  
8.  Décidez quels utilisateurs peuvent créer une source de données externe pour le stockage d’objets blob Microsoft Azure. Chacun de ces utilisateurs donner le nom de compte de stockage et également **ALTER ANY EXTERNAL DATA SOURCE** ou **CONTROL SERVER** autorisation.  
  
9. Pour les connexions de Hadoop, décidez quels utilisateurs peuvent créer une source de données externe à Hadoop. Donnez à chacun de ces utilisateurs l’adresse IP et port numéro de chaque nœud de nom Hadoop et leur donner **ALTER ANY EXTERNAL DATA SOURCE** ou **CONTROL SERVER** autorisation.  
  
10. La connexion à WASB nécessite également le transfert DNS pour être configuré sur l’appliance. Pour configurer la redirection DNS, consultez [utiliser un redirecteur DNS pour résoudre les noms DNS Non-Appliance &#40;Analytique Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
Les utilisateurs autorisés peuvent maintenant créer des sources de données externes, les formats de fichier externe et les tables externes. Ils peuvent les utiliser pour intégrer des données provenant de plusieurs sources, notamment Hadoop, stockage d’objets blob Microsoft Azure et SQL Server PDW.  

## <a name="kerberos-configuration"></a>Configuration de Kerberos  
Notez que lorsque PolyBase s’authentifie auprès d’un cluster sécurisé Kerberos, le paramètre hadoop.rpc.protection doit être défini à l’authentification. De cette façon, la communication de données entre les nœuds Hadoop n’est pas chiffrée. 

 Pour vous connecter à un cluster Hadoop sécurisé Kerberos [à l’aide de MIT KDC] :
   
  
1.  Rechercher le répertoire de configuration Hadoop dans le chemin d’installation sur le nœud de contrôle :  
  
    ```  
    C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf
    ```  
  
2.  Recherchez la valeur de configuration côté Hadoop des clés de configuration répertoriées dans le tableau. Sur l’ordinateur Hadoop, recherchez les fichiers dans le répertoire de configuration Hadoop.  
  
3.  Copiez les valeurs de configuration dans la propriété de valeur dans les fichiers correspondants sur le nœud de contrôle.  
  
    |**#**|**Fichier de configuration**|**Clé de configuration**|**Action**|  
    |------------|----------------|---------------------|----------|   
    | 1|core-site.xml|polybase.kerberos.kdchost|Spécifiez le nom d’hôte KDC. Par exemple : kerberos.votre-domaine.com.|  
    |2|core-site.xml|polybase.kerberos.realm|Spécifiez le domaine Kerberos. Par exemple : VOTRE-DOMAINE.COM|  
    |3|core-site.xml|hadoop.security.authentication|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : KERBEROS<br></br>**Note de sécurité :** KERBEROS doit être écrit en majuscules. Dans le cas contraire, il pourrait ne pas être activé.|   
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : hdfs/_HOST@YOUR-REALM.COM|  
    |5|mapred-site.xml|mapreduce.jobhistory.principal|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : mapred/_HOST@YOUR-REALM.COM|  
    |6|mapred-site.xml|mapreduce.jobhistory.address|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : 10.193.26.174:10020|  
    |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : yarn/_HOST@YOUR-REALM.COM|  
  
4. Créez un objet d’informations d’identification limité à la base de données pour spécifier les informations d’authentification de chaque utilisateur Hadoop. Consultez [Objets T-SQL PolyBase](../relational-databases/polybase/polybase-t-sql-objects.md).  

5. Redémarrez la région PDW. Pour ce faire, utilisez l’outil de Configuration Manager. Consultez [lancer le Gestionnaire de Configuration &#40;Analytique Platform System&#41;](launch-the-configuration-manager.md).
 
## <a name="see-also"></a>Voir aussi  
[Configuration de l’appliance &#40;Analytique Platform System&#41;](appliance-configuration.md)  
<!-- MISSING LINKS [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  -->  
  
