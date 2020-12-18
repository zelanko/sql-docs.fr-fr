---
title: Estimer la taille d’un index cluster | Microsoft Docs
description: Cette procédure permet d’estimer la quantité d’espace nécessaire au stockage de données dans un index cluster dans SQL Server.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.prod_service: database-engine, sql-database
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], index size
- size [SQL Server], tables
- disk space [SQL Server], indexes
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- space [SQL Server], indexes
- clustered indexes, table size
- nonclustered indexes [SQL Server], table size
- designing databases [SQL Server], estimating size
- calculating table size
ms.assetid: 2b5137f8-98ad-46b5-9aae-4c980259bf8d
author: stevestein
ms.author: sstein
monikerRange: = azuresqldb-current || >= sql-server-2016
ms.openlocfilehash: d963a8745d83be039fa2970a24d04a2a882bf7a9
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97478360"
---
# <a name="estimate-the-size-of-a-clustered-index"></a>Estimer la taille d’un index cluster

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Vous pouvez estimer la quantité d'espace nécessaire au stockage des données d'un index cluster en procédant comme suit :  
  
1.  Calculez l'espace utilisé pour le stockage des données au niveau feuille de l'index cluster.  
  
2.  Calculez l'espace utilisé pour le stockage des informations relatives à l'index cluster.  
  
3.  Faites la somme des valeurs calculées.  
  
## <a name="step-1-calculate-the-space-used-to-store-data-in-the-leaf-level"></a>Étape 1. Calculer l'espace utilisé pour le stockage des données au niveau feuille  
  
1.  Déterminez le nombre de lignes que contiendra la table :  
  
     ***Num_Rows** _ = nombre de lignes dans la table  
  
2.  Spécifiez le nombre de colonnes de longueur fixe et variable et calculez l'espace nécessaire à leur stockage :  
  
     Calculez l'espace que chacun de ces groupes de colonnes occupe dans la ligne de données. La taille d'une colonne dépend du type des données et de la longueur spécifiée.  
  
     _*_Num_Cols_*_  = nombre total de colonnes (de longueur fixe et de longueur variable)  
  
     _*_Fixed_Data_Size_*_  = taille totale, en octets, de toutes les colonnes de longueur fixe  
  
     _*_Num_Variable_Cols_*_  = nombre de colonnes de longueur variable  
  
     _*_Max_Var_Size_*_  = taille maximale, en octets, de toutes les colonnes de longueur variable  
  
3.  S’il s’agit d’un index cluster non unique, définissez la colonne _uniqueifier* :  
  
     Cette colonne est une colonne de longueur variable qui accepte les valeurs NULL. Elle présentera une valeur non NULL et une taille de 4 octets dans les lignes qui contiennent des valeurs de clés non uniques. Cette valeur fait partie de la clé d'index et est nécessaire pour garantir que chaque ligne contient une valeur de clé unique.  
  
     ***Num_Cols** _ = _*_Num_Cols_*_  + 1  
  
     _*_Num_Variable_Cols_*_  = _*_Num_Variable_Cols_*_  + 1  
  
     _*_Max_Var_Size_*_  = _*_Max_Var_Size_*_  + 4  
  
     Ces modifications supposent que toutes ces valeurs ne seront pas uniques.  
  
4.  Une partie de la ligne, connue sous le nom de bitmap NULL, est réservée pour gérer la possibilité de valeur NULL de la colonne. Calculez sa taille :  
  
     _*_Null_Bitmap_*_  = 2 + ((_*_Num_Cols_*_  + 7) / 8)  
  
     Seule la partie entière de l'expression précédente doit être utilisée ; omettez le reste.  
  
