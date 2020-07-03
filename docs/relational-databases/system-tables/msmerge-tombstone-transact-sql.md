---
title: MSmerge_tombstone (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_tombstone_TSQL
- MSmerge_tombstone
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_tombstone system table
ms.assetid: 8b3fc7bf-729b-40f2-8a26-e7dfbe8ddb38
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e46010c61b8646763e3ca8e07e46e6d62864965d
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889700"
---
# <a name="msmerge_tombstone-transact-sql"></a>MSmerge_tombstone (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  La table **MSmerge_tombstone** contient des informations sur les lignes supprimées et permet la propagation des suppressions aux autres abonnés. Cette table est stockée dans les bases de données de publication et d’abonnement.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**rowguid**|**uniqueidentifier**|Identificateur de ligne.|  
|**tablenick**|**int**|Surnom de la table.|  
|**type**|**tinyint**|Type de suppression :<br /><br /> 1 = suppression de l'utilisateur<br /><br /> 5 = exclusion de la ligne de la partition filtrée<br /><br /> 6 = suppression par le système|  
|**lignage**|**varbinary (249)**|Indique la version de l'enregistrement objet de la suppression, ainsi que les mises à jour connues lors de la suppression. Permet d'obtenir la résolution cohérente d'un conflit lorsqu'un abonné modifie une ligne alors qu'un autre abonné est en train de la supprimer.|  
|**toute**|**int**|Est affecté lors de la suppression d'une ligne. Si un abonné demande la génération N, seuls les objets tombstone avec la génération >= N sont envoyés.|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Identifie l'enregistrement logique auquel une ligne supprimée appartient.|  
|**logical_record_lineage**|**Varbinary (501)**|Paires nom de l'Abonné/numéro de version permettant de gérer un historique des suppressions pour l'enregistrement logique auquel cette ligne appartient.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
