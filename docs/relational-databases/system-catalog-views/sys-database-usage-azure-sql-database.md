---
title: Sys.database_usage (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- database_usage
- database_usage_TSQL
- sys.database_usage_TSQL
- sys.database_usage
dev_langs:
- TSQL
helpviewer_keywords:
- database_usage
- sys.database_usage
ms.assetid: be6820de-60bf-4ddd-ace7-4077893d630f
author: julieMSFT
ms.author: jrasnick
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 56e09dc849223832bbd65c09c16e1f6aeed09e17
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716569"
---
# <a name="sysdatabaseusage-azure-sql-database"></a>sys.database_usage (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **Remarque : Cela s’applique uniquement à Azure SQL Database V11.**  
  
 Répertorie le nombre, le type et la durée des bases de données sur le [!INCLUDE[ssSDS](../../includes/sssds-md.md)] server.  
  
 Le **sys.database_usage** vue contient les colonnes suivantes.  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|time|Date à laquelle les événements d'utilisation se sont produits.|  
|sku|Le type de niveau de service pour la base de données : **Web**, **Business**, **Basic**, **Standard**, **Premium**|  
|quantity|Nombre maximal de bases de données d'un type de SKU ayant existé pendant cette journée.|  
  
## <a name="permissions"></a>Autorisations  
 Accès en lecture seule à cette vue est disponible pour tous les utilisateurs disposant des autorisations pour se connecter à la **master** base de données.  
  
## <a name="remarks"></a>Notes  
 Le **sys.database_usage** vue retourne une ligne pour chaque jour de votre abonnement.  
  
## <a name="see-also"></a>Voir aussi  
 [Tarification – base de données SQL](https://go.microsoft.com/fwlink/?LinkID=394978)   
 [Comptes et facturation dans Microsoft Azure SQL Database](https://msdn.microsoft.com/library/windowsazure/ee621788.aspx)  
  
  
