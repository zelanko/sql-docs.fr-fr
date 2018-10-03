---
title: Instructions d’utilisation des index sur les Tables mémoire optimisées | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- hash indexes
ms.assetid: 16ef63a4-367a-46ac-917d-9eebc81ab29b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 514b6c8fedb50417b8c4060cb45e73bfa88fdddb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094361"
---
# <a name="guidelines-for-using-indexes-on-memory-optimized-tables"></a>Instructions pour utiliser les index sur les tables optimisées en mémoire
  Les index sont utilisés pour accéder efficacement aux données dans les tables [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Spécifier les index appropriés peut améliorer considérablement les performances des requêtes. Par exemple, considérez la requête :  
  
```tsql  
SELECT c1, c2 FROM t WHERE c1 = 1;  
```  
  
 S'il n'y a pas d'index sur la colonne c1, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] doit analyser la totalité de la table t, puis filtrer sur les lignes qui répondent à la condition c1=1. Toutefois, si t a un index sur la colonne c1, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut rechercher directement la valeur 1 et récupérer les lignes.  
  
 Lorsque vous recherchez des enregistrements ayant une valeur spécifique, ou une plage de valeurs, dans une ou plusieurs colonnes de la table, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut utiliser un index sur ces colonnes pour localiser rapidement les enregistrements correspondants. Les tables sur disque et optimisées en mémoire tirent parti des index. Il existe, toutefois, certaines différences entre les structures d'index, dont il faut tenir compte lorsqu'on utilise des tables optimisées en mémoire. (Les index des tables optimisées en mémoire sont appelés des index optimisés en mémoire.) Parmi les principales différences, citons :  
  
-   Index optimisés en mémoire doivent être créés avec [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql). Les index sur disque peuvent être créés avec `CREATE TABLE` et `CREATE INDEX`.  
  
-   Les index optimisés en mémoire existent uniquement en mémoire. Les structures d'index ne sont pas conservées sur le disque et les opérations d'index ne sont pas consignées dans le journal des transactions. La structure de l'index est créée lorsque la table optimisée en mémoire est créée dans la mémoire, au cours de CREATE TABLE et lors du démarrage de la base de données.  
  
-   Les index optimisés en mémoire sont couvrants. La couverture signifie que toutes les colonnes sont virtuellement incluses dans l'index, et que les recherches de signets ne sont pas nécessaires pour les tables optimisées en mémoire. Au lieu d'une référence à la clé primaire, les index optimisés en mémoire contiennent simplement un pointeur de mémoire sur la ligne réelle dans la structure de données de la table.  
  
-   Les concepts de fragmentation et de fillfactor ne s'appliquent pas aux index optimisés en mémoire. Dans les index sur disque, la fragmentation fait référence aux pages de l'arbre B (B-tree) écrites sur le disque dans le désordre. Les index optimisés en mémoire ne sont pas écrits sur le disque, ou lus à partir de celui-ci. Fillfactor dans les index d'arbre B (B-tree) sur disque fait référence au degré selon lequel les structures des pages physiques sont remplies avec des données réelles. Les structures d'index optimisés en mémoire n'ont pas de pages de taille fixe.  
  
 Il existe deux types d'index optimisés en mémoire :  
  
-   Les index de hachage non cluster, qui sont faits pour les recherches de point. Pour plus d’informations sur les index de hachage, consultez [index de hachage](hash-indexes.md).  
  
-   Les index non cluster, qui sont faits pour les analyses de plage et les analyses triées.  
  
 Avec un index de hachage, les données sont accédées via une table de hachage en mémoire. Les index de hachage n'ont pas de pages et sont toujours d'une taille fixe. Toutefois, un index de hachage peut avoir des compartiments de hachage vides, ce qui aboutit à un espace gaspillé limité. Les valeurs retournées par une requête utilisant un index de hachage ne sont pas triées. Les index de hachage sont optimisés pour les recherches d'index sur les prédicats d'égalité et prennent également en charge les analyses complètes d'index.  
  
 Les index non cluster (pas les index de hachage) prennent en charge toutes les opérations prises en charge par les index de hachage en plus des opérations de recherche sur les prédicats d'inégalité comme supérieur ou inférieur à, ainsi que l'ordre de tri. Les lignes peuvent être récupérées selon l'ordre spécifié à la création de l'index. Si l'ordre de tri de l'index représente l'ordre de tri requis pour une requête spécifique, par exemple si la clé d'index correspond à la clause ORDER BY, il n'est pas nécessaire de trier les lignes dans le cadre de l'exécution de la requête. Les index non cluster optimisés en mémoire sont unidirectionnels ; ils ne prennent pas en charge la récupération de lignes dans un ordre de tri qui est l'inverse de l'ordre de tri de l'index. Par exemple, pour un index spécifié sous la forme (c1 ASC), il n'est pas possible d'analyser l'index dans l'ordre inverse, sous la forme (c1 DESC).  
  
 Chaque index consomme de la mémoire. Les index de hachage consomment une quantité fixe de mémoire, en fonction du nombre de compartiments. Pour les index non cluster, la consommation de mémoire est une fonction du nombre de lignes et de la taille des colonnes clés d'index, avec une surcharge supplémentaire dépendant de la charge de travail. La mémoire pour les index optimisés en mémoire est en plus et est distincte de la mémoire utilisée pour stocker les lignes dans les tables optimisées en mémoire.  
  
 Les valeurs de clé en double partagent le même compartiment de hachage. Si un index de hachage contient plusieurs clés en double, les chaînes de hachage longues qui en résulte auront un impact sur les performances. Les collisions de hachage, qui se produisent dans un index de hachage, réduisent également les performances dans ce scénario. Pour cette raison, si le nombre de clés d’index uniques est au moins 100 fois plus petit que le nombre de lignes, vous pouvez réduire le risque de collisions de hachage en rendant le compartiment compter beaucoup plus volumineux (au moins huit fois le nombre de clés d’index uniques ; consultez [déterminer le Nombre de compartiments correct pour les index de hachage](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) pour plus d’informations) ou vous pouvez éliminer les collisions de hachage en utilisant un index non cluster.  
  
## <a name="determining-which-indexes-to-use-for-a-memory-optimized-table"></a>Détermination des index à utiliser pour une table optimisée en mémoire  
 Chaque table optimisée en mémoire doit avoir au moins un index. Notez que chaque contrainte PRIMARY KEY crée implicitement un index. Par conséquent, si une table possède une clé primaire, elle possède un index. Une clé primaire est requise pour une table optimisée en mémoire durable.  
  
 Lors de l'interrogation d'une table optimisée en mémoire, les index de hachage s'avèrent plus efficaces si la clause de prédicat contient uniquement des prédicats d'égalité. Le prédicat doit inclure toutes les colonnes dans la clé d'index de hachage. Un index de hachage rétablit une analyse en fonction d'un prédicat d'inégalité.  
  
 Une colonne dans une table optimisée en mémoire peut faire partie d'un index de hachage et d'un index non cluster.  
  
 Lors de l'interrogation d'une table optimisée en mémoire avec des prédicats d'inégalité, les index non cluster s'avèrent plus efficaces que les index de hachage non cluster.  
  
 L'index de hachage nécessite une clé (pour hacher) pour rechercher dans l'index. Si une clé d'index est constituée de deux colonnes et vous indiquez uniquement la première colonne, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne dispose pas d'une clé complète pour hacher. Cela génère un plan de requête d'analyse d'index. L'utilisation détermine les colonnes qui doivent être indexées.  
  
 Lorsqu'une colonne dans un index non cluster a la même valeur dans plusieurs de lignes (les colonnes clés d'index ont plusieurs valeurs dupliquées), cela peut nuire aux performances lors des mises à jour, des insertions et des suppressions.  Une façon d'améliorer les performances dans cette situation consiste à ajouter une autre colonne à l'index non cluster.  
  
