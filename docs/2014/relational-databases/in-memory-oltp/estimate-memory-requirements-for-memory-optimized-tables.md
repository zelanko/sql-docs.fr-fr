---
title: Estimer les besoins en mémoire des tables optimisées en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5c5cc1fc-1fdf-4562-9443-272ad9ab5ba8
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: b0d22fd13abf68cd9eea1c21b135427161fbf8be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143276"
---
# <a name="estimate-memory-requirements-for-memory-optimized-tables"></a>Estimer les besoins en mémoire des tables mémoire optimisées
  Si vous créez une table [!INCLUDE[hek_2](../../includes/hek-2-md.md)] optimisée en mémoire ou migrez une table existante basée sur disque vers une table optimisée en mémoire, il est important d'estimer avec justesse les besoins en mémoire de chaque table, de façon à configurer le serveur avec suffisamment de mémoire. Cette section explique comment estimer la quantité de mémoire nécessaire pour accueillir les données d'une table mémoire optimisée.  
  
 Si vous envisagez d’effectuer une migration à partir de tables sur disque vers des tables optimisées en mémoire, avant de poursuivre la lecture de cette rubrique, consultez [Déterminer si une table ou une procédure stockée doit être déplacée vers l’OLTP en mémoire](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) pour obtenir des conseils sur les tables les plus judicieuses à faire migrer. Toutes les rubriques sous [Migration vers OLTP en mémoire](migrating-to-in-memory-oltp.md) fournissent des conseils sur la migration à partir de tables sur disque vers des tables optimisées en mémoire.  
  
## <a name="sections-in-this-topic"></a>Sections de cette rubrique  
  
