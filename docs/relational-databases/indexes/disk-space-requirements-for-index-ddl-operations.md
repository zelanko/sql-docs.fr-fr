---
title: "Espace disque n&#233;cessaire pour les op&#233;rations DDL d&#39;index | Microsoft Docs"
ms.custom: ""
ms.date: "02/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-indexes"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "espace disque [SQL Server], index"
  - "espace disque des index [SQL Server]"
  - "espace [SQL Server], index"
  - "index [SQL Server], espace disque nécessaire"
  - "espace disque temporaire [SQL Server]"
ms.assetid: 35930826-c870-44c1-a966-a6a4638f62ef
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Espace disque n&#233;cessaire pour les op&#233;rations DDL d&#39;index
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  L'espace disque est un élément important à prendre en compte lors de la création, de la reconstruction ou de la suppression d'index. Un espace disque inadéquat peut réduire les performances, voire entraîner l'échec de l'opération d'index. Cette rubrique propose des informations générales qui peuvent vous aider à déterminer la quantité d'espace disque nécessaire pour les opérations DDL d'index.  
  
## Opérations d'index ne nécessitant pas d'espace disque supplémentaire  
 Les opérations d'index suivantes ne nécessitent pas d'espace disque supplémentaire :  
  
-   ALTER INDEX REORGANIZE ; un espace journal est toutefois nécessaire.  
  
-   DROP INDEX lors de la suppression d'un index non-cluster.  
  
-   DROP INDEX lors de la suppression d'un index cluster hors ligne sans spécifier la clause MOVE TO et qu'il n'existe pas d'index non-cluster.  
  
-   CREATE TABLE (contraintes PRIMARY KEY ou UNIQUE)  
  
## Opérations d'index nécessitant de l'espace disque supplémentaire  
 Toutes les autres opérations DDL d'index nécessitent de l'espace disque temporaire supplémentaire lors de l'exécution de l'opération ainsi que de l'espace disque permanent pour stocker la ou les nouvelles structures d'index.  
  
 Lorsqu'une nouvelle structure d'index est créée, de l'espace disque est nécessaire pour l'ancienne structure (source) et la nouvelle (cible) dans les fichiers et groupes de fichiers appropriés. L'ancienne structure n'est pas désallouée aussi longtemps que la transaction de création d'index n'est pas validée.  
  
 Les opérations DDL d'index suivantes créent de nouvelles structures d'index et nécessitent de l'espace disque supplémentaire :  
  
-   CREATE INDEX  
  
-   CREATE INDEX WITH DROP_EXISTING  
  
-   ALTER INDEX REBUILD  
  
-   ALTER TABLE ADD CONSTRAINT (PRIMARY KEY ou UNIQUE)  
  
-   ALTER TABLE DROP CONSTRAINT (PRIMARY KEY ou UNIQUE) lorsque la contrainte est basée sur un index cluster  
  
-   DROP INDEX MOVE TO (concerne uniquement les index cluster)  
  
## Espace disque temporaire à des fins de tri  
 Outre l'espace disque nécessaire pour les structures source et cible, de l'espace disque temporaire est nécessaire à des fins de tri, à moins que l'optimiseur de requête trouve un plan d'exécution ne nécessitant pas de tri.  
  
 En cas de tri, celui-ci s'applique à un nouvel index à la fois. Par exemple, lorsque vous reconstruisez un index cluster et des index non-cluster associés dans une seule instruction, les index sont triés un après l'autre. La quantité d'espace disque temporaire supplémentaire nécessaire pour le tri doit par conséquent correspondre à l'index le plus volumineux traité. Il s'agit généralement de l'index cluster.  
  
 Si l’option SORT_IN_TEMPDB a la valeur ON, l’index le plus volumineux doit tenir dans **tempdb**. Bien que cette option augmente la quantité d’espace disque temporaire utilisée pour créer un index, elle peut réduire le temps nécessaire pour créer un index quand **tempdb** ne se trouve pas sur le même ensemble de disques que la base de données utilisateur.  
  
 Si l'option SORT_IN_TEMPDB est définie sur OFF (par défaut) chaque index, y compris les index partitionnés, est stocké sur l'espace disque de destination et de l'espace disque n'est nécessaire que pour les nouvelles structures d'index.  
  
 Pour obtenir un exemple de calcul de l’espace disque, consultez [Exemple d’espace disque d’un index](../../relational-databases/indexes/index-disk-space-example.md).  
  
## Espace disque temporaire pour les opérations d'index en ligne  
 L'exécution d'opérations d'index en ligne nécessite de l'espace disque temporaire supplémentaire.  
  
 Lors de la création, reconstruction ou suppression d'un index cluster, un index non-cluster temporaire est créé pour mapper les anciens signets sur les nouveaux. Si l’option SORT_IN_TEMPDB a la valeur ON, cet index temporaire est créé dans **tempdb**. En revanche, si elle est définie sur OFF, le même groupe de fichiers ou schéma de partition que l'index cible est utilisé. L'index de mappage temporaire contient un enregistrement pour chaque ligne de la table et son contenu constitue un lien entre les anciennes et les nouvelles colonnes à signets, y compris les indicateurs d'unicité et les identificateurs d'enregistrement ; il ne comprend qu'une seule copie de chaque colonne utilisée dans les deux signets. Pour plus d’informations sur les opérations en ligne sur les index, consultez [Exécuter des opérations en ligne sur les index](../../relational-databases/indexes/perform-index-operations-online.md).  
  
> [!NOTE]  
>  L'option SORT_IN_TEMPDB ne peut pas être définie pour les instructions DROP INDEX. L'index de mappage temporaire est toujours créé dans le même groupe de fichiers ou schéma de partition que l'index cible.  
  
 Les opérations d'index en ligne utilisent le contrôle de version de ligne pour isoler l'opération d'index des effets des modifications d'autres transactions. Ceci permet d'éviter de demander des verrous partagés sur des lignes qui ont été lues. Les opérations simultanées de suppression et de mise à jour d’utilisateur lors d’opérations d’index en ligne nécessitent de l’espace pour les enregistrements de version dans **tempdb**. Pour plus d’informations, consultez [Exécuter des opérations en ligne sur les index](../../relational-databases/indexes/perform-index-operations-online.md).  
  
## Tâches associées  
 [Exemple d'espace disque d'un index](../../relational-databases/indexes/index-disk-space-example.md)  
  
 [Espace disque du journal des transactions pour les opérations d'index](../../relational-databases/indexes/transaction-log-disk-space-for-index-operations.md)  
  
 [Estimer la taille d'une table](../../relational-databases/databases/estimate-the-size-of-a-table.md)  
  
 [Estimer la taille d'un index cluster](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)  
  
 [Estimer la taille d'un index non-cluster](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)  
  
 [Estimer la taille d'un segment de mémoire](../../relational-databases/databases/estimate-the-size-of-a-heap.md)  
  
## Contenu connexe  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
  
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)  
  
 [DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)  
  
 [Spécifier un facteur de remplissage pour un index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)  
  
 [Réorganiser et reconstruire des index](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)  
  
  