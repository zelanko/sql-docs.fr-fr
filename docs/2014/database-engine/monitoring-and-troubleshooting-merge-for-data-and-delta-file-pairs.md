---
title: Surveillance et dépannage de la fusion pour les paires de fichiers de données et Delta | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a8b0bacc-4d2c-42e4-84bf-1a97e0bd385b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c7a13345da45d7e6c31a53bc51371306da444a96
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "75228181"
---
# <a name="monitoring-and-troubleshooting-merge-for-data-and-delta-file-pairs"></a>Surveiller et dépanner la fusion de paires de fichiers de données et de fichiers delta
  L'OLTP en mémoire utilise une stratégie de fusion pour fusionner des paires de fichiers de données et delta automatiquement. Vous ne pouvez pas désactiver l'activité de fusion.  
  
 Surveillez les paires de fichiers de données et delta, comme suit :  
  
-   Comparez la taille du stockage en mémoire à la taille globale du stockage. Si le stockage a une taille disproportionnée, il est possible que la fusion ne se déclenche pas. Pour plus d'informations  
  
-   Examinez l’espace utilisé dans les fichiers de données et Delta à l’aide de [sys. dm_db_xtp_checkpoint_files &#40;&#41;Transact-SQL](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql) pour voir si la fusion n’est pas déclenchée quand elle le devrait.  
  
## <a name="performing-a-manual-merge"></a>Exécution d'une fusion manuelle  
 Vous pouvez utiliser [sys. sp_xtp_merge_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql) pour effectuer une fusion manuelle.  
  
 Utilisez la requête suivante pour récupérer les informations sur les fichiers de données et delta :  
  
```sql  
select checkpoint_file_id, file_type_desc, internal_storage_slot, file_size_in_bytes, file_size_used_in_bytes,   
inserted_row_count, deleted_row_count, lower_bound_tsn, upper_bound_tsn   
from sys.dm_db_xtp_checkpoint_files  
where state = 1  
order by file_type_desc, upper_bound_tsn  
```  
  
 Supposons que vous avez trouvé trois fichiers de données qui n’ont pas été fusionnés. Utilisez la valeur `lower_bound_tsn` du premier fichier de données et la valeur `upper_bound_tsn` du dernier fichier de données pour émettre la commande suivante :  
  
```sql  
exec sys.sp_xtp_merge_checkpoint_files 'H_DB',  12345, 67890  
```  
  
 Supposez que les trois paires de fichiers de données et delta comportent chacune 15 836 lignes et 5 279 lignes supprimées. Une fois la fusion terminée, le nouveau fichier de données contient 31 872 lignes et 0 ligne supprimée. La taille du nouveau fichier de données peut être beaucoup plus volumineuse que la taille initialement allouée de 128 Mo. Cela est dû au fait que la fusion manuelle remplace la stratégie de fusion et force la fusion des fichiers demandés.  
  
 La [transition de l’état du blog des fichiers de point de contrôle dans les bases de données avec des tables mémoire optimisées](https://blogs.technet.com/b/dataplatforminsider/archive/2014/01/23/state-transition-of-checkpoint-files-in-databases-with-memory-optimized-tables.aspx) décrit la transition d’état des paires de fichiers de données et Delta de la création à la garbage collection.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et gestion du stockage des objets mémoire optimisés](../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
