---
title: "Nettoyer les m&#233;tadonn&#233;es de fusion (programmation Transact-SQL de la r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "métadonnées [réplication SQL Server]"
  - "sp_mergemetadataretentioncleanup"
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Nettoyer les m&#233;tadonn&#233;es de fusion (programmation Transact-SQL de la r&#233;plication)
  Les métadonnées de réplication de fusion sont nettoyées régulièrement par l'Agent de fusion en fonction du paramètre de rétention de la publication. Cela se produit sur l’éditeur et l’abonné dans la [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), [MSmerge_past_partition_mappings](../../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md), et [MSmerge_current_partition_mappings](../../../relational-databases/system-tables/msmerge-current-partition-mappings.md) tables système. Vous pouvez également nettoyer par programmation les données dans ces tables à l'aide de procédures stockées de réplication.  
  
### Pour nettoyer les métadonnées de fusion manuellement  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_mergemetadataretentioncleanup](../../../relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql.md).  
  
2.  (Facultatif) Notez le nombre de lignes supprimées dans l’étape 1 de la [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), et [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) tables système, retournées respectivement dans les **@num_genhistory_rows**, **@num_contents_rows**, et **@num_tombstone_rows** les paramètres de sortie.  
  
3.  Répétez les étapes 1 et 2 sur l'Abonné à nettoyer les métadonnées de la base de données d'abonnement.  
  
## Voir aussi  
 [Expiration et désactivation des abonnements](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  