---
title: "Récupérer un numéro séquentiel dans le journal (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- log sequence numbers [SQL Server]
- STOPBEFOREMARK option [RESTORE statement]
- STOPATMARK option [RESTORE statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
- recovery [SQL Server], databases
- restoring [SQL Server], point in time
- LSNs
- database recovery [SQL Server]
- database restores [SQL Server], point in time
ms.assetid: f7b3de5b-198d-448d-8c71-1cdd9239676c
caps.latest.revision: 38
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ef9f98df730801b692eace924e094caa6b078ac6
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="recover-to-a-log-sequence-number-sql-server"></a>Récupérer un numéro séquentiel dans le journal (SQL Server)
  Cette rubrique s'applique uniquement aux bases de données employant les modes de restauration complète ou de récupération utilisant les journaux de transactions.  
  
 Vous pouvez utiliser un numéro séquentiel dans le journal pour définir le point de récupération d'une opération de restauration. Toutefois, cette fonctionnalité est spécialement conçue pour les fournisseurs d'outils et ne devrait pas être nécessaire dans la plupart des cas.  
  
##  <a name="LSNs"></a> Vue d'ensemble des numéros séquentiels dans le journal  
 Les numéros LSN sont utilisés en interne pendant une séquence RESTORE pour rechercher le point dans le temps par rapport auquel les données ont été restaurées. Lorsqu'une sauvegarde est restaurée, les données sont restaurées par rapport au numéro LSN qui correspond au point dans le temps à partir duquel la sauvegarde a été effectuée. Les sauvegardes différentielles et de journaux font passer la base de données restaurée à une date ultérieure qui correspond à un numéro LSN supérieur.  
  
 Chaque enregistrement du journal de transactions est identifié de manière unique par un numéro séquentiel dans le journal (LSN). Les numéros de séquence d'enregistrement sont ordonnés de sorte que si LSN2 est supérieur à LSN1, la modification décrite par l'enregistrement de journal référencé par LSN2 se produit après la modification décrite par le numéro LSN d'enregistrement de journal.  
  
 Le numéro LSN d'un enregistrement de journal qui correspond à l'occurrence d'un événement significatif peut s'avérer utile pour créer les séquences de restauration appropriées. Du fait que les numéros LSN sont ordonnés, il est possible de comparer leur égalité et leur inégalité (à savoir, **\<**, **>**, **=**, **\<=**, **>=**). Ces comparaisons sont utiles pour créer des séquences de restauration.  
  
> [!NOTE]  
>  Les numéros LSN sont des valeurs de type données **numeric**(25,0). Les opérations arithmétiques (addition ou soustraction, par exemple) ne sont pas significatives et ne doivent pas être utilisées avec les numéros LSN.  
  
  
## <a name="viewing-lsns-used-by-backup-and-restore"></a>Affichage des numéros LSN utilisés par la sauvegarde et la restauration  
 Le numéro LSN d'un enregistrement de journal dans lequel un événement de sauvegarde et de restauration s'est produit peut être affiché en utilisant une ou plusieurs des commandes suivantes :  
  
-   [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
-   [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md)  
  
-   [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md); [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
-   [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)  
  
-   [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)  
  
> [!NOTE]  
>  Les numéros LSN figurent également dans les textes de message.  
  
## <a name="transact-sql-syntax-for-restoring-to-an-lsn"></a>Syntaxe Transact-SQL relative à la restauration d'après un LSN  
 Grâce à l'instruction [RESTORE](../../t-sql/statements/restore-statements-transact-sql.md) , vous pouvez vous arrêter à un LSN ou immédiatement avant ce point de la façon suivante :  
  
-   Utilisez la clause WITH STOPATMARK **='**lsn:*<numéro_lsn>***'**, où lsn:*\<numéro_lsn* correspond à une chaîne précisant que l’enregistrement du journal qui contient le LSN spécifié équivaut au point de récupération.  
  
     STOPATMARK permet la restauration par progression jusqu'au NSE et inclut l'enregistrement correspondant issu du journal, dans la restauration.  
  
-   Utilisez la clause WITH STOPBEFOREMARK **='**lsn:*<numéro_lsn>***'**, où lsn:*\<numéro_lsn>* correspond à une chaîne précisant que l’entrée se trouvant dans le journal immédiatement avant celle qui contient le NSE précisé équivaut au point de récupération.  
  
     STOPBEFOREMARK permet la restauration par progression jusqu'au NSE mais exclut l'enregistrement correspondant, se trouvant dans le journal, de la restauration par progression.  
  
 De façon générale, une transaction donnée est sélectionnée dans le but d'être incluse ou exclue. Dans la pratique, et ce même s'il n'est pas requis, l'enregistrement spécifié dans le journal correspond à un enregistrement de validation de transaction.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant suppose que la base de données `AdventureWorks` a été modifiée afin d'utiliser le mode de récupération complète.  
  
```  
RESTORE LOG AdventureWorks FROM DISK = 'c:\adventureworks_log.bak'   
WITH STOPATMARK = 'lsn:15000000040000037'  
GO  
```  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Restaurer une sauvegarde de base de données à l’aide de SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [Sauvegarder un journal des transactions &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   [Restaurer une sauvegarde de journal des transactions &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [Restaurer une base de données jusqu’au point d’échec en mode de récupération complète &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-database-to-point-of-failure-full-recovery.md)  
  
-   [Restaurer une base de données jusqu’à une transaction marquée &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [Restaurer une base de données SQL Server jusqu’à une limite dans le temps &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Appliquer les sauvegardes du journal des transactions &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [Journal des transactions &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
  
