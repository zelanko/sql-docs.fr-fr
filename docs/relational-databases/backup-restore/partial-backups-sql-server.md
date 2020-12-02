---
title: Sauvegardes partielles (SQL Server) | Microsoft Docs
description: Dans SQL Server, une sauvegarde partielle contient les données du groupe de fichiers principal, l’ensemble des groupes de fichiers en lecture-écriture et, éventuellement, un ou plusieurs fichiers en lecture seule.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- partial backups [SQL Server]
- READ_WRITE_FILEGROUPS option
- database backups [SQL Server], about backing up databases
ms.assetid: fe6b6bb1-38d0-46c4-bab8-31df14e8999c
author: cawrites
ms.author: chadam
ms.openlocfilehash: 715eb703a5ae2d09e363c1b572f3645d42e7090f
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "96129242"
---
# <a name="partial-backups-sql-server"></a>Sauvegardes partielles (SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Tous les modes de récupération de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prennent en charge les sauvegardes partielles ; par conséquent, cette rubrique concerne toutes les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Toutefois, les sauvegardes partielles sont conçues pour le mode de récupération simple et permettent d'améliorer la souplesse des sauvegardes de bases de données très volumineuses qui contiennent un ou plusieurs groupes de fichiers en lecture seule.  
  
 Les sauvegardes partielles sont utiles à chaque fois que vous souhaitez exclure des groupes de fichiers en lecture seule. Une *sauvegarde partielle* s’apparente à une sauvegarde complète de base de données, mais la première ne contient pas tous les groupes de fichiers. En revanche, pour une base de données accessible en lecture/écriture, une sauvegarde partielle contient toutes les données du groupe de fichiers primaire, de chaque groupe de fichiers en lecture/écriture et, éventuellement, d'un ou de plusieurs fichiers en lecture seule. La sauvegarde partielle d'une base de données en lecture seule contient uniquement le groupe de fichiers primaire.  
  
> [!NOTE]  
>  Si la base de données en lecture seule est convertie ensuite en base de données en lecture-écriture après une sauvegarde partielle, des groupes de fichiers secondaires en lecture-écriture peuvent ne pas figurer dans la sauvegarde partielle. Dans ce cas, si vous tentez d'effectuer une sauvegarde partielle différentielle, la sauvegarde échoue. Pour pouvoir créer une sauvegarde partielle différentielle de la base de données, vous devez créer une autre sauvegarde partielle. La nouvelle sauvegarde partielle contient tous les groupes de fichiers secondaires en lecture-écriture qui peuvent servir de base pour les sauvegardes partielles différentielles.  
  
 Des sauvegardes de fichiers de groupes de fichiers en lecture seule peuvent être associées à des sauvegardes partielles. Pour plus d’informations sur les sauvegardes de fichiers, consultez [Sauvegardes de fichiers complètes &#40;SQL Server&#41;](../../relational-databases/backup-restore/full-file-backups-sql-server.md).  
  
 Une sauvegarde partielle peut servir de *base différentielle* pour des sauvegardes partielles différentielles. Pour plus d’informations, consultez [Sauvegardes différentielles &#40;SQL Server&#41;](../../relational-databases/backup-restore/differential-backups-sql-server.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
> [!NOTE]  
>  Les sauvegardes partielles ne sont pas prises en charge par [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou par l'Assistant Plan de maintenance.  
  
 **Pour créer une sauvegarde partielle**  
  
-   [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md) (READ_WRITE_FILEGROUPS ; option FILEGROUP, si nécessaire)  
  
 **Pour utiliser une sauvegarde partielle dans une séquence de restauration**  
  
-   [Exemple : restauration fragmentaire d’une base de données &#40;mode de récupération simple&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire de quelques groupes de fichiers uniquement &#40;mode de récupération simple&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Vue d’ensemble de la sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)   
 [Restaurations de fichiers &#40;mode de récupération simple&#41;](../../relational-databases/backup-restore/file-restores-simple-recovery-model.md)   
 [Restaurations fragmentaires &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
  
