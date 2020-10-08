---
description: sys.database_usage (Azure SQL Database)
title: sys.database_usage (Azure SQL Database) | Microsoft Docs
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
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: f0c8809138bfad5cc9b7c4866978e7f2c111e09a
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91809207"
---
# <a name="sysdatabase_usage-azure-sql-database"></a>sys.database_usage (Azure SQL Database)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  **Remarque : cela s’applique uniquement à Azure SQL Database v11.**  
  
 Répertorie le nombre, le type et la durée des bases de données sur le [!INCLUDE[ssSDS](../../includes/sssds-md.md)] serveur.  
  
 La vue **sys.database_usage** contient les colonnes suivantes.  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|time|Date à laquelle les événements d'utilisation se sont produits.|  
|sku|Type de niveau de service pour la base de données : **Web**, **Business**, de **base**, **standard**, **Premium**|  
|quantité|Nombre maximal de bases de données d'un type de SKU ayant existé pendant cette journée.|  
  
## <a name="permissions"></a>Autorisations  
 L’accès en lecture seule à cette vue est disponible pour tous les utilisateurs disposant d’autorisations pour se connecter à la base de données **Master** .  
  
## <a name="remarks"></a>Notes  
 La vue **sys.database_usage** renvoie une ligne pour chaque journée de votre abonnement.  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de la tarification de SQL Database](https://go.microsoft.com/fwlink/?LinkID=394978)   
 [Comptes et facturation dans Base de données SQL Azure](/previous-versions/azure/ee621788(v=azure.100))  
  
