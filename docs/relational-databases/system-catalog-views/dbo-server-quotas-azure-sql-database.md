---
title: dbo.server_quotas (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: ''
ms.reviewer: ''
ms.prod_service: sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.server_quotas
- dbo.server_quotas_TSQL
- server_quotas
- server_quotas_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server_quotas
ms.assetid: 34423903-1aaa-4a55-88a6-8228315d84e7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: e11b4ef7224a622b22c3d7cc15d97175c73625bd
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51671329"
---
# <a name="dboserverquotas-azure-sql-database"></a>dbo.server_quotas (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> **IMPORTANT** Cela s’applique aux  **[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11 uniquement !**  
>   
>  Cette fonctionnalité est dans un état d'aperçu. N'établissez pas de dépendance sur l'implémentation spécifique de cette fonctionnalité, car elle est susceptible d'être modifiée ou supprimée dans une future version.  
  
 Retourne les types de quota de base de données disponibles sur le serveur.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|quota_name|**nvarchar**|Type de quota du serveur. Le type **Premium_database** équivaut aux bases de données avec une réservation de ressources.|  
|quota_value|**Int**|Nombre de types de quota autorisé dans le serveur.|  
  
## <a name="permissions"></a>Permissions  
 Cette vue est disponible pour tous les rôles d’utilisateur avec des autorisations pour se connecter à virtuel **master** base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des bases de données Premium](https://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
