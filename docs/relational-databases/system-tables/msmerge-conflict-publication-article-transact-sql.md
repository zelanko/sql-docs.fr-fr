---
title: MSmerge_conflict_&lt;publication&gt;_&lt;article(Transact-SQL)|&gt; Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_conflict_publication_article_TSQL
- MSmerge_conflict_publication_article
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_conflict_publication_article system table
ms.assetid: dc4490b4-02d8-4dfc-98f5-0cf8de8e11be
author: stevestein
ms.author: sstein
ms.openlocfilehash: 342b0f51fb4f68945f6ab8c4b511c5299acfba49
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893586"
---
# <a name="msmerge_conflict_ltpublicationgt_ltarticlegt-transact-sql"></a>Article\_&lt;\_surla&gt;publicationde&lt;conflitsMSmerge (Transact-SQL)\_&gt;
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La **table\_d'\__Articles_ depublication\_de conflit MSmerge** contient des informations sur les lignes qui sont en conflit ou pour les modifications de ligne qui ont été annulées pour la convergence des données. Il existe une table de conflits pour chaque table répliquée dans une publication, où le nom de la table de conflits est ajouté au nom de la publication et à celui de l'article. Ces tables de conflits spécifiques aux articles existent dans la base de données utilisée pour la journalisation des conflits ; il s'agit généralement de la base de données de publication, mais il peut s'agir de la base de données d'abonnement si la journalisation des conflits est décentralisée.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**_nom\_de\_colonne de l’article_**|**variable**|Représente une colonne d'une table répliquée. Cette table système contient une colonne pour chaque colonne de l'article de la table.|  
|**rowguid**|**uniqueidentifier**|Identificateur de ligne de la ligne en conflit.|  
|**ModifiedDate**|**datetime**|Heure d'occurrence du conflit.|  
|**ID\_de\_source de source d’origine**|**uniqueidentifier**|Abonnement pour lequel la modification de ligne a été annulée ou qui a perdu le conflit.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables &#40;de réplication Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
