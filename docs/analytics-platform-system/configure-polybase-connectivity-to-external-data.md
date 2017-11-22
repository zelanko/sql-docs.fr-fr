---
title: "Configurer la connectivité PolyBase pour données externes (système de plateforme Analytique)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6f14ac21-a086-4c05-861f-0a12bf278259
caps.latest.revision: "43"
ms.openlocfilehash: 7d486992f688b5bc914508ef000f23209b4bde89
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="configure-polybase-connectivity-to-external-data"></a>Configurer la connectivité PolyBase pour données externes
Explique comment configurer PolyBase dans SQL Server PDW pour se connecter à Hadoop ou Microsoft Azure storage blob sources de données externes. PolyBase permet d’exécuter des requêtes qui intègrent des données à partir de plusieurs sources, notamment Hadoop, le stockage d’objets blob Azure et SQL Server PDW.  
  
### <a name="to-configure-connectivity"></a>Pour configurer la connectivité  
  
1.  Ouvrez un outil de requête, telles que sqlcmd ou SQL Server Data Tools (SSDT) et exécutez sp_configure pour afficher les paramètres de 'connectivité hadoop' en cours.  
  
    ![paramètre de connectivité Hadoop](./media/configure-polybase-connectivity-to-external-data/APS_PDW_sp_configure.png "APS_PDW_sp_configure")  
  
