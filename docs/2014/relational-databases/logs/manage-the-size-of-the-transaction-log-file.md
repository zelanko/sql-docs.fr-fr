---
title: Gérer la taille du fichier journal des transactions | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- transaction logs [SQL Server], size management
ms.assetid: 3a70e606-303f-47a8-96d4-2456a18d4297
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b2ebcd653adebed5541b1d2cdf814f638d0af683
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52816611"
---
# <a name="manage-the-size-of-the-transaction-log-file"></a>Gérer la taille du fichier journal des transactions
  Dans certains cas, il peut être utile de réduire ou développer physiquement le fichier journal physique du journal des transactions d'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cette rubrique contient des informations sur la façon de contrôler la taille d'un journal des transactions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , réduire le journal des transactions, ajouter ou agrandir un fichier journal de transactions, optimiser le taux de croissance du journal des transactions **tempdb** et contrôler la croissance d'un fichier journal de transactions.  
  
  
##  <a name="MonitorSpaceUse"></a> Contrôler l’utilisation d’espace journal  
 Vous pouvez contrôler l'espace occupé par le journal à l'aide de DBCC SQLPERF(LOGSPACE). Cette commande retourne des informations sur la quantité d'espace journal actuellement utilisée et indique à quel moment le journal des transactions a besoin d'être tronqué. Pour plus d’informations, consultez [DBCC SQLPERF &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql). Pour plus d’informations sur la taille actuelle d’un fichier journal, sa taille maximale et l’option de croissance automatique du fichier, vous pouvez également utiliser les colonnes **size**, **max_size** et **growth** pour ce fichier journal dans **sys.database_files**. Pour plus d’informations, consultez [sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql).  
  
> [!IMPORTANT]  
>  Nous vous recommandons d'éviter de surcharger le disque du journal.  
  
  
##  <a name="ShrinkSize"></a> Réduire la taille du fichier journal  
 Pour réduire la taille physique d'un fichier journal physique, vous devez réduire le fichier journal. Cela est utile si vous savez qu'un fichier journal de transactions contient de l'espace inutilisé dont vous n'avez pas besoin. La réduction d'un fichier journal ne peut avoir lieu que lorsque la base de données est en ligne et, également, lorsqu'au moins un fichier journal virtuel est libre. Dans certains cas, la réduction du journal peut n'être possible qu'après la troncation de journal suivante.  
  
> [!NOTE]  
>  Certains facteurs (par exemple, une transaction longue) chargés de maintenir les fichiers journaux virtuels actifs pendant une période de temps prolongée peuvent limiter, voire empêcher, la réduction du journal. Pour plus d’informations sur les facteurs susceptibles de retarder la troncation du journal, consultez [Journal des transactions &#40;SQL Server&#41;](the-transaction-log-sql-server.md).  
  
 La réduction d'un fichier journal supprime un ou plusieurs fichiers journaux virtuels qui ne contiennent aucune partie du journal logique (autrement dit, des *fichiers journaux virtuels inactifs*). Lorsque vous réduisez un fichier journal de transactions, un nombre suffisant de fichiers journaux virtuels inactifs sont supprimés à la fin du fichier journal afin de réduire le journal et le ramener à une taille proche de la taille cible.  
  
 **Pour réduire un fichier journal (sans réduire les fichiers de base de données)**  
  
-   [DBCC SHRINKFILE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql)  
  
-   [Réduire un fichier](../databases/shrink-a-file.md)  
  
 **Pour surveiller les événements de réduction du fichier journal**  
  
-   [Log File Auto Shrink Event Class](../event-classes/log-file-auto-shrink-event-class.md).  
  
 `To monitor log space`  
  
-   [DBCC SQLPERF &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql)  
  
-   [sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) (consultez les colonnes **size**, **max_size** et **growth** du ou des fichiers journaux.)  
  
> [!NOTE]  
>  Il est possible de définir une réduction automatique des fichiers de la base de données et des fichiers journaux. Toutefois, nous vous déconseillons la réduction automatique, et la propriété de base de données `autoshrink` est définie par défaut par la valeur FALSE. Si `autoshrink` est définie par la valeur TRUE, la troncation automatique réduit la taille d'un fichier uniquement lorsque plus de 25 pour cent de son espace est inutilisé. Le fichier est réduit soit à la taille à laquelle seuls 25 % de ce dernier sont inutilisés soit à sa taille d'origine, selon la valeur la plus élevée. Pour plus d’informations sur la modification du paramètre de la `autoshrink` propriété, consultez [afficher ou modifier les propriétés d’une base de données](../databases/view-or-change-the-properties-of-a-database.md)-utiliser le **Auto Shrink** propriété sur le **Options**page- ou [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)-utilisez l’option AUTO_SHRINK.  
  
  
##  <a name="AddOrEnlarge"></a> Ajouter ou agrandir un fichier journal  
 Une autre solution pour gagner de l'espace consiste à agrandir le fichier journal existant (si l'espace disque le permet) ou à ajouter un fichier journal à la base de données, généralement sur un autre disque.  
  
-   Pour ajouter un fichier journal à la base de données, utilisez la clause ADD LOG FILE de l'instruction ALTER DATABASE. L'ajout d'un fichier journal permet au journal de croître.  
  
-   Pour agrandir le fichier journal, utilisez la clause MODIFY FILE de l'instruction ALTER DATABASE en spécifiant la syntaxe SIZE et MAXSIZE. Pour plus d’informations, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
  
##  <a name="tempdbOptimize"></a> Optimiser la taille du journal des transactions tempdb  
 Le redémarrage d’une instance de serveur permet de redimensionner le journal des transactions de la base de données **tempdb** conformément à sa taille d’origine avant la croissance automatique. Ceci peut réduire les performances du journal des transactions **tempdb** . Vous pouvez éviter cette surcharge en augmentant la taille du journal des transactions **tempdb** après avoir démarré ou redémarré l'instance de serveur. Pour plus d'informations, consultez [tempdb Database](../databases/tempdb-database.md).  
  
  
##  <a name="ControlGrowth"></a> Contrôler la croissance d’un fichier journal des transactions  
 Vous pouvez utiliser l’instruction [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) pour gérer la croissance d’un fichier journal de transactions. Notez les points suivants :  
  
-   Pour modifier la taille actuelle du fichier selon les unités Ko, Mo, Go et To, utilisez l'option SIZE.  
  
-   Pour modifier l'incrément de croissance, utilisez l'option FILEGROWTH. Une valeur 0 indique que la croissance automatique est désactivée et qu'aucun espace supplémentaire n'est autorisé. Un faible incrément de croissance automatique d'un fichier journal peut réduire les performances. L'incrément de croissance d'un fichier journal doit être suffisamment important pour éviter une expansion fréquente. Un incrément de croissance par défaut de 10 % convient généralement.  
  
     Pour plus d’informations sur la modification de la propriété de croissance des fichiers sur un fichier journal, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
-   Pour contrôler la taille maximale d'un fichier journal en Ko, Mo, Go et To ou affecter la valeur UNLIMITED à la croissance, utilisez l'option MAXSIZE.  
  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Résoudre les problèmes liés à un journal des transactions saturé &#40;erreur SQL Server 9002&#41;](troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
  
