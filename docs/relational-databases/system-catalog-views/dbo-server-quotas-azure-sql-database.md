---
title: "dbo.server_quotas (base de données de SQL Azure) | Documents Microsoft"
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 08/02/2016
ms.prod: 
ms.reviewer: 
ms.service: sql-database
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.server_quotas
- dbo.server_quotas_TSQL
- server_quotas
- server_quotas_TSQL
dev_langs: TSQL
helpviewer_keywords: server_quotas
ms.assetid: 34423903-1aaa-4a55-88a6-8228315d84e7
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 612f4d0a819c1271ca9b5e8b9fda8f224ae6fbe6
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="dboserverquotas-azure-sql-database"></a>dbo.server_quotas (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> **IMPORTANT** Cela s’applique aux  **[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11 uniquement !**  
>   
>  Cette fonctionnalité est dans un état d'aperçu. N'établissez pas de dépendance sur l'implémentation spécifique de cette fonctionnalité, car elle est susceptible d'être modifiée ou supprimée dans une future version.  
  
 Retourne les types de quota de base de données disponibles sur le serveur.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|quota_name|**nvarchar**|Type de quota du serveur. Le type **Premium_database** est équivalent aux bases de données avec une réservation de ressources.|  
|quota_value|**int**|Nombre de types de quota autorisé dans le serveur.|  
  
## <a name="permissions"></a>Permissions  
 Cette vue est disponible pour tous les rôles d’utilisateur disposant des autorisations pour se connecter à virtuel **master** base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des bases de données Premium](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
