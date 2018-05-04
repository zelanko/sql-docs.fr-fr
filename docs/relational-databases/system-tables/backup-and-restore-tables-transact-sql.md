---
title: Sauvegarde et restauration des Tables (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system tables [SQL Server], backup tables
- backup system tables [SQL Server]
- system tables [SQL Server], restore tables
- restore system tables [SQL Server]
ms.assetid: aa615add-54e6-40f5-8b55-3728b26884ee
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: de2fb96afe4fb24cc7fe6455c880027d61d43ddb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="backup-and-restore-tables-transact-sql"></a>Sauvegarder et restaurer des tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Les rubriques de cette section détaillent les tables système qui stockent les informations utilisées par les procédures de sauvegarde et de restauration des bases de données.  
  
## <a name="in-this-section"></a>Dans cette section  
 [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md)  
 Contient une ligne pour chaque fichier de données ou fichier journal d'une base de données.  
  
 [backupfilegroup](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
 Contient une ligne pour chaque groupe de fichiers d'une base de données au moment de la sauvegarde.  
  
 [backupmediafamily](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
 Contient une ligne pour chaque famille de supports de sauvegarde.  
  
 [backupmediaset](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
 Contient une ligne pour chaque support de sauvegarde.  
  
 [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)  
 Contient une ligne pour chaque jeu de sauvegarde.  
  
 [logmarkhistory](../../relational-databases/system-tables/logmarkhistory-transact-sql.md)  
 Contient une ligne par transaction marquée validée.  
  
 [restorefile](../../relational-databases/system-tables/restorefile-transact-sql.md)  
 Contient une ligne pour chaque fichier restauré. Les fichiers restaurés indirectement par nom de groupe de fichiers sont compris.  
  
 [restorefilegroup](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)  
 Contient une ligne par groupe de fichiers restaurés.  
  
 [restorehistory](../../relational-databases/system-tables/restorehistory-transact-sql.md)  
 Contient une ligne par opération de restauration.  
  
 [suspect_pages](../../relational-databases/system-tables/suspect-pages-transact-sql.md)  
 Contient une ligne par page ayant échoué avec une erreur 824 (avec une limite de 1 000 lignes).  
  
 [sysopentapes](../../relational-databases/system-tables/sysopentapes-transact-sql.md)  
 Contient une ligne pour chaque unité de bande actuellement ouverte.  
  
  
