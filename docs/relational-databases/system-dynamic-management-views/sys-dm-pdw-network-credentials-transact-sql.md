---
title: sys. dm_pdw_network_credentials (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b75eb53da9961025e3310f27e4a12608dd4fda78
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899361"
---
# <a name="sysdm_pdw_network_credentials-transact-sql"></a>sys. dm_pdw_network_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Retourne la liste de toutes les informations d’identification réseau stockées [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] dans l’appliance pour tous les serveurs cibles. Les résultats sont répertoriés pour le nœud de contrôle et tous les nœuds de calcul.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|ID numérique unique associé au nœud.|  
|target_server_name|**nvarchar (32)**|Adresse IP du serveur cible qui [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] accédera à l’aide des informations d’identification du nom d’utilisateur et du mot de passe.|  
|username|**nvarchar (32)**|Nom d’utilisateur pour lequel le mot de passe est stocké.|  
|last_modified|**DATETIME**|Date et heure de la dernière opération ayant modifié les informations d’identification.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert l’état du serveur d’affichage.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 La clé de cette vue de gestion dynamique est *pdw_node_id* plus *target_server_name*.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de gestion dynamique Data Warehouse parallèles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
