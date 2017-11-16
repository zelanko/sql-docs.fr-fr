---
title: "Conditions requises pour l’utilisation des tables optimisées en mémoire | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47d9a7e8-c597-4b95-a58a-dcf66df8e572
caps.latest.revision: 65
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d30c5b808c13258e784187182eab23b0a50c76e0
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="requirements-for-using-memory-optimized-tables"></a>Conditions requises pour l'utilisation des tables optimisées en mémoire
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Pour savoir comment utiliser la fonction OLTP en mémoire dans la base de données Azure, consultez [Prise en main de In-Memory (version préliminaire) dans la base de données SQL](http://azure.microsoft.com/documentation/articles/sql-database-in-memory/).  
  
 En plus des [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md), voici les conditions d’utilisation de la fonction OLTP en mémoire :  
  
-   SQL Server 2016 SP1 (ou version ultérieure), n’importe quelle édition. Pour SQL Server 2014 et SQL Server 2016 RTM (antérieure àSP1), vous avez besoin de l’édition Enterprise, Developer ou Evaluation.
    - Remarque : L’OLTP en mémoire nécessite la version 64 bits de SQL Server.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessite une quantité de mémoire suffisante pour contenir les données des tables et des index optimisés en mémoire, ainsi qu’une quantité de mémoire supplémentaire pour gérer la charge de travail en ligne. Pour plus d’informations, consultez [Estimer les besoins en mémoire des tables optimisées en mémoire](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md) .  

-   Lors de l’exécution de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans une machine virtuelle, vérifiez qu’une quantité de mémoire suffisante est allouée à la machine virtuelle pour prendre en charge la mémoire nécessaire pour les tables et index optimisés en mémoire. Selon l’application hôte de la machine virtuelle, l’option de configuration pour garantir l’allocation de mémoire pour la machine virtuelle peut être appelée réserve de mémoire ou, lors de l’utilisation de mémoire dynamique, RAM minimale. Vérifiez que ces paramètres sont suffisants pour les besoins des bases de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
-   Espace disque disponible correspondant au double de la taille de vos tables optimisées en mémoire durables.  
  
-   Un processeur doit prendre en charge l’instruction **cmpxchg16b** pour pouvoir utiliser la fonction OLTP en mémoire. Tous les processeurs 64 bits modernes prennent en charge l’instruction **cmpxchg16b**.  
  
     Si vous utilisez une machine virtuelle et que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche une erreur provoquée par un processeur plus ancien, vérifiez si l’application hôte de la machine virtuelle dispose d’une option de configuration pour autoriser **cmpxchg16b**. Si ce n’est pas le cas, vous pouvez utiliser Hyper-V, qui prend en charge l’instruction **cmpxchg16b** sans qu’il ne soit nécessaire de modifier une option de configuration.  
  
-   OLTP en mémoire est installé dans le cadre des **Services Moteur de base de données**.  
  
     Pour installer la création de rapports ([Déterminer si une table ou une procédure stockée doit être déplacée vers l’OLTP en mémoire](../../relational-databases/in-memory-oltp/determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) et [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (pour gérer l’OLTP en mémoire via l’Explorateur d’objets [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ), [Télécharger SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx).   
  
## <a name="important-notes-on-using-includehek2includeshek-2-mdmd"></a>Notes importantes lors de l'utilisation de l' [!INCLUDE[hek_2](../../includes/hek-2-md.md)]  
  
-   Depuis SQL Server 2016, il n’existe aucune limite de la taille des tables optimisées en mémoire, autre que la mémoire disponible. Dans SQL Server 2014, la taille totale en mémoire de toutes les tables durables dans une base de données ne devait pas dépasser 250 Go pour les bases de données SQL Server 2014. Pour plus d’informations, consultez [Estimer les besoins en mémoire des tables optimisées en mémoire](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md).  
    - Remarque : À compter de SQL Server 2016 SP1, les éditions Standard et Express prennent en charge l’OLTP en mémoire, mais elles imposent des quotas sur la quantité de mémoire que vous pouvez utiliser pour les tables optimisées en mémoire dans une base de données. Dans l’édition Standard, ce quota est de 32 Go par base de données ; dans l’édition Express, il est de 352 Mo par base de données. 
  
-   Si vous créez une ou plusieurs bases de données avec des tables optimisées en mémoire, vous devez activer l'initialisation instantanée de fichiers (accordez au compte de démarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le droit de l'utilisateur SE_MANAGE_VOLUME_NAME) pour l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Faute d'initialisation instantanée, les fichiers de stockage optimisés en mémoire (fichiers de données et delta) seront initialisés à la création, ce qui peut avoir un impact négatif sur les performances de votre charge de travail. Pour plus d'informations sur l'initialisation instantanée de fichiers, consultez [Initialisation des fichiers de base de données](http://msdn.microsoft.com/library/ms175935\(SQL.105\).aspx). Pour plus d'informations sur la façon d'activer l'initialisation instantanée de fichiers, consultez [Comment et pourquoi activer l'initialisation instantanée de fichiers](http://blogs.msdn.com/b/sql_pfe_blog/archive/2009/12/23/how-and-why-to-enable-instant-file-initialization.aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  

