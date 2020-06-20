---
title: Nettoyer les métadonnées de fusion (programmation Transact-SQL de la réplication) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 5a2306db72fd3f0098e18ff058796a5498eafcac
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85043325"
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a>Nettoyer les métadonnées de fusion (programmation Transact-SQL de la réplication)
  Les métadonnées de réplication de fusion sont nettoyées régulièrement par l'Agent de fusion en fonction du paramètre de rétention de la publication. Cela se produit sur le serveur de publication et l'Abonné dans les tables système [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)et [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) . Vous pouvez également nettoyer par programmation les données dans ces tables à l'aide de procédures stockées de réplication.  
  
### <a name="to-manually-clean-up-merge-metadata"></a>Pour nettoyer les métadonnées de fusion manuellement  
  
1.  Sur la base de données de publication du serveur de publication, exécutez [sp_mergemetadataretentioncleanup](/sql/relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql).  
  
2.  Facultatif Notez le nombre de lignes supprimées à l’étape 1 dans les tables système [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)et [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql) , retournées respectivement dans les **@num_genhistory_rows** paramètres de **@num_contents_rows** sortie, et **@num_tombstone_rows** .  
  
3.  Répétez les étapes 1 et 2 sur l'Abonné à nettoyer les métadonnées de la base de données d'abonnement.  
  
## <a name="see-also"></a>Voir aussi  
 [Expiration et désactivation des abonnements](../subscription-expiration-and-deactivation.md)  
  
  