5.  Calculez la taille des données de longueur variable :  
  
     En présence de colonnes de longueur variable dans la table, déterminez l'espace utilisé pour stocker les colonnes dans la ligne au moyen de la formule suivante :  
  
     _*_Variable_Data_Size_*_  = 2 + (_*_Num_Variable_Cols_*_  x 2) + _*_Max_Var_Size_*_  
  
     Les octets ajoutés à _*_Max_Var_Size_*_ servent à assurer le suivi de chaque colonne variable. Il est supposé, lorsque vous utilisez cette formule, que toutes les colonnes de longueur variable sont entièrement remplies. Si vous pensez qu’un pourcentage inférieur de l’espace de stockage des colonnes de longueur variable sera utilisé, vous pouvez ajuster la valeur de _*_Max_Var_Size_*_ en fonction de ce pourcentage pour obtenir une estimation plus précise de la taille globale de la table.  
  
    > [!NOTE]  
    >  Vous pouvez combiner des colonnes _*varchar**, **nvarchar**, **varbinary** ou **sql_variant** qui provoquent le dépassement de la largeur totale de la table définie au-delà de 8 060 octets. La longueur de chacune de ces colonnes doit toujours être inférieure à la limite de 8 000 octets pour une colonne **varchar**, **varbinary** ou **sql_variant** et de 4 000 octets pour les colonnes **nvarchar** . Toutefois, l'association de leurs largeurs peut dépasser la limite de 8 060 octets dans une table.  
  
     En l’absence de toute colonne de longueur variable, attribuez la valeur 0 à **_Variable_Data_Size_* _.  
  
6.  Calculez la taille totale de la ligne :  
  
     _*_Row_Size_*_  = _*_Fixed_Data_Size_*_ + _*_Variable_Data_Size_*_ + _*_Null_Bitmap_*_  + 4  
  
     La valeur 4 correspond à l'espace réservé à l'en-tête d'une ligne de données.  
  
7.  Calculez le nombre de lignes par page (8 096 octets disponibles par page) :  
  
     _*_Rows_Per_Page_*_  = 8096 / (_*_Row_Size_*_  + 2)  
  
     Comme les lignes ne peuvent pas être fractionnées sur plusieurs pages de données, arrondissez le nombre de lignes par page à la ligne entière inférieure. La valeur 2 dans la formule correspond à l'entrée de la ligne dans le tableau d'emplacements de la page.  
  
8.  Calculez le nombre de lignes libres réservées par page en fonction du taux de remplissage [Fill_Factor](../../relational-databases/indexes/specify-fill-factor-for-an-index.md) spécifié :  
  
     _*_Free_Rows_Per_Page_*_  = 8096 x ((100 - _*_Fill_Factor_*_) / 100) / (_*_Row_Size_*_  + 2)  
  
     Le facteur de remplissage utilisé dans le calcul est un nombre et non un pourcentage. Comme les lignes ne peuvent pas être fractionnées sur plusieurs pages de données, arrondissez le nombre de lignes par page à la ligne entière inférieure. Au fur et à mesure que le facteur de remplissage s'accroît, davantage de données seront stockées sur chaque page et il y aura moins de pages. La valeur 2 dans la formule correspond à l'entrée de la ligne dans le tableau d'emplacements de la page.  
  
9. Calculez ensuite le nombre de pages de données requises pour le stockage de toutes les lignes :  
  
     _*_Num_Leaf_Pages_*_  = _*_Num_Rows_*_  / (_*_Rows_Per_Page_*_ - _*_Free_Rows_Per_Page_*_ )  
  
     Le nombre de pages de données estimé doit être arrondi à la page entière la plus proche.  
  
10. Calculez la quantité d'espace nécessaire pour le stockage des données au niveau feuille (au total, 8 192 octets par page) :  
  
     _*_Leaf_space_used_*_  = 8192 x _*_Num_Leaf_Pages_*_  
  
## <a name="step-2-calculate-the-space-used-to-store-index-information"></a>Étape 2. Calculer l'espace utilisé pour le stockage des informations d'index  
 Vous pouvez estimer la quantité d'espace nécessaire au stockage des niveaux supérieurs de l'index en procédant comme suit :  
  
