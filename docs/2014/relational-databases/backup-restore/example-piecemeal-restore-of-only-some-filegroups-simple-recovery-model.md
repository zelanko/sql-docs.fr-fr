---
title: 'Exemple : Restauration fragmentaire de quelques groupes de fichiers (mode de récupération Simple) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- piecemeal restores [SQL Server], simple recovery model
- restore sequences [SQL Server], piecemeal
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: d7ad026c-5355-4308-9560-0dc843940d4f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7cdc7e6c036a38ac40eb8c7bb2495b1ed5a3e6e7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62922027"
---
# <a name="example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model"></a>Exemple : Restauration fragmentaire de quelques groupes de fichiers uniquement (mode de récupération simple)
  Cette rubrique concerne les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] obéissant au mode de récupération simple et contenant un groupe de fichiers en lecture seule.  
  
 Une séquence de restauration fragmentaire restaure et récupère une base de données par étapes au niveau des groupes de fichiers, en commençant par le groupe de fichiers primaire et tous les groupes de fichiers secondaires en lecture-écriture.  
  
 Dans cet exemple, une base de données appelée `adb`qui utilise le mode de récupération simple, contient trois groupes de fichiers. Le groupe de fichiers `A` est en lecture-écriture, et les groupes de fichiers `B` et `C` sont en lecture seule. Au départ, tous les groupes de fichiers sont en ligne.  
  
 Le groupe de fichiers primaire et le groupe de fichiers `B` de la base de données `adb` s'avèrent endommagés. L'administrateur de la base de données décide donc de les restaurer à l'aide d'une séquence de restauration fragmentaire. En mode de récupération simple, tous les groupes de fichiers en lecture-écriture doivent être restaurés à partir de la même sauvegarde partielle. Même si le groupe de fichiers `A` est intact, celui-ci doit être restauré avec le groupe de fichiers primaire pour s'assurer de sa cohérence (la base de données sera restaurée à un point dans le temps défini à la fin de la dernière sauvegarde partielle). Le groupe de fichiers `C` est intact, mais il doit être récupéré pour être mis en ligne. Bien que le groupe de fichiers `B`soit endommagé, il contient des données moins critiques que le groupe de fichiers `C`. Par conséquent, `B` sera restauré en dernier.  
  
## <a name="restore-sequences"></a>Séquences de restauration  
  
> [!NOTE]  
>  La syntaxe pour une séquence de restauration en ligne est la même que pour une séquence de restauration hors connexion.  
  
1.  Restauration partielle du groupe de fichiers primaire et du groupe de fichiers `A` à partir d'une sauvegarde partielle  
  
    ```  
    RESTORE DATABASE adb READ_WRITE_FILEGROUPS FROM partial_backup   
    WITH PARTIAL, RECOVERY  
    ```  
  
     À ce stade, le groupe de fichiers primaire et le groupe de fichiers `A` sont en ligne. Les fichiers dans les groupes de fichiers `B` et `C` sont en attente de récupération et les groupes de fichiers sont hors connexion.  
  
2.  Récupération en ligne du groupe de fichiers `C`.  
  
     Le groupe de fichiers `C` est cohérent car la sauvegarde partielle restaurée ci-dessus a été effectuée une fois que le groupe de fichiers `C` est passé en lecture seule, même si la restauration de la base de données a été effectuée antérieurement. L'administrateur de la base de données récupère le groupe de fichiers `C`, sans le restaurer, pour le mettre en ligne.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='C' WITH RECOVERY  
    ```  
  
     À ce stade, le groupe de fichiers primaire et les groupes de fichiers `A` et `C` sont en ligne. Les fichiers du groupe de fichiers B restent en attente de récupération et le groupe de fichiers est hors connexion.  
  
3.  Restauration en ligne du groupe de fichiers `B.`  
  
     Les fichiers du groupe de fichiers `B` doivent être restaurés. L'administrateur de la base de données restaure la sauvegarde du groupe de fichiers `B` effectuée après que ce groupe de fichiers `B` est passé en lecture seule et avant la sauvegarde partielle.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup   
    WITH RECOVERY  
    ```  
  
     Tous les groupes de fichiers sont maintenant en ligne.  
  
## <a name="additional-examples"></a>Autres exemples  
  
-   [Exemple : restauration fragmentaire d’une base de données &#40;mode de récupération simple&#41;](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Exemple : restauration en ligne d’un fichier en lecture seule &#40;mode de récupération simple&#41;](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire d’une base de données &#40;mode de restauration complète&#41;](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire de quelques groupes de fichiers &#40;mode de récupération complète&#41;](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Exemple : restauration en ligne d’un fichier en lecture/écriture &#40;mode de récupération complète&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Exemple : restauration en ligne d’un fichier en lecture seule &#40;mode de restauration complète&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Restauration en ligne &#40;SQL Server&#41;](online-restore-sql-server.md)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Restaurations fragmentaires &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)  
  
  
