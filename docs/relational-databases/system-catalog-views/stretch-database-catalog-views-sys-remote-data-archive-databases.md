---
title: sys. remote_data_archive_databases (Transact-SQL) | Microsoft Docs
description: Découvrez comment sys. remote_data_archive_databases contient une ligne pour chaque base de données distante qui stocke des données à partir d’une base de données locale Stretch.
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
ms.openlocfilehash: e192a70c1d8f46b7ad89844a3b38019ab6364cc1
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248148"
---
# <a name="stretch-database-catalog-views---sysremote_data_archive_databases"></a>Affichages catalogue Stretch Database-sys. remote_data_archive_databases
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Contient une ligne pour chaque base de données distante qui stocke les données d’une base de données locale Stretch.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**remote_database_id**|**int**|Identificateur local généré automatiquement de la base de données distante.|  
|**remote_database_name**|**sysname**|Nom de la base de données distante.|  
|**data_source_id**|**int**|Source de données utilisée pour se connecter au serveur distant|  
  
## <a name="see-also"></a>Voir aussi  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