### <a name="operations-on-memory-optimized-and-disk-based-indexes"></a>Opérations sur les index optimisés en mémoire et les index sur disque.  
  
|Opération|Index de hachage non cluster optimisé en mémoire|Index non cluster optimisé en mémoire|Index sur disque|  
|---------------|-------------------------------------------------|------------------------------------------|-----------------------|  
|Analyse d'index, récupère toutes les lignes de la table.|Oui|Oui|Oui|  
|Recherche d'index sur les prédicats d'égalité (=).|Oui<br /><br /> (Clé complète requise.)|Oui <sup>1</sup>|Oui|  
|Recherche d’index sur les prédicats d’inégalité (>, <, \<=, > =, BETWEEN).|Non (résulte dans une analyse d'index)|Oui <sup>1</sup>|Oui|  
|Récupérez les lignes selon un ordre de tri qui correspond à la définition de l'index.|non|Oui|Oui|  
|Récupérez les lignes selon un ordre de tri inverse par rapport à la définition de l'index.|non|non|Oui|  
  
 Dans la table, Oui signifie que l'index peut traiter la demande et Non signifie que l'index ne peut pas être utilisé pour répondre à cette demande.  
  
 <sup>1</sup> pour un index non cluster optimisé en mémoire, la clé complète n’est pas nécessaire pour effectuer une recherche d’index. Même si, en fonction de l'ordre des colonnes de la clé d'index, une analyse se produit si une valeur d'une colonne vient après une colonne manquante.  
  
## <a name="index-count"></a>Nombre d'index  
 Une table optimisée en mémoire peut avoir jusqu'à 8 index, y compris l'index créé avec la clé primaire.  
  
 En ce qui concerne le nombre d'index créés sur une table optimisée en mémoire, tenez compte des éléments suivants :  
  
-   Spécifiez les index dont vous avez besoin lors de la création de la table. Vous ne pouvez pas créer d'index pour une table optimisée en mémoire après la création de la table. Si vous souhaitez ajouter un index sur une table optimisée en mémoire, supprimez et recréez cette table.  
  
-   Ne créez pas d'index que vous utilisez rarement :  
  
     Le nettoyage de la mémoire fonctionne mieux si tous les index de la table sont utilisés fréquemment. Les index rarement utilisés peuvent entraîner un fonctionnement non optimal du système de nettoyage de la mémoire pour les anciennes versions de ligne.  
  
## <a name="creating-a-memory-optimized-index-code-samples"></a>Création d'un index mémoire optimisé : exemples de code  
 Index de hachage au niveau des colonnes :  
  
```tsql  
CREATE TABLE t1   
   (c1 INT NOT NULL INDEX idx HASH WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 Index de hachage au niveau des tables :  
  
```tsql  
CREATE TABLE t1_1   
   (c1 INT NOT NULL,   
   INDEX IDX HASH (c1) WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 Index de hachage de clé primaire au niveau des colonnes :  
  
```tsql  
CREATE TABLE t2   
   (c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 Index de hachage de clé primaire au niveau des tables :  
  
```tsql  
CREATE TABLE t2_2   
   (c1 INT NOT NULL,   
   PRIMARY KEY NONCLUSTERED HASH (c1) WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 Index non cluster au niveau de la colonne :  
  
```tsql  
CREATE TABLE t3   
   (c1 INT NOT NULL INDEX ID)   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 Index non cluster au niveau de la table :  
  
```tsql  
CREATE TABLE t3_3   
   (c1 INT NOT NULL,   
   INDEX IDX NONCLUSTERED (c1))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 Index non cluster de clé primaire au niveau de la colonne :  
  
```tsql  
CREATE TABLE t4   
   (c1 INT NOT NULL PRIMARY KEY NONCLUSTERED)   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 Index non cluster de clé primaire de niveau table :  
  
```tsql  
CREATE TABLE t4_4   
   (c1 INT NOT NULL,   
   PRIMARY KEY NONCLUSTERED (c1))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 Index multicolonne défini après la définition des colonnes :  
  
```tsql  
create table t (  
       a int not null constraint ta primary key nonclustered,  
       b int not null,  
       c int not null,  
       d int not null,  
       index idx_t_b_c_d nonclustered (b, c asc, d desc)  
) with (memory_optimized = on, durability = SCHEMA_AND_DATA)  
go  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Index des Tables optimisées en mémoire](../relational-databases/in-memory-oltp/memory-optimized-tables.md)   
 [Déterminer le nombre de compartiments Correct pour les index de hachage](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md)   
 [Index de hachage](hash-indexes.md)  
  
  
