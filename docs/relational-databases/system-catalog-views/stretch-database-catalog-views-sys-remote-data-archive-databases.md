---
title: sys.remote_data_archive_databases (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.remote_data_archive_databases
- sys.remote_data_archive_databases_TSQL
- remote_data_archive_databases
- remote_data_archive_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_data_archive_databases catalog view
ms.assetid: 25bffb0c-9821-40b4-88cf-75f854891a09
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: 339d960a136e9cf939032068c21ec737f4d37ceb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68018197"
---
# <a name="stretch-database-catalog-views---sysremotedataarchivedatabases"></a>Stretch Database des vues de catalogue - sys.remote_data_archive_databases
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque base de données distante qui stocke les données à partir d’une base de données locale prenant en charge Stretch.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**remote_database_id**|**int**|L’identificateur local généré automatiquement de la base de données distante.|  
|**remote_database_name**|**sysname**|Le nom de la base de données distante.|  
|**data_source_id**|**Int**|La source de données utilisée pour se connecter au serveur distant|  
  
## <a name="see-also"></a>Voir aussi  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
