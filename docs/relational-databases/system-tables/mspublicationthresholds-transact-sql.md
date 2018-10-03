---
title: MSpublicationthresholds (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- mspublicationthresholds
- mspublicationthresholds_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublicationthresholds system table
ms.assetid: 9da3879f-b1f4-4ab4-abd4-a9a8ac395eba
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 133bdbd53cf89b9ebf20260c867e22008b460aae
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47703087"
---
# <a name="mspublicationthresholds-transact-sql"></a>MSpublicationthresholds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSpublicationthresholds** table est utilisée pour effectuer le suivi des mesures de performances de réplication pour une publication, avec une ligne pour chaque valeur de seuil en cours d’analyse. Cette table est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publication_id**|**Int**|Identifie la publication pour laquelle un seuil a été défini.|  
|**metric_id**|**Int**|Identifie une mesure de performances de réplication surveillée telle que définie dans le [MSreplmonthresholdmetrics](../../relational-databases/system-tables/msreplmonthresholdmetrics-transact-sql.md) (table système).|  
|**value**|**sql_variant**|Valeur de seuil de la mesure surveillée.|  
|**shouldalert**|**bit**|La valeur **1** indique qu’une alerte doit être générée lorsque la mesure dépasse le seuil défini.|  
|**IsEnabled**|**bit**|La valeur **1** indique que la surveillance est activée pour cette métrique de performances de réplication.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