2.  Décider quel paramètre, vous avez besoin et s’il faut modifier le paramètre actuel de la connectivité Hadoop. Cette option s’applique à toute la région de SQL Server PDW. Pour obtenir une liste complète des paramètres de configuration et des versions, consultez [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
3.  Pour modifier le paramètre 'connectivité hadoop', exécutez sp_configure avec RECONFIGURE. Voici quelques exemples.  
  
    ```sql  
    --Enable connectivity to Hortonworks Data Platform for Windows Server (HDP), HDInsight on Analytics Platform System, or HDInsight’s Microsoft Azure blob storage  
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
  
    En cours d’exécution sp_configure avec RECONFIGURE définit la valeur de configuration. Le redémarrage de la région est nécessaire pour définir la valeur d’exécution. Dans la mesure où un redémarrage est nécessaire après l’arrêt suivant également, vous n’avez pas besoin effectuer le redémarrage jusqu'à ce que l’étape suivante, ce qui modifie core-site.Xml.  
  
4.  Pour activer le stockage d’objets blob Microsoft Azure en tant que source de données externe, ajoutez une ou plusieurs clés d’accès de compte de stockage Microsoft Azure au fichier de base-site.XML PDW. Pour ajouter une clé :  
  
    1.  Rechercher le nom de votre compte de stockage Microsoft Azure. Pour afficher vos comptes de stockage, le nom de connexion à la[portail Azure](https://portal.azure.com) et cliquez sur **comptes de stockage (classiques)**.  
  
        ![Nom de compte de stockage Windows Azure](./media/configure-polybase-connectivity-to-external-data/APS_PDW_AzureStorageAccountName.png "APS_PDW_AzureStorageAccountName")  
  
    2.  Trouver votre clé d’accès de compte stockage Azure. Pour ce faire, cliquez sur le nom de votre compte de stockage, puis dans le panneau paramètres **clés**. Cette opération affiche vos clés de stockage et le nom du compte.  
  
        ![Clés de l’accès du compte de stockage Windows Azure](./media/configure-polybase-connectivity-to-external-data/APS_PDW_AzureStorageAccountAccessKey.png "APS_PDW_AzureStorageAccountAccessKey")  
  
    3.  Ouvrez une connexion Bureau à distance au nœud de contrôle de PDW.  
  
    4.  Ouvrez le fichier C:\Program Files\Microsoft SQL Server Parallel données Warehouse\100\Hadoop\conf\core-site.xml.  
  
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
        > Prendre des précautions de sécurité avant de stocker la clé d’accès dans core-site.Xml. Tout utilisateur qui possède l’autorisation CONTROL SERVER ou ALTER ANY EXTERNAL DATA SOURCE peut créer une source de données externe qui accède à ce compte. Une fois la source de données externe est créée, tous les utilisateurs de SQL Server PDW qui sont autorisés à créer des tables peuvent créer une table externe qui accède à ce compte de stockage. Les utilisateurs seront alors en mesure d’accéder aux données de compte et consomment des ressources dans le compte.  
  
    6.  Enregistrez les modifications dans core-site.Xml.  
  
5.  Ajoutez yarn.application.classpath et des valeurs dans le fichier yarn-site.Xml.  
  
    Ignorez cette étape si vous vous connectez à un 1.3 Hadoop externe.  
  
    À partir de Hadoop 2.0, le fichier yarn-site.XML contient des paramètres de configuration de l’infrastructure des fils de Hadoop. Ce fichier se trouve sur le nœud de contrôle sous **C:\program files\Microsoft SQL Server Parallel données Warehouse\100\Hadoop\conf\\**.  
  
    Pour exécuter des requêtes PolyBase par rapport à un Cluster de 2.0 externe Hadoop sur Windows ou Linux, vous devez configurer les yarn.application.classpath propriété et les valeurs pour être cohérent avec les paramètres yarn-site.XML sur votre Hadoop Cluster externe. Cette configuration est nécessaire même si votre Hadoop Cluster externe utilise les paramètres par défaut.  
  
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
  
    Une fois que n’importe quelle propriété est définie dans yarn-site.XML, PolyBase utilisera ces paramètres de propriété lors de l’exécution des requêtes par rapport à la HDInsight région. Si vous projetez d’exécuter des requêtes PolyBase sur la HDInsight région et sur un Cluster de 2.0 externe Hadoop sur Windows, il doit y avoir une cohérence entre tous les fichiers yarn-site.XML, sinon les requêtes PolyBase échoue.  
  
    Pour exécuter PolyBase sur la HDInsight région et un Cluster de 2.0 Hadoop externe, utilisez les paramètres par défaut d’yarn-site.XML sur votre Hadoop Cluster externe.  
  
6.  Redémarrer la région PDW. Pour ce faire, utilisez l’outil de Configuration Manager. Consultez [lance le Gestionnaire de Configuration &#40; Système de plateforme Analytique &#41; ](launch-the-configuration-manager.md).  
  
7.  Vérifiez les paramètres de sécurité pour les connexions Hadoop. Si le **d’authentification faible** sur Hadoop côté est activée à l’aide de `dfs.permission = true`, vous devez créer un utilisateur Hadoop **pdw_user** et accorder complet en lecture et en écriture à cet utilisateur. SQL Server PDW et appels correspondants à partir de SQL Server PDW sont toujours émis en tant que **pdw_user** qui est un nom d’utilisateur fixe et ne peut pas être modifié dans cette version de la connectivité Hadoop et la version de SQL Server PDW. Si la sécurité sur Hadoop est désactivée à l’aide de `dfs.permission = false`, alors aucune autre action ne doivent être exécutées.  
  
8.  Décidez quels utilisateurs peuvent créer une source de données externe pour le stockage d’objets blob Microsoft Azure. Chacun de ces utilisateurs donner le nom de compte de stockage et également **ALTER ANY EXTERNAL DATA SOURCE** ou **CONTROL SERVER** autorisation.  
  
9. Pour les connexions Hadoop, décidez quels utilisateurs peuvent créer une source de données externes pour Hadoop. Donnez à chacun de ces utilisateurs l’adresse IP et port numéro de chaque nœud de nom Hadoop et leur donner **ALTER ANY EXTERNAL DATA SOURCE** ou **CONTROL SERVER** autorisation.  
  
10. La connexion à WASB nécessite également de transfert DNS à configurer sur l’appareil. Pour configurer le transfert de DNS, consultez [utiliser un redirecteur DNS pour résoudre les noms DNS Non Appliance &#40; Système de plateforme Analytique &#41; ](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
Les utilisateurs autorisés peuvent maintenant créer des sources de données externes, les formats de fichiers externes et des tables externes. Ils peuvent utiliser ces pour intégrer des données provenant de plusieurs sources, notamment Hadoop, stockage d’objets blob Microsoft Azure et SQL Server PDW.  
  
## <a name="see-also"></a>Voir aussi  
[Configuration du matériel &#40; Système de plateforme Analytique &#41;](appliance-configuration.md)  
<!-- MISSING LINKS [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  -->  
  
