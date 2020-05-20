---
title: sys. configurations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.configurations_TSQL
- configurations
- sys.configurations
- configurations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.configurations catalog view
ms.assetid: c4709ed1-bf88-4458-9e98-8e9b78150441
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 885b736424dfa0b1a83f0d0c854fc11b80f67ade
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832764"
---
# <a name="sysconfigurations-transact-sql"></a>sys.configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque valeur de l’option de configuration au niveau du serveur dans le système.  

|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|ID unique pour la valeur de configuration.|  
|**name**|**nvarchar(35)**|Nom de l'option de configuration.|  
|**value**|**sql_variant**|Valeur configurée pour cette option.|  
|**minimale**|**sql_variant**|Valeur minimale pour l'option de configuration.|  
|**valeurs**|**sql_variant**|Valeur maximale pour l'option de configuration.|  
|**value_in_use**|**sql_variant**|Valeur en cours d'exécution actuellement en effet pour cette option.|  
|**descriptive**|**nvarchar(255)**|Description de l'option de configuration.|  
|**is_dynamic**|**bit**|1 = Variable qui prend effet lorsque l'instruction RECONFIGURE est exécutée.|  
|**is_advanced**|**bit**|1 = la variable s’affiche uniquement lorsque l' **affichage advancedoption** est défini.|  
  
 Pour obtenir la liste de toutes les options de configuration du serveur, consultez [options de configuration du serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
> [!NOTE]  
>  Pour les options de configuration au niveau de la base de données, consultez [ALTER DATABASE scoped configuration &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md). Pour configurer soft-NUMA, consultez [Soft-numa &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md).  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue de configurations à l’ensemble du serveur &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
