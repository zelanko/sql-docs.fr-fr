---
title: sys. database_usage (Azure SQL Database) | Microsoft Docs
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
ms.openlocfilehash: 0a0789ebd9a5aa4bd10605d69afa59a586ce75b2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70155534"
---
# <a name="sysdatabase_usage-azure-sql-database"></a>sys.database_usage (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **Remarque : cela s’applique uniquement à Azure SQL Database v11.**  
  
 Répertorie le nombre, le type et la durée des bases de [!INCLUDE[ssSDS](../../includes/sssds-md.md)] données sur le serveur.  
  
 La vue **sys. database_usage** contient les colonnes suivantes.  
  
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
 [Comptes et facturation dans Base de données SQL Azure](https://msdn.microsoft.com/library/windowsazure/ee621788.aspx)  
  
  
