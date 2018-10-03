---
title: Sys.dm_pdw_network_credentials (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0661b5bd203cd1bca26ed6fb5bf380d6882dc5e5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47609917"
---
# <a name="sysdmpdwnetworkcredentials-transact-sql"></a>Sys.dm_pdw_network_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Retourne une liste de toutes les informations d’identification réseau stockée dans le [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] appliance pour tous les serveurs cibles. Résultats sont répertoriées pour le nœud de contrôle et chaque nœud de calcul.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**Int**|Id numérique unique associé au nœud.|  
|target_server_name|**nvarchar(32)**|Adresse IP du serveur cible qui [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] en utilisant les informations d’identification de nom d’utilisateur et mot de passe.|  
|username|**nvarchar(32)**|Nom d’utilisateur pour lequel le mot de passe est stockée.|  
|last_modified|**datetime**|Date et heure de la dernière opération qui a modifié les informations d’identification.|  
  
## <a name="permissions"></a>Permissions  
 Requiert VIEW SERVER STATE.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 La clé pour cette vue de gestion dynamique est *pdw_node_id* plus *nom_du_serveur_cible*.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
