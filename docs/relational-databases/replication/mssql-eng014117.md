---
title: "MSSQL_ENG014117 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014117 (erreur)"
ms.assetid: e5906a76-9511-4c47-8826-8c765b58a39d
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# MSSQL_ENG014117
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14117|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|'%1!' n'est pas configuré comme base de données de distribution.|  
  
## Explication  
 Cette erreur peut se produire si une ou plusieurs des conditions suivantes sont vraies :  
  
-   L’entrée pour la base de données de distribution spécifiée est absente de **msdb... MSdistributiondbs**.  
  
-   Il n’est pas une entrée pour le serveur local dans le **master** base de données ou l’entrée il est incorrect.  
  
     La réplication requiert que tous les serveurs d'une topologie soient enregistrés avec le nom d'ordinateur et un nom d'instance facultatif (dans le cas d'une instance cluster, le nom du serveur virtuel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec le nom d'instance facultatif). Pour que la réplication fonctionne correctement, la valeur renvoyée par `SELECT @@SERVERNAME` pour chaque serveur de la topologie doit correspondre au nom d'ordinateur ou au nom de serveur virtuel avec le nom d'instance facultatif.  
  
     La réplication n'est pas prise en charge si vous avez inscrit une des instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par adresse IP ou par nom de domaine pleinement qualifié (FQDN). Si vous aviez une des instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inscrites par adresse IP ou par nom de domaine pleinement qualifié dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] quand vous avez configuré la réplication, cette erreur a pu se produire.  
  
## Action de l'utilisateur  
 Vérifiez que l'instance du serveur de distribution est inscrite correctement. Si le nom réseau de l'ordinateur et le nom de l'instance SQL Server diffèrent, effectuez une des actions suivantes :  
  
-   Ajoutez le nom de l'instance SQL Server comme nom réseau valide. Pour définir un autre nom réseau, une méthode possible consiste à l'ajouter au fichier hosts local. Le fichier hosts local est installé par défaut dans le répertoire WINDOWS\system32\drivers\etc ou WINNT\system32\drivers\etc. Pour plus d'informations, consultez la documentation Windows.  
  
     Si, par exemple, le nom d'ordinateur est comp1, l'adresse IP de l'ordinateur 10.193.17.129 et le nom de l'instance inst1/nominst, ajoutez l'entrée suivante au fichier des hôtes :  
  
     10.193.17.129 inst1  
  
-   Désactivez la distribution, inscrivez l'instance puis réactivez la distribution. Si la valeur de @@SERVERNAME n'est pas correcte pour une instance non cluster, suivez ces étapes :  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     Après avoir exécuté le [sp_addserver & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md) la procédure stockée, vous devez redémarrer le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service de la modification de @@SERVERNAME en vigueur.  
  
     Si la valeur de @@SERVERNAME n'est pas correcte pour une instance cluster, vous devez modifier le nom à l'aide de l'administrateur de cluster. Pour plus d’informations, consultez la page [les Instances de Cluster de basculement AlwaysOn & #40 ; SQL Server & #41 ;](../Topic/AlwaysOn%20Failover%20Cluster%20Instances%20\(SQL%20Server\).md).  
  
 Après avoir vérifié que l’instance de serveur de distribution est inscrit correctement, vérifiez que la base de données de distribution est répertoriée dans **msdb... MSdistributiondbs**. Si elle ne s'y trouve pas :  
  
1.  Créez un script de la configuration de la distribution. Pour plus d'informations, voir [Scripting Replication](../../relational-databases/replication/scripting-replication.md).  
  
2.  Désactivez la distribution puis réactivez-la. Pour plus d’informations, consultez [configurer la Distribution](../../relational-databases/replication/configure-distribution.md).  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  