-   [Exemple de table optimisée en mémoire](#bkmk_ExampleTable)  
  
-   [Mémoire pour la table](#bkmk_MemoryForTable)  
  
-   [Mémoire pour les index](#bkmk_IndexMeemory)  
  
-   [Mémoire pour le contrôle de version de ligne](#bkmk_MemoryForRowVersions)  
  
-   [Mémoire pour les variables de table](#bkmk_TableVariables)  
  
-   [Mémoire pour la croissance](#bkmk_MemoryForGrowth)  
  
##  <a name="bkmk_ExampleTable"></a> Exemple de table optimisée en mémoire  
 Prenons le schéma de table mémoire optimisée suivant :  
  
```tsql  
  
CREATE TABLE t_hk (  
col1 int NOT NULL PRIMARY KEY NONCLUSTERED,  
col2 int NOT NULL INDEX t1c2_index   
     HASH WITH (bucket_count = 5000000),  
col3 int NOT NULL INDEX t1c3_index   
     HASH WITH (bucket_count = 5000000),  
col4 int NOT NULL INDEX t1c4_index   
     HASH WITH (bucket_count = 5000000),  
col5 int NOT NULL INDEX t1c5_index NONCLUSTERED,  
col6 char (50) NOT NULL,  
col7 char (50) NOT NULL,   
col8 char (30) NOT NULL,   
col9 char (50) NOT NULL  
     WITH (memory_optimized = on)  
GO  
  
```  
  
 Ce schéma va permettre de déterminer la mémoire minimale requise pour cette table mémoire optimisée.  
  
##  <a name="bkmk_MemoryForTable"></a> Mémoire pour la table  
 Une ligne de table mémoire optimisée est composée de trois parties :  
  
-   **Horodateurs**   
    En-tête de ligne/horodateurs = 24 octets.  
  
-   **Pointeurs d’index**   
    Pour chaque index de hachage dans la table, chaque ligne a un pointeur d'adresse 8 octets vers la ligne suivante dans l'index.  Étant donné qu'il y a 4 index, chaque ligne alloue 32 octets pour les pointeurs d'index (pointeur de 8 octets pour chaque index).  
  
-   **Données**   
    La taille de la partie données de la ligne est déterminé en additionnant la taille du type pour chaque colonne de données.  Dans notre table, il y a cinq entiers de 4 octets, trois colonnes de type caractère de 50 octets et une colonne de type caractère de 30 octets.  Par conséquent, la partie données de chaque ligne est de 4 + 4 + 4 + 4 + 4 + 50 + 50 + 30 + 50 ou 200 octets.  
  
 Voici un calcul de taille de 5 millions de lignes dans une table mémoire optimisée : La quantité totale de mémoire utilisée par les lignes de données estimée est la suivante :  
  
 **Mémoire pour les lignes de la table**  
  
 Selon les calculs ci-dessus, la taille de chaque ligne de la table mémoire optimisée est de 24 + 32 + 200, ou 256 octets.  Étant donné qu'il y a 5 millions de lignes, la table consommera 5 000 000 * 256 octets, ou 1 280 000 000 octets (soit environ 1,28 Go).  
  
##  <a name="bkmk_IndexMeemory"></a> Mémoire pour les index  
 **Mémoire pour chaque index de hachage**  
  
 Chaque index de hachage est un tableau de hachage de pointeurs d'adresse 8 octets.  La taille du tableau est déterminée par le nombre de valeurs d'index uniques pour cet index – par exemple, le nombre de valeurs uniques Col2 est un bon point de départ pour la taille du tableau de t1c2_index. Un tableau de hachage qui est trop grand gaspille de la mémoire.  Un tableau de hachage qui est trop petit ralentit les performances, car il y a trop de collisions par valeurs d'index qui hachent au même index.  
  
 Les index de hachage exécutent des recherches d'égalité rapides, notamment :  
  
```tsql  
  
SELECT * FROM t_hk  
   WHERE Col2 = 3  
  
```  
  
 Les index non cluster sont plus rapides pour les recherches de plage suivantes :  
  
```tsql  
  
SELECT * FROM t_hk  
   WHERE Col2 >= 3  
  
```  
  
 Si vous migrez une table basée sur disque, utilisez les éléments suivants pour déterminer le nombre de valeurs uniques de l'index t1c2_index.  
  
```tsql  
  
SELECT COUNT(DISTINCT [Col2])  
  FROM t_hk  
  
```  
  
 Si vous créez une table, vous devrez évaluer la taille du tableau ou regrouper les données de votre test avant le déploiement.  
  
 Pour plus d’informations sur le fonctionnement des index de hachage dans les tables optimisées en mémoire [!INCLUDE[hek_2](../../includes/hek-2-md.md)] , consultez [Index de hachage](../../database-engine/hash-indexes.md).  
  
 **Remarque :** vous ne pouvez pas modifier la taille de tableau des index de hachage à la volée. Pour modifier la taille du tableau d'index de hachage, vous devez supprimer la table, modifier la valeur bucket_count et recréer la table.  
  
 **Définition de la taille de tableau des index de hachage**  
  
 La taille de tableau de hachage est définie par `(bucket_count= <value>)` où \<valeur > est une valeur entière supérieure à zéro. Si \<valeur > n’est pas une puissance de 2, la valeur de bucket_count réel est arrondi à la puissance de 2 suivante.  Dans notre exemple, (bucket_count = 5000000), étant donné que 5 000 000 n’est pas une puissance de 2, le nombre réel de compartiments est arrondi à 8 388 608 (2<sup>23</sup>).  Vous devez utiliser ce nombre, et non pas 5 000 000, lorsque vous calculez la mémoire nécessaire pour le tableau de hachage.  
  
 Ainsi, dans notre exemple, la mémoire nécessaire pour chaque tableau de hachage est :  
  
 8 388 608 * 8 = 2<sup>23</sup> \* 8 = 2<sup>23</sup> \* 2<sup>3</sup> = 2<sup>26</sup> = 67 108 864 ou approximativement 64 Mo.  
  
 Comme il y a trois index de hachage, la mémoire nécessaire pour les index de hachage est de 3 * 64 Mo = 192 Mo.  
  
 **Mémoire pour les index non cluster**  
  
 Les index non cluster sont implémentés en tant que BTrees avec nœuds internes contenant la valeur d'index et les pointeurs vers les nœuds suivants.  Les nœuds terminaux contiennent la valeur d'index et un pointeur vers la ligne de table en mémoire.  
  
 Contrairement aux index de hachage, les index non cluster n'ont pas une taille fixe de compartiment. L'index augmente et se réduit de façon dynamique avec les données.  
  
 La mémoire nécessaire pour les index non cluster peut être calculée comme suit :  
  
-   **Mémoire allouée aux nœuds non terminaux**   
    Pour une configuration spécifique, la mémoire allouée aux nœuds non terminaux représente un tout petit pourcentage de la mémoire globale utilisée par l'index. Il est si petit qu'il peut être ignoré sans risque.  
  
-   **Mémoire allouée aux nœuds terminaux**   
    Les nœuds terminaux ont une ligne pour chaque clé unique dans la table et elle pointe vers les lignes de données avec cette clé unique.  Si vous avez plusieurs lignes ayant la même clé (c'est-à-dire que vous avez un index non cluster non unique), il n'y a qu'une seule ligne dans le nœud terminal d'index qui pointe vers une des lignes avec les autres lignes liées entre elles.  Ainsi, la mémoire totale requise peut être estimée par :   
    memoryForNonClusteredIndex = (pointerSize + sum(keyColumnDataTypeSizes)) * rowsWithUniqueKeys  
  
 Les index non en cluster sont préférables lorsqu'ils sont utilisés pour les recherches de plage, comme l'illustre la requête suivante :  
  
```tsql  
  
SELECT * FROM t_hk  
   WHERE c2 > 5  
```  
  
##  <a name="bkmk_MemoryForRowVersions"></a> Mémoire pour le contrôle de version de ligne  
 Pour éviter les verrous, OLTP en mémoire utilise l'accès concurrentiel optimiste lors de la mise à jour ou de la suppression des lignes. Cela signifie que lorsqu'une ligne est mise à jour, une version supplémentaire de la ligne est créée. Le système conserve les versions précédentes disponibles tant que toutes les transactions susceptibles d'utiliser la version ne sont pas exécutées. Lorsqu'une ligne est supprimée, le système agit d'une manière similaire à une mise à jour, en conservant la version disponible jusqu'à ce qu'elle ne soit plus nécessaire. Les opérations de lecture et d'insertion ne créent pas de versions supplémentaires de ligne.  
  
 Étant donné qu'il peut y avoir plusieurs lignes supplémentaires en mémoire à tout moment lors de l'attente du cycle de garbage collection pour libérer la mémoire, vous devez disposer de suffisamment de mémoire pour gérer ces lignes supplémentaires.  
  
 Le nombre de lignes supplémentaires peut être estimé en calculant le nombre maximal de mises à jour et de suppressions de ligne par seconde, puis en le multipliant par le nombre de secondes nécessaires pour la plus longue transaction (au moins 1).  
  
 Cette valeur est ensuite multipliée par la taille de ligne pour obtenir le nombre d'octets nécessaires pour le contrôle de version de ligne.  
  
 `rowVersions = durationOfLongestTransactionInSeconds * peakNumberOfRowUpdatesOrDeletesPerSecond`  
  
 Besoins en mémoire pour les lignes obsolètes est ensuite estimée en multipliant le nombre de lignes obsolètes par la taille d’une ligne de table mémoire optimisée (voir [mémoire pour la table](#bkmk_MemoryForTable) ci-dessus).  
  
 `memoryForRowVersions = rowVersions * rowSize`  
  
##  <a name="bkmk_TableVariables"></a> Mémoire pour les variables de table  
 La mémoire utilisée pour une variable de table est libérée uniquement lorsque la variable de table sort de l'étendue. Les lignes supprimées d'une variable de table, y compris les lignes supprimées dans le cadre d'une mise à jour, ne sont pas concernées par l'opération de garbage collection. Aucun volume de mémoire n'est libéré avant que la variable de table sorte de l'étendue.  
  
 Les variables de table définies dans un grand lot SQL, par opposition à une étendue de procédure, et qui sont utilisées par plusieurs transactions, peuvent consommer beaucoup de mémoire. Étant donné qu'elles ne sont pas nettoyées, les lignes supprimées d'une variable de table peuvent utiliser beaucoup de mémoire et réduire les performances, car les opérations de lecture doivent analyser au-delà des lignes supprimées.  
  
##  <a name="bkmk_MemoryForGrowth"></a> Mémoire pour la croissance  
 Les calculs ci-dessus estiment les besoins en mémoire de la table, telle qu'elle existe actuellement. Outre cette mémoire, vous devez évaluer la croissance de la table et fournir suffisamment de mémoire pour gérer cette croissance.  Par exemple, si vous anticipez une croissance de 10 %, vous devez multiplier le résultat ci-dessus par 1,1 pour obtenir la mémoire totale nécessaire pour votre table.  
  
## <a name="see-also"></a>Voir aussi  
 [Migration vers OLTP en mémoire](migrating-to-in-memory-oltp.md)  
  
  