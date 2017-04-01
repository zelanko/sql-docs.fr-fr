---
title: "Configuration de PolyBase | Microsoft Docs"
ms.custom: ""
ms.date: "11/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80ff73c1-2861-438b-a13f-309155f3d6e1
caps.latest.revision: 17
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 12
---
# Configuration de PolyBase
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Utilisez les procédures ci-dessous pour configurer PolyBase.  
  
## <a name="external-data-source-configuration"></a>Configuration de source de données externes  
 Assurez-vous que SQL Server est bien connecté à la source de données externes. Le type de connectivité a une grande influence sur les performances de requête. Par exemple, une liaison Ethernet 10 Gbit offre un temps de réponse aux requêtes PolyBase plus rapide qu’une liaison Ethernet 1 Gbit.  
  
 Vous devez configurer SQL Server pour qu’il se connecte à votre version de Hadoop ou à Azure Blob Storage à l’aide de **sp_configure**. PolyBase prend en charge deux distributions Hadoop : Hortonworks Data Platform (HDP) et Cloudera Distributed Hadoop (CDH).  Pour obtenir une liste complète des sources de données externes prises en charge, consultez [PolyBase Connectivity Configuration &#40;Transact-SQL&#41;](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md) (Configuration de la connectivité PolyBase).  
  
### <a name="run-spconfigure"></a>Exécuter sp_configure  
  
1.  Exécutez sp_configure « connexion à hadoop » et définissez une valeur appropriée.  Pour trouver la valeur, consultez [PolyBase Connectivity Configuration &#40;Transact-SQL&#41;](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md) (Configuration de la connectivité PolyBase).  
  
    ```tsql  
    -- Values map to various external data sources.  
    -- Example: value 7 stands for Azure blob storage and Hortonworks HDP 2.3 on Linux.  
    sp_configure @configname = 'hadoop connectivity', @configvalue = 7;   
    GO   
  
    RECONFIGURE   
    GO   
    ```  
  
2.  Vous devez redémarrer SQL Server à l’aide de **services.msc**. Le redémarrage de SQL Server redémarre ces services :  
  
    -   Service de déplacement des données SQL Server PolyBase  
  
    -   Moteur SQL Server PolyBase  
  
## <a name="pushdown-configuration"></a>Configuration de la poussée vers le bas  
 Pour améliorer les performances des requêtes, activez le calcul de poussée vers le bas sur un cluster Hadoop :  
  
1.  Recherchez le fichier **yarn-site.XML** dans le chemin d’installation de SQL Server. En règle générale, le chemin d’accès est le suivant :  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf  
    ```  
  
2.  Sur l’ordinateur Hadoop, recherchez le fichier analogue dans le répertoire de configuration Hadoop. Dans le fichier, recherchez et copiez la valeur de la clé de configuration yarn.application.classpath.  
  
3.  Sur l’ordinateur SQL Server, dans le **fichier yarn.site.xml** , recherchez la propriété **yarn.application.classpath** . Collez la valeur de l’ordinateur Hadoop dans l’élément de valeur.  
  
## <a name="kerberos-configuration"></a>Configuration de Kerberos  
 Pour vous connecter à un cluster Hadoop sécurisé Kerberos [à l’aide de MIT KDC] :  
  
1.  Recherchez le répertoire de configuration Hadoop dans le chemin d’installation de SQL Server. En règle générale, le chemin d’accès est le suivant :  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf  
    ```  
  
2.  Recherchez la valeur de configuration côté Hadoop des clés de configuration répertoriées dans le tableau. Sur l’ordinateur Hadoop, recherchez les fichiers dans le répertoire de configuration Hadoop.  
  
3.  Copiez les valeurs de configuration dans la propriété de valeur dans les fichiers correspondants sur l’ordinateur SQL Server.  
  
    |**#**|**Fichier de configuration**|**Clé de configuration**|**Action**|  
    |------------|----------------|---------------------|----------|   
    | 1|core-site.xml|polybase.kerberos.kdchost|Spécifiez le domaine Kerberos. Par exemple : VOTRE-DOMAINE.COM|  
    |2|core-site.xml|polybase.kerberos.realm|Spécifiez le nom d’hôte KDC. Par exemple : kerberos.votre-domaine.com.|  
    |3|core-site.xml|hadoop.security.authentication|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : KERBEROS<br></br>**Note de sécurité :** KERBEROS doit être écrit en majuscules. Dans le cas contraire, il pourrait ne pas être activé.|   
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : hdfs/_HOST@YOUR-REALM.COM|  
    |5|mapred-site.xml|mapreduce.jobhistory.address|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : mapred/_HOST@YOUR-REALM.COM|  
    |6|mapred-site.xml|mapreduce.jobhistory.principal|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : 10.193.26.174:10020|  
    |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : yarn/_HOST@YOUR-REALM.COM|  
  
4.  Créez un objet d’informations d’identification limité à la base de données pour spécifier les informations d’authentification de chaque utilisateur Hadoop. Consultez [Objets T-SQL PolyBase](../../relational-databases/polybase/polybase-t-sql-objects.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Objets T-SQL PolyBase](../../relational-databases/polybase/polybase-t-sql-objects.md)  
  
 [Bien démarrer avec PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de la connectivité PolyBase &#40;Transact-SQL&#41;](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)   
 [Guide de PolyBase](../../relational-databases/polybase/polybase-guide.md)  
  
  