---
title: Nettoyer les métadonnées de fusion (procédures stockées de réplication)
description: Nettoyez programmatiquement les données dans les tables de réplication de fusion à l'aide de procédures stockées de réplication
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3b11994be2889cce85b2be739dad5e991a5c55b3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897941"
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a>Nettoyer les métadonnées de fusion (programmation Transact-SQL de la réplication)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Les métadonnées de réplication de fusion sont nettoyées régulièrement par l'Agent de fusion en fonction du paramètre de rétention de la publication. Cela se produit sur le serveur de publication et l'Abonné dans les tables système [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), [MSmerge_past_partition_mappings](../../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md)et [MSmerge_current_partition_mappings](../../../relational-databases/system-tables/msmerge-current-partition-mappings.md) . Vous pouvez également nettoyer par programmation les données dans ces tables à l'aide de procédures stockées de réplication.  
  
### <a name="to-manually-clean-up-merge-metadata"></a>Pour nettoyer les métadonnées de fusion manuellement  
  
1.  Sur la base de données de publication du serveur de publication, exécutez [sp_mergemetadataretentioncleanup](../../../relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql.md).  
  
2.  (Facultatif) Notez le nombre de lignes supprimées à l’étape 1 des tables système [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md)et [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), retournées respectivement dans les paramètres de sortie `@num_genhistory_rows`, `@num_contents_rows` et `@num_tombstone_rows`.  
  
3.  Répétez les étapes 1 et 2 sur l'Abonné à nettoyer les métadonnées de la base de données d'abonnement.  
  
## <a name="see-also"></a>Voir aussi  
 [Expiration et désactivation des abonnements](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
