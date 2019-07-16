---
title: sys.dm_pdw_network_credentials (Transact-SQL) | Microsoft Docs
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899361"
---
# <a name="sysdmpdwnetworkcredentials-transact-sql"></a>Sys.dm_pdw_network_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Retourne une liste de toutes les informations d’identification réseau stockée dans le [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] appliance pour tous les serveurs cibles. Résultats sont répertoriées pour le nœud de contrôle et chaque nœud de calcul.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|Id numérique unique associé au nœud.|  
|target_server_name|**nvarchar(32)**|Adresse IP du serveur cible qui [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] en utilisant les informations d’identification de nom d’utilisateur et mot de passe.|  
|userName|**nvarchar(32)**|Nom d’utilisateur pour lequel le mot de passe est stockée.|  
|last_modified|**datetime**|Date et heure de la dernière opération qui a modifié les informations d’identification.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert VIEW SERVER STATE.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 La clé pour cette vue de gestion dynamique est *pdw_node_id* plus *nom_du_serveur_cible*.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