1.  Spécifiez le nombre de colonnes de longueur fixe et de longueur variable de la clé d'index et calculez l'espace nécessaire à leur stockage :  
  
     Les colonnes clés d'un index peuvent inclure des colonnes de longueur fixe et variable. Pour estimer la taille de la ligne d'index du niveau intérieur, calculez l'espace occupé par chacun de ces groupes de colonnes dans la ligne d'index. La taille d'une colonne dépend du type des données et de la longueur spécifiée.  
  
     _*_Num_Key_Cols_*_  = nombre total de colonnes clés (de longueur fixe et variable)  
  
     _*_Fixed_Key_Size_*_  = taille totale, en octets, de toutes les colonnes clés de longueur fixe  
  
     _*_Num_Variable_Key_Cols_*_  = nombre de colonnes clés de longueur variable  
  
     _*_Max_Var_Key_Size_*_  = taille maximale, en octets, de toutes les colonnes clés de longueur variable  
  
2.  Définissez les colonnes uniqueifier nécessaires s'il s'agit d'un index non unique :  
  
     Cette colonne est une colonne de longueur variable qui accepte les valeurs NULL. Elle présentera une valeur non NULL et une taille de 4 octets dans les lignes qui contiennent des valeurs de clés d'index non uniques. Cette valeur fait partie de la clé d'index et est nécessaire pour garantir que chaque ligne contient une valeur de clé unique.  
  
     _*_Num_Key_Cols_*_  = _*_Num_Key_Cols_*_  + 1  
  
     _*_Num_Variable_Key_Cols_*_  = _*_Num_Variable_Key_Cols_*_  + 1  
  
     _*_Max_Var_Key_Size_*_  = _*_Max_Var_Key_Size_*_  + 4  
  
     Ces modifications supposent que toutes ces valeurs ne seront pas uniques.  
  
3.  Calculez la taille de null bitmap :  
  
     En présence de colonnes autorisant des valeurs Null dans la clé d'index, une partie de la ligne d'index est réservée à la bitmap Null. Calculez sa taille :  
  
     _*_Index_Null_Bitmap_*_  = 2 + ((nombre de colonnes dans la ligne d’index + 7) / 8)  
  
     Seule la partie entière de l'expression précédente doit être utilisée. Omettez le reste.  
  
     En l’absence de toute colonne clé autorisant les valeurs Null, attribuez la valeur 0 à _*_Index_Null_Bitmap_*_.  
  
4.  Calculez la taille des données de longueur variable :  
  
     En présence de colonnes de longueur variable, déterminez l'espace utilisé pour le stockage des colonnes dans la ligne d'index au moyen de la formule suivante :  
  
     _*_Variable_Key_Size_*_  = 2 + (_*_Num_Variable_Key_Cols_*_  x 2) + _*_Max_Var_Key_Size_*_  
  
     Les octets ajoutés à _*_Max_Var_Key_Size_*_ servent à assurer le suivi de chaque colonne de longueur variable. Il est supposé, lorsque vous utilisez cette formule, que toutes les colonnes de longueur variable sont entièrement remplies. Si vous pensez qu’un pourcentage inférieur de l’espace de stockage des colonnes de longueur variable sera utilisé, vous pouvez ajuster la valeur de _*_Max_Var_Key_Size_*_ en fonction de ce pourcentage pour obtenir une estimation plus précise de la taille globale de la table.  
  
     En l’absence de toute colonne de longueur variable, attribuez la valeur 0 à _*_Variable_Key_Size_*_.  
  
5.  Calculez la taille de la ligne d'index :  
  
     _*_Index_Row_Size_*_  = _*_Fixed_Key_Size_*_ + _*_Variable_Key_Size_*_ + _*_Index_Null_Bitmap_*_  + 1 (représentant la surcharge de l’en-tête de la ligne d’index) + 6 (représentant le pointeur de l’ID de la page enfant)  
  
6.  Calculez le nombre de lignes d'index par page (8 096 octets libres par page) :  
  
     _*_Index_Rows_Per_Page_*_  = 8096 / (_*_Index_Row_Size_*_  + 2)  
  
     Comme les lignes d'index ne peuvent pas être fractionnées sur plusieurs pages de données, arrondissez le nombre de lignes d'index par page à la ligne entière inférieure. Le chiffre 2 de la formule concerne l'entrée de la ligne du tableau d'emplacement de la page.  
  
7.  Calculez le nombre de niveaux contenus dans l'index :  
  
     _*_Non-leaf_Levels_*_  = 1 + log (Index_Rows_Per_Page) (_*_Num_Leaf_Pages_*_ / _*_Index_Rows_Per_Page_*_)  
  
     Arrondissez cette valeur au nombre entier supérieur le plus proche. Cette valeur n'inclut pas le niveau feuille de l'index cluster.  
  
