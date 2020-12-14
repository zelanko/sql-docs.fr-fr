---
description: sys.pdw_diag_sessions (Transact-SQL)
title: sys.pdw_diag_sessions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4d23688a-cddb-4eed-8231-ecde2a0b0e65
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016'
ms.openlocfilehash: 3418e974be1c5b52b3fe4bcdcca8fa6dd4bfcc57
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97404565"
---
# <a name="syspdw_diag_sessions-transact-sql"></a>sys.pdw_diag_sessions (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Contient des informations sur les différentes sessions de diagnostic qui ont été créées sur le système.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar(255)**|Nom de la session de diagnostic.<br /><br /> Clé pour cette vue.||  
|**xml_data**|**nvarchar(4000)**|Charge utile XML décrivant la session.||  
|**is_active**|**bit**|Indicateur qui spécifie si l’indicateur est actif.||  
|**host_address**|**nvarchar(255)**|Adresse de l’ordinateur hébergeant la définition de session (nœud de contrôle).||  
|**principal_id**|**int**|ID de l’utilisateur qui a créé la session au niveau de la base de données.||  
|**database_id**|**int**|ID de la base de données qui est l’étendue de la session de diagnostic.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue Azure Synapse Analytics et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
