---
title: DOMAIN_CONSTRAINTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DOMAIN_CONSTRAINTS
- DOMAIN_CONSTRAINTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.DOMAIN_CONSTRAINTS view
- DOMAIN_CONSTRAINTS view
ms.assetid: 436c4480-f1e3-403f-b2bd-de04539afe3c
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7392edabcef2b1ff8348bab641380b6ab64cea0f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67950765"
---
# <a name="domain_constraints-transact-sql"></a>DOMAIN_CONSTRAINTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque type d'alias dans la base de données actuelle, qui a une règle lui étant associée et à laquelle l'utilisateur actuel peut accéder.  
  
 Pour récupérer des informations de ces vues, spécifiez le nom complet de **INFORMATION_SCHEMA.** _view_name_.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**nvarchar (** 128 **)**|Base de données dans laquelle se trouve la règle.|  
|**CONSTRAINT_SCHEMA**|**nvarchar (** 128 **)**|Nom du schéma qui contient la contrainte.<br /><br /> <strong> \* Important \* \* </strong> N’utilisez pas de vues de INFORMATION_SCHEMA pour déterminer le schéma d’un objet. La seule méthode fiable pour rechercher le schéma d’un objet consiste à interroger l’affichage catalogue sys. Objects.|  
|**CONSTRAINT_NAME**|**sysname**|Nom de la règle.|  
|**DOMAIN_CATALOG**|**nvarchar (** 128 **)**|Base de données dans laquelle réside le type de données alias.|  
|**DOMAIN_SCHEMA**|**nvarchar (** 128 **)**|Nom du schéma qui contient le type de données alias.<br /><br /> <strong> \* Important \* \* </strong> N’utilisez pas de vues de INFORMATION_SCHEMA pour déterminer le schéma d’un type de données. La seule méthode fiable pour rechercher le schéma d'un type est d'utiliser la fonction TYPEPROPERTY.|  
|**DOMAIN_NAME**|**sysname**|Type de données alias.|  
|**IS_DEFERRABLE**|**varchar (** 2 **)**|Spécifie si la vérification de contrainte peut être différée. Renvoie toujours NO.|  
|**INITIALLY_DEFERRED**|**varchar (** 2 **)**|Spécifie si la vérification des contraintes est différée au départ. Renvoie toujours NO.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues système &#40;&#41;Transact-SQL](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Vues de schémas d’informations &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys. Objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
  