8.  Calculez le nombre de pages non-feuille contenues dans l'index :  
  
     _*_Num_Index_Pages =_*_ ∑Level _*_ (Num_Leaf_Pages / (Index_Rows_Per_Page_ *_^Level_* _))_ *_  
  
     où 1 <= Level <= _*_Non-leaf_Levels_*_  
  
     Arrondissez chaque élément de la somme au nombre entier supérieur le plus proche. À titre d’exemple simple, imaginez un index où _*_Num_Leaf_Pages_*_  = 1000 et _*_Index_Rows_Per_Page_*_  = 25. Le premier niveau d'index au-dessus du niveau feuille stocke 1 000 lignes d'index, ce qui représente une ligne d'index par page feuille et 25 lignes d'index par page. Par conséquent, il faut 40 pages pour stocker ces 1 000 lignes d'index. Le niveau suivant de l'index doit stocker 40 lignes. Cela requiert donc 2 pages. Le niveau final de l'index doit stocker 2 lignes. Cela requiert donc 1 page. Il en résulte 43 pages d'index non-feuille. Lorsque ces nombres sont utilisés dans les formules précédentes, le résultat est le suivant :  
  
     _*_Non-leaf_Levels_*_  = 1 + log(25) (1000 / 25) = 3  
  
     _*_Num_Index_Pages_*_  = 1000/(25^3) + 1000/(25^2) + 1000/(25^1) = 1 + 2 + 40 = 43, ce qui correspond au nombre de pages décrit dans l’exemple.  
  
9. Calculez la taille de l'index (8 192 octets par page) :  
  
     _*_Index_Space_Used_*_  = 8192 x _*_Num_Index_Pages_*_  
  
## <a name="step-3-total-the-calculated-values"></a>Étape 3. Faire la somme des valeurs calculées  
 Faites la somme des valeurs obtenues à partir des deux étapes précédentes :  
  
 Taille de l’index cluster (octets) = _*_Leaf_Space_Used_*_ + _*_Index_Space_used_*_  
  
 Ce calcul ne tient pas compte des éléments suivants :  
  
-   Partitionnement  
  
     L'espace réservé pour le partitionnement est minime, mais complexe à calculer. Il n'est pas nécessaire de l'inclure.  
  
-   Pages d'allocation  
  
     Au moins une page IAM est utilisée pour assurer le suivi des pages allouées à un segment de mémoire, mais l'espace réservé est minime. De plus, il n'existe aucun algorithme capable de calculer de manière déterministe et exacte le nombre de pages IAM qui seront utilisées.  
  
-   Valeurs LOB  
  
     L’algorithme permettant de déterminer avec exactitude la quantité d’espace qui sera utilisée pour stocker les valeurs des types de données LOB _*varchar(max)**, **varbinary(max)** , **nvarchar(max)** , **text**, **ntext**, **xml** et **image** est complexe. Il suffit simplement de faire la somme de la taille moyenne des valeurs LOB attendues, de la multiplier par **_Num_Rows_**, puis d’ajouter le résultat à la taille totale de l’index cluster.  
  
-   Compression  
  
     Vous ne pouvez pas précalculer la taille d'un index compressé.  
  
-   Colonnes éparses  
  
     Pour plus d'informations sur l'espace nécessaire pour les colonnes éparses, consultez [Use Sparse Columns](../../relational-databases/tables/use-sparse-columns.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Description des index cluster et non-cluster](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)   
 [Estimer la taille d'une table](../../relational-databases/databases/estimate-the-size-of-a-table.md)   
 [Créer des index cluster](../../relational-databases/indexes/create-clustered-indexes.md)   
 [Créez des index non-cluster](../../relational-databases/indexes/create-nonclustered-indexes.md)   
 [Estimer la taille d'un index non-cluster](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)   
 [Estimer la taille d’un segment de mémoire](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [Estimer la taille d'une base de données](../../relational-databases/databases/estimate-the-size-of-a-database.md)  
  
  
