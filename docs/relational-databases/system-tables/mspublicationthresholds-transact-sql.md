---
title: MSpublicationthresholds (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- mspublicationthresholds
- mspublicationthresholds_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublicationthresholds system table
ms.assetid: 9da3879f-b1f4-4ab4-abd4-a9a8ac395eba
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7b5ab784ea0c8cc34068773739c2a818a11aa5f1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85751616"
---
# <a name="mspublicationthresholds-transact-sql"></a>MSpublicationthresholds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  La table **MSpublicationthresholds** est utilisée pour suivre les métriques de performances de réplication d’une publication, avec une ligne pour chaque valeur de seuil surveillée. Cette table est stockée dans la base de données de distribution.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publication_id**|**int**|Identifie la publication pour laquelle un seuil a été défini.|  
|**metric_id**|**int**|Identifie une mesure de performance de réplication surveillée telle qu’elle est définie dans la table système [MSreplmonthresholdmetrics](../../relational-databases/system-tables/msreplmonthresholdmetrics-transact-sql.md) .|  
|**value**|**sql_variant**|Valeur de seuil de la mesure surveillée.|  
|**shouldalert**|**bit**|La valeur **1** indique qu’une alerte doit être générée lorsque la mesure dépasse le seuil défini.|  
|**IsEnabled**|**bit**|La valeur **1** indique que l’analyse est activée pour cette mesure de performance de réplication.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
