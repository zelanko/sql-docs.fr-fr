---
description: TABLES (Transact-SQL)
title: TABLES (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/20/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- TABLES_TSQL
- TABLES
dev_langs:
- TSQL
helpviewer_keywords:
- TABLES view
- INFORMATION_SCHEMA.TABLES view
ms.assetid: 723a9e63-8f6e-4d6e-b570-468cfaf03201
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7e94fe84e47f40cfc85af1cc002fced981c01706
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97440580"
---
# <a name="tables-transact-sql"></a>TABLES (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Retourne une ligne pour chaque table ou vue de la base de données active pour laquelle l’utilisateur actuel dispose d’autorisations.  
  
 Pour récupérer des informations de ces vues, spécifiez le nom complet de **INFORMATION_SCHEMA.** _view_name_.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|Qualificateur de la table.|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|Nom du schéma qui contient la table.<br /><br /> Important la seule façon fiable de trouver le schéma d’un objet est d’interroger l’affichage catalogue sys. Objects. <strong> \* \* \* \* </strong> Les vues INFORMATION_SCHEMA peuvent être incomplètes dans la mesure où elles ne sont pas mises à jour pour toutes les nouvelles fonctionnalités.|  
|**TABLE_NAME**|**sysname**|Nom de table ou de vue.|  
|**TABLE_TYPE**|**varchar (** 10 **)**|Type de table. Peut être VIEW ou BASE TABLE.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues système &#40;&#41;Transact-SQL ](../../t-sql/language-reference.md)   
 [Vues de schémas d’informations &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)  
  
