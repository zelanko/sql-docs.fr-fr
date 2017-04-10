---
title: "Exemple&#160;: restauration en ligne d&#39;un fichier en lecture seule (mode de restauration compl&#232;te) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mode de récupération complète [SQL Server], exemple RESTORE"
  - "restaurations en ligne [SQL Server], mode de récupération complète"
  - "séquences de restauration [SQL Server], en ligne"
ms.assetid: 7ea2d2af-086f-48dc-9636-38dc194c7090
caps.latest.revision: 26
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 26
---
# Exemple&#160;: restauration en ligne d&#39;un fichier en lecture seule (mode de restauration compl&#232;te)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Cette rubrique concerne les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui relèvent du mode de récupération complète et qui contiennent plusieurs fichiers ou groupes de fichiers.  
  
 Dans cet exemple, une base de données appelée `adb` qui utilise le mode de restauration complète, contient trois groupes de fichiers. Le groupe de fichiers `A` est en lecture-écriture, et les groupes de fichiers `B` et `C` sont en lecture seule. Au départ, tous les groupes de fichiers sont en ligne.  
  
 Un fichier en lecture seule `b1` du groupe de fichiers `B` de la base de données `adb` doit être restauré. Une sauvegarde ayant été réalisée depuis que le fichier est devenu accessible en lecture seule ; les sauvegardes du journal ne sont pas nécessaires. Le groupe de fichiers `B` est hors connexion pendant la restauration, mais le reste de la base de données demeure en ligne.  
  
## Séquence de restauration  
  
> [!NOTE]  
>  La syntaxe pour une séquence de restauration en ligne est la même que pour une séquence de restauration hors connexion.  
  
 Pour restaurer le fichier, l'administrateur de la base de données doit utiliser la séquence de restauration suivante :  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup  
WITH RECOVERY   
```  
  
 Le groupe de fichiers B est maintenant en ligne.  
  
## Autres exemples  
  
-   [Exemple : restauration fragmentaire d’une base de données &#40;Mode de récupération simple&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire de quelques groupes de fichiers uniquement &#40;mode de récupération simple&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Exemple : restauration en ligne d’un fichier en lecture seule &#40;Mode de récupération simple&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire d’une base de données &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire de quelques groupes de fichiers &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Exemple : restauration en ligne d’un fichier en lecture/écriture &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
## Voir aussi  
 [Restauration en ligne &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [Vue d’ensemble de la restauration et de la récupération &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [Restaurations de fichiers &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  