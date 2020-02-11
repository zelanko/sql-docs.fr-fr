---
title: MSmerge_metadataaction_request (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_metadataaction_request
- MSmerge_metadataaction_request_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_metadataaction_request system table
ms.assetid: cd31a114-900a-4218-ab58-d959e547c647
author: stevestein
ms.author: sstein
ms.openlocfilehash: 09f3fa61a1f79e98b8cd3330a03361b1b6a5c507
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106370"
---
# <a name="msmerge_metadataaction_request-transact-sql"></a>MSmerge_metadataaction_request (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table **MSmerge_metadataaction_request** stocke une ligne pour chaque action de compensation requise. À l’aide de la synchronisation Web, si une erreur se produit et que la synchronisation doit être retentée, une entrée est créée dans **MSmerge_metadataaction_request**. Lors de la phase de téléchargement de la fusion suivante, les demandes de tous les articles appartenant à la publication à synchroniser sont extraites de cette table et téléchargées. Une fois la synchronisation terminée avec succès, la ligne correspondante dans la table **MSmerge_metadataaction_request** est supprimée. Cette table est stockée dans la base de données de publication du serveur de publication et dans la base de données d'abonnement de l'Abonné.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Surnom de la table publiée.|  
|**GuidLigne**|**uniqueidentifier**|Identificateur de ligne pour la ligne concernée.|  
|**transactionnel**|**tinyint**|Définit l'action de compensation nécessaire.|  
|**toute**|**bigint**|Valeur de la génération pour laquelle l'action de compensation est nécessaire.|  
|**remplacé**|**int**|À usage interne uniquement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [Synchronisation web pour la réplication de fusion](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
