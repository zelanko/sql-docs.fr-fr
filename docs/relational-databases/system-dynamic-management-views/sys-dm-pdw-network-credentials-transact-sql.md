---
title: Sys.dm_pdw_network_credentials (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.reviewer: 
ms.service: 
ms.component: dmv's
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 21935bde6ebefe2b30743a4961ba05e3092539d6
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwnetworkcredentials-transact-sql"></a>Sys.dm_pdw_network_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Retourne une liste de toutes les informations d’identification de réseau est stockée dans le [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] matériel pour tous les serveurs cibles. Les résultats sont répertoriés pour le nœud de contrôle et chaque nœud de calcul.  
  
|Nom de la colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|Id numérique unique associé au nœud.|  
|nom_du_serveur_cible|**nvarchar(32)**|Adresse IP du serveur cible qui [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] en utilisant les informations d’identification de nom d’utilisateur et mot de passe.|  
|username|**nvarchar(32)**|Nom d’utilisateur pour lequel le mot de passe est stocké.|  
|last_modified|**datetime**|Date et heure de la dernière opération qui a modifié les informations d’identification.|  
  
## <a name="permissions"></a>Permissions  
 Requiert VIEW SERVER STATE.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 La clé pour cette vue de gestion dynamique est *pdw_node_id* plus *nom_du_serveur_cible*.  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de gestion dynamique de l’entrepôt de données en parallèle &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
