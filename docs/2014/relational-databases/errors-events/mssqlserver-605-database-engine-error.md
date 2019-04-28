---
title: MSSQLSERVER_605 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 605 (Database Engine error)
ms.assetid: d8d3a22e-1ff8-48a4-891f-4c8619437e24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f8d49bcc6b25b9d66d8aba77c2300549c682a879
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62867705"
---
# <a name="mssqlserver605"></a>MSSQLSERVER_605
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|605|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|WRONGPAGE|  
|Texte du message|La tentative d'extraction de la page logique %S_PGID dans la base de données %d a échoué. Elle appartient à l'unité d'allocation %I64d et non à %I64d.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur est généralement synonyme d'altération de page ou d'allocation dans la base de données spécifiée. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] détecte l’altération en suivant les liens des pages ou en utilisant la page IAM (Index Allocation Map) au cours de la lecture de pages appartenant à une table. Toutes les pages allouées à une table doivent appartenir à l'une des unités d'allocations associées à la table. Si l'ID d'unité d'allocation contenu dans l'en-tête de page ne correspond pas à un ID d'unité d'allocation associé à la table, cette exception est générée. Le premier ID d'unité d'allocation listé dans le message d'erreur est l'ID présent dans l'en-tête de page et le second est l'ID associé à la table.  
  
 **Erreurs d’altération des données**  
  
 Un niveau de gravité de 21 indique une potentielle altération des données. Les causes possibles sont les suivantes : chaîne de page endommagée, page IAM altérée ou entrée non valide dans la vue de catalogue [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) pour l’objet concerné. Ces erreurs sont souvent causées par une défaillance du matériel ou du pilote de disque.  
  
 **Erreurs temporaires**  
  
 Un niveau de gravité de 12 indique une potentielle erreur temporaire, c'est-à-dire qu'elle se produit dans le cache mais n'indique aucune altération des données sur le disque. Les erreurs 605 temporaires peuvent être causées par les conditions suivantes :  
  
-   Le système d'exploitation informe prématurément [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qu'une opération d'E/S vient de se terminer. Le message d'erreur est affiché même si aucune altération des données n'a lieu.  
  
 Une requête est exécutée avec l'indicateur d'optimiseur NOLOCK ou le niveau d'isolement des transactions est défini avec la valeur READ UNCOMMITTED. Lorsqu'une requête utilisant NOLOCK ou READ UNCOMMITTED tente de lire des données qui ont été déplacées ou modifiées par un autre utilisateur, une erreur 605 se produit. Pour vérifier qu'il s'agit bien d'une erreur 605 temporaire, réexécutez la requête ultérieurement. Pour plus d’informations, consultez l’article [235880](https://support.microsoft.com/kb/235880/en-us): « Vous recevez un message d’erreur « Erreur 605 » lorsque vous exécutez une requête avec l’indicateur d’optimiseur NOLOCK ou que vous définissez le niveau d’isolation de transaction READ UNCOMMITTED dans SQL Server ».  
  
 Généralement, si l'erreur se produit lors de l'accès aux données, mais que les opérations DBCC CHECKDB qui suivent s'exécutent sans erreur, l'erreur 605 était probablement temporaire.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si l'erreur 605 n'est pas temporaire, le problème est grave et doit être résolu en effectuant les opérations suivantes :  
  
1.  Identifiez les tables associées aux unités d'allocation spécifiées dans le message en exécutant la requête suivante. Remplacez `allocation_unit_id` par les unités d'allocation spécifiées dans le message d'erreur.  
  
     USE`database_name`;  
  
     GO  
  
     SELECT au.allocation_unit_id, OBJECT_NAME(p.object_id) AS table_name, fg.name AS filegroup_name,  
  
     au.type_desc allocation_type AS, au.data_pages, partition_number  
  
     FROM sys.allocation_units AS au  
  
     JOIN sys.partitions AS p ON au.container_id = p.partition_id  
  
     JOIN sys.filegroups AS fg ON fg.data_space_id = au.data_space_id  
  
     WHERE au.allocation_unit_id = `allocation_unit_id` OR au.allocation_unit_id = `allocation_unit_id`  
  
     ORDER BY au.allocation_unit_id;  
  
     GO  
  
2.  Exécutez DBCC CHECKTABLE sans clause REPAIR sur la table associée au deuxième ID d'unité d'allocation spécifié dans le message d'erreur.  
  
3.  Exécutez DBCC CHECKDB sans clause REPAIR dès que possible pour déterminer le niveau d'altération des données dans l'ensemble de la base de données.  
  
4.  Dans le journal des erreurs, recherchez d'autres erreurs qui accompagnent souvent une erreur 605 et examinez le journal des événements Windows pour détecter d'éventuels problèmes système ou matériels associés. Corrigez les éventuels problèmes matériels contenus dans les journaux.  
  
 Si le problème n'est pas matériel, effectuez l'une des opérations suivantes :  
  
1.  Restaurez la base de données à partir d'une sauvegarde saine. Vous pouvez optimiser la fonctionnalité de sauvegarde de la restauration de pages pour restaurer uniquement les pages endommagées.  
  
2.  Exécutez DBCC CHECKDB avec la clause REPAIR recommandée par l'opération DBCC CHECKDB effectuée à l'étape 3 pour réparer l'endommagement. Si l'exécution de DBCC CHECKDB avec une des clauses REPAIR ne résout pas le problème, contactez l’assistance technique. Gardez le résultat de DBCC CHECKDB à disposition pour consultation ultérieure.  
  
    > [!CAUTION]  
    >  Si vous n'êtes pas sûr de l'effet de DBCC CHECKDB avec une clause REPAIR sur vos données, contactez l'assistance technique avant d'exécuter cette instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [DBCC CHECKTABLE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql)  
  
  
