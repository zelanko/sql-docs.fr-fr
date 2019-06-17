---
title: Conditions requises pour l’utilisation des tables optimisées en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 47d9a7e8-c597-4b95-a58a-dcf66df8e572
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 9b9e442fb97245d32c398602cdfd727de8239cb8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62467891"
---
# <a name="requirements-for-using-memory-optimized-tables"></a>Conditions requises pour l'utilisation des tables optimisées en mémoire
  Outre le [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md), voici la configuration requise pour utiliser OLTP en mémoire :  
  
-   Édition 64 bits Enterprise, Developer ou Evaluation de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessite une quantité de mémoire suffisante pour contenir les données des tables et des index optimisés en mémoire. Pour prendre en compte les versions de ligne, vous devez disposer d'une quantité de mémoire deux fois plus importante que la taille prévue pour les tables et les index optimisés en mémoire. Mais le volume réel de mémoire nécessaire dépendra de votre charge de travail. Vous devez surveiller votre utilisation de la mémoire et l'ajuster selon vos besoins. La taille des données dans les tables optimisées en mémoire ne doit pas dépasser le pourcentage autorisé pour le pool. Pour découvrir la taille d’une table optimisée en mémoire, consultez [sys.dm_db_xtp_table_memory_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql).  
  
     Si la base de données contient des tables sur disque, vous devez prévoir suffisamment de mémoire pour le pool de mémoires tampons et le traitement des requêtes sur ces tables.  
  
     Il est important de déterminer la quantité de mémoire requise par votre application OLTP en mémoire. Pour plus d’informations, consultez [Estimer les besoins en mémoire des tables mémoire optimisées](memory-optimized-tables.md) .  
  
-   L'espace disque disponible doit correspondre au double de la taille de vos tables optimisées en mémoire durables.  
  
-   Un processeur doit prendre en charge l'instruction **cmpxchg16b** pour utiliser l'OLTP en mémoire. Tous les processeurs 64 bits actuels prennent en charge **cmpxchg16b**.  
  
     Si vous utilisez une application hôte de machine virtuelle et que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche une erreur provoquée par un processeur plus ancien, vérifiez si l'application dispose d'une option de configuration permettant d'autoriser **cmpxchg16b**. Si ce n'est pas le cas, vous pouvez utiliser Hyper-V, qui prend en charge **cmpxchg16b** sans avoir à modifier une option de configuration.  
  
-   Pour installer l'OLTP en mémoire, sélectionnez **Services Moteur de base de données** lorsque vous installez [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
     Pour installer la création de rapports ([déterminer si une Table ou une procédure stockée doit être déplacée vers In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) et [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] (pour gérer l’OLTP en mémoire via [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Explorateur d’objets), sélectionnez **gestion Outils-Basic** ou **outils de gestion avancés** lorsque vous installez [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
## <a name="important-notes-on-using-includehek2includeshek-2-mdmd"></a>Notes importantes lors de l'utilisation de l' [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]  
  
-   La taille totale en mémoire des tables durables dans une base de données ne doit pas dépasser 250 Go. Pour plus d’informations, consultez [durabilité pour les Tables optimisées en mémoire](durability-for-memory-optimized-tables.md).  
  
-   Cette version de l' [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] cible des systèmes avec 2 ou 4 sockets et moins de 60 cœurs.  
  
-   Les fichiers de point de contrôle ne doivent pas être supprimés manuellement. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue automatiquement l'opération de garbage collection sur les fichiers de point de contrôle inutiles. Pour plus d’informations, consultez la discussion sur la fusion des fichiers de données et delta dans [durabilité pour les Tables optimisées en mémoire](durability-for-memory-optimized-tables.md).  
  
-   Dans cette première version de l'OLTP en mémoire (dans [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]), la seule façon de supprimer un groupe de fichiers optimisé en mémoire consiste à supprimer la base de données.  
  
-   Si vous tentez de supprimer une large plage de lignes qui fait simultanément l'objet d'une charge de travail d'insertion ou de mise à jour, la suppression échouera probablement. Pour éviter ce problème, vous devez arrêter la charge de travail d'insertion ou de mise à jour avant d'effectuer la suppression. Sinon, vous pouvez aussi décomposer la transaction en transactions plus petites, qui sont moins susceptibles d'être perturbées par une charge de travail simultanée. Comme avec toutes les opérations d'écriture sur les tables optimisées en mémoire, utilisez la logique de nouvelle tentative ([Guidelines for Retry Logic for Transactions on Memory-Optimized Tables](../../database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)).  
  
-   Si vous créez une ou plusieurs bases de données avec des tables optimisées en mémoire, vous devez activer l'initialisation instantanée de fichiers (accordez au compte de démarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le droit de l'utilisateur SE_MANAGE_VOLUME_NAME) pour l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Faute d'initialisation instantanée, les fichiers de stockage optimisés en mémoire (fichiers de données et delta) seront initialisés à la création, ce qui peut avoir un impact négatif sur les performances de votre charge de travail. Pour plus d'informations sur l'initialisation instantanée de fichiers, consultez [Initialisation des fichiers de base de données](../databases/database-instant-file-initialization.md). Pour plus d'informations sur la façon d'activer l'initialisation instantanée de fichiers, consultez [Comment et pourquoi activer l'initialisation instantanée de fichiers](https://blogs.msdn.com/b/sql_pfe_blog/archive/2009/12/23/how-and-why-to-enable-instant-file-initialization.aspx).  
  
## <a name="did-this-article-help-you-were-listening"></a>Cet article vous a-t-il été utile ? Nous sommes à votre écoute  
 Quels renseignements souhaitez-vous obtenir ? Avez-vous trouvé ce que vous cherchiez ? Nous sommes à l’écoute de vos commentaires pour améliorer le contenu. Veuillez envoyer vos commentaires à l’adresse suivante : [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Requirements%20for%20Using%20Memory-Optimized%20Tables%20page).  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](in-memory-oltp-in-memory-optimization.md)  
  
  
