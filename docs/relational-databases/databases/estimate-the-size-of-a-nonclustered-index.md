---
title: Estimer la taille d’un index non-cluster | Microsoft Docs
description: Cette procédure permet d’estimer la quantité d’espace nécessaire au stockage d’un index non cluster dans SQL Server.
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.reviewer: ''
ms.prod_service: database-engine, sql-database
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], index size
- size [SQL Server], tables
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- designing databases [SQL Server], estimating size
- calculating table size
ms.assetid: c183b0e4-ef4c-4bfc-8575-5ac219c25b0a
author: stevestein
ms.author: sstein
monikerRange: = azuresqldb-current || >= sql-server-2016
ms.openlocfilehash: 9c234bb8371d99025bd97cfb86f5d85472d34ee4
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97474080"
---
# <a name="estimate-the-size-of-a-nonclustered-index"></a>Estimer la taille d'un index non-cluster

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Utilisez la procédure suivante pour estimer la quantité d'espace nécessaire au stockage d'un index non cluster :  
  
1.  Calculez les variables à utiliser dans les étapes 2 et 3.  
  
2.  Calculez l'espace utilisé pour stocker les informations d'index au niveau feuille de l'index non cluster.  
  
3.  Calculez l'espace utilisé pour stocker les informations d'index aux niveaux non-feuille de l'index non cluster.  
  
4.  Faites la somme des valeurs calculées.  
  
## <a name="step-1-calculate-variables-for-use-in-steps-2-and-3"></a>Étape 1. Calculer les variables à utiliser dans les étapes 2 et 3  
 Vous pouvez utiliser la procédure suivante afin de calculer les variables utilisées pour estimer la quantité d'espace nécessaire au stockage des niveaux supérieurs de l'index.  
  
1.  Déterminez le nombre de lignes que contiendra la table :  
  
     ***Num_Rows** _ = nombre de lignes dans la table  
  
2.  Spécifiez le nombre de colonnes de longueur fixe et de longueur variable de la clé d'index et calculez l'espace nécessaire à leur stockage :  
  
     Les colonnes clés d'un index peuvent inclure des colonnes de longueur fixe et variable. Pour estimer la taille de la ligne d'index du niveau intérieur, calculez l'espace occupé par chacun de ces groupes de colonnes dans la ligne d'index. La taille d'une colonne dépend du type des données et de la longueur spécifiée.  
  
     _*_Num_Key_Cols_*_  = nombre total de colonnes clés (de longueur fixe et variable)  
  
     _*_Fixed_Key_Size_*_  = taille totale, en octets, de toutes les colonnes clés de longueur fixe  
  
     _*_Num_Variable_Key_Cols_*_  = nombre de colonnes clés de longueur variable  
  
     _*_Max_Var_Key_Size_*_  = taille maximale, en octets, de toutes les colonnes clés de longueur variable  
  
3.  Tenez compte du localisateur de ligne de données nécessaire si l'index n'est pas unique :  
  
     Si l'index non-cluster n'est pas unique, le localisateur de ligne de données est associé à la clé d'index non-cluster pour produire une valeur de clé unique pour chaque ligne.  
  
     Si l'index non-cluster est au-dessus d'un segment, le localisateur de ligne de données est le RID de ce segment. Sa taille est de 8 octets.  
  
     _*_Num_Key_Cols_*_  = _*_Num_Key_Cols_*_  + 1  
  
     _*_Num_Variable_Key_Cols_*_  = _*_Num_Variable_Key_Cols_*_  + 1  
  
     _*_Max_Var_Key_Size_*_  = _*_Max_Var_Key_Size_*_  + 8  
  
     Si l'index non cluster est au-dessus d'un index cluster, le localisateur de lignes de données est la clé de clustering. Les colonnes qui doivent être associées à la clé d'index non cluster sont les colonnes de la clé de clustering qui ne sont pas déjà présentes dans l'ensemble des colonnes clés de l'index non cluster.  
  
     _*_Num_Key_Cols_*_  = _*_Num_Key_Cols_*_  + nombre de colonnes de clés de clustering non présentes dans l’ensemble de colonnes de clés d’index non cluster (+ 1 si l’index cluster est non unique)  
  
     _*_Fixed_Key_Size_*_  = _*_Fixed_Key_Size_*_  + taille totale, en octets, des colonnes de clés de clustering de longueur fixe non présentes dans l’ensemble de colonnes de clés d’index non cluster  
  
     _*_Num_Variable_Key_Cols_*_  = _*_Num_Variable_Key_Cols_*_  + nombre de colonnes de clés de clustering de longueur variable non présentes dans l’ensemble de colonnes de clés d’index non cluster (+ 1 si l’index cluster n’est pas unique)  
  
     _*_Max_Var_Key_Size_*_  = _*_Max_Var_Key_Size_*_  + taille maximale, en octets, des colonnes de clés de clustering de longueur variable non présentes dans l’ensemble de colonnes de clés d’index non cluster (+ 4 si l’index cluster n’est pas unique)  
  
4.  Une partie de la ligne, nommée null bitmap, peut être réservée à la gestion de l'acceptation de valeurs NULL dans les colonnes. Calculez sa taille :  
  
     En présence de colonnes autorisant des valeurs Null dans la clé d'index, notamment toutes les colonnes clés de clustering nécessaires comme décrit dans l'étape 1.3, une partie de la ligne d'index est réservée à la bitmap Null.  
  
     _*_Index_Null_Bitmap_*_  = 2 + ((nombre de colonnes dans la ligne d’index + 7) / 8)  
  
     Seule la partie entière de l'expression précédente doit être utilisée. Omettez le reste.  
  
     En l’absence de toute colonne clé autorisant les valeurs Null, attribuez la valeur 0 à _*_Index_Null_Bitmap_*_.  
  
5.  Calculez la taille des données de longueur variable :  
  
     En présence de colonnes de longueur variable dans la clé d'index, notamment les colonnes clés d'index cluster nécessaires, déterminez l'espace utilisé pour le stockage des colonnes dans la ligne d'index :  
  
     _*_Variable_Key_Size_*_  = 2 + (_*_Num_Variable_Key_Cols_*_  x 2) + _*_Max_Var_Key_Size_*_  
  
     Les octets ajoutés à _*_Max_Var_Key_Size_*_ servent à assurer le suivi de chaque colonne variable. Cette formule suppose que toutes les colonnes de longueur variable sont entièrement remplies. Si vous pensez qu’un pourcentage inférieur de l’espace de stockage des colonnes de longueur variable sera utilisé, vous pouvez ajuster la valeur de _*_Max_Var_Key_Size_*_ en fonction de ce pourcentage pour obtenir une estimation plus précise de la taille globale de la table.  
  
     En l’absence de toute colonne de longueur variable, attribuez la valeur 0 à _*_Variable_Key_Size_*_.  
  
6.  Calculez la taille de la ligne d'index :  
  
     _*_Index_Row_Size_*_  = _*_Fixed_Key_Size_*_ + _*_Variable_Key_Size_*_ + _*_Index_Null_Bitmap_*_  + 1 (représentant la surcharge de l’en-tête de la ligne d’index) + 6 (représentant le pointeur de l’ID de la page enfant)  
  
7.  Calculez le nombre de lignes d'index par page (8 096 octets libres par page) :  
  
     _*_Index_Rows_Per_Page_*_  = 8096 / (_*_Index_Row_Size_*_  + 2)  
  
     Comme les lignes d'index ne peuvent pas être fractionnées sur plusieurs pages de données, arrondissez le nombre de lignes d'index par page à la ligne entière inférieure. Le chiffre 2 de la formule concerne l'entrée de la ligne du tableau d'emplacement de la page.  
  
## <a name="step-2-calculate-the-space-used-to-store-index-information-in-the-leaf-level"></a>Étape 2. Calculer l'espace utilisé pour le stockage des informations d'index au niveau feuille  
 Vous pouvez utiliser la procédure suivante pour estimer la quantité d'espace nécessaire au stockage du niveau feuille de l'index. Vous aurez besoin des valeurs conservées dans l'étape 1 pour effectuer cette étape-ci.  
  
1.  Spécifiez le nombre de colonnes de longueur fixe et de longueur variable au niveau feuille et calculez l'espace nécessaire à leur stockage :  
  
    > [!NOTE]  
    >  Vous pouvez étendre un index non cluster en incluant les colonnes sans clé en plus des colonnes de clés d'index. Ces colonnes supplémentaires sont stockées uniquement au niveau feuille de l'index non-cluster. Pour plus d’informations, consultez [Créer des index avec colonnes incluses](../../relational-databases/indexes/create-indexes-with-included-columns.md).  
  
    > [!NOTE]  
    >  Vous pouvez combiner des colonnes _*varchar**, **nvarchar**, **varbinary** ou **sql_variant** qui provoquent le dépassement de la largeur totale de la table définie au-delà de 8 060 octets. La longueur de chacune de ces colonnes doit toujours être inférieure à la limite de 8 000 octets pour une colonne **varchar**, **varbinary** ou **sql_variant** et de 4 000 octets pour les colonnes **nvarchar** . Toutefois, l'association de leurs largeurs peut dépasser la limite de 8 060 octets dans une table. Ceci s'applique également aux lignes de feuille d'index non-cluster possédant des colonnes incluses.  
  
     Si l'index non-cluster ne possède aucune colonne incluse, utilisez les valeurs de l'étape 1, y compris les éventuelles modifications déterminées dans l'étape 1.3 :  
  
     **_Num_Leaf_Cols_* _ = _*_Num_Key_Cols_*_  
  
     _*_Fixed_Leaf_Size_*_  = _*_Fixed_Key_Size_*_  
  
     _*_Num_Variable_Leaf_Cols_*_  = _*_Num_Variable_Key_Cols_*_  
  
     _*_Max_Var_Leaf_Size_*_  = _*_Max_Var_Key_Size_*_  
  
     Si l'index non-cluster ne possède aucune colonne incluse, ajoutez les valeurs appropriées aux valeurs de l'étape 1, y compris les éventuelles modifications de l'étape 1.3. La taille d'une colonne dépend du type des données et de la longueur spécifiée. Pour plus d’informations, consultez [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).  
  
     _*_Num_Leaf_Cols_*_  = _*_Num_Key_Cols_*_  + nombre de colonnes incluses  
  
     _*_Fixed_Leaf_Size_*_  = _*_Fixed_Key_Size_*_  + taille totale, en octets, des colonnes incluses de longueur fixe  
  
     _*_Num_Variable_Leaf_Cols_*_  = _*_Num_Variable_Key_Cols_*_ + nombre de colonnes incluses de longueur variable  
  
     _*_Max_Var_Leaf_Size_*_  = _*_Max_Var_Key_Size_*_ + taille maximale, en octets, des colonnes incluses de longueur variable  
  
2.  Tenez compte du localisateur de ligne de données :  
  
     Si l'index non-cluster n'est pas unique, la surcharge du localisateur de ligne de données a déjà été prise en compte dans l'étape 1.3 et aucune modification supplémentaire n'est nécessaire. Passez à l'étape suivante.  
  
     Si l'index non-cluster est unique, le localisateur de ligne des données doit être pris en compte dans toutes les lignes au niveau feuille.  
  
     Si l'index non-cluster est au-dessus d'un segment, le localisateur de ligne de données est le RID du segment (taille 8 octets).  
  
     _*_Num_Leaf_Cols_*_  = _*_Num_Leaf_Cols_*_  + 1  
  
     _*_Num_Variable_Leaf_Cols_*_  = _*_Num_Variable_Leaf_Cols_*_  + 1  
  
     _*_Max_Var_Leaf_Size_*_  = _*_Max_Var_Leaf_Size_*_  + 8  
  
     Si l'index non cluster est au-dessus d'un index cluster, le localisateur de lignes de données est la clé de clustering. Les colonnes qui doivent être associées à la clé d'index non cluster sont les colonnes de la clé de clustering qui ne sont pas déjà présentes dans l'ensemble des colonnes clés de l'index non cluster.  
  
     _*_Num_Leaf_Cols_*_  = _*_Num_Leaf_Cols_*_ + nombre de colonnes de clés de clustering non présentes dans l’ensemble de colonnes de clés d’index non cluster (+ 1 si l’index cluster n’est pas unique)  
  
     _*_Fixed_Leaf_Size_*_  = _*_Fixed_Leaf_Size_*_ + nombre de colonnes de clés de clustering de longueur fixe non présentes dans l’ensemble de colonnes de clés d’index non cluster  
  
     _*_Num_Variable_Leaf_Cols_*_  = _*_Num_Variable_Leaf_Cols_*_ + nombre de colonnes de clés de clustering de longueur variable non présentes dans l’ensemble de colonnes de clés d’index non cluster (+ 1 si l’index cluster n’est pas unique)  
  
     _*_Max_Var_Leaf_Size_*_  = _*_Max_Var_Leaf_Size_*_ + taille, en octets, des colonnes de clés de clustering de longueur variable non présentes dans l’ensemble de colonnes de clés d’index non cluster (+ 4 si l’index cluster n’est pas unique)  
  
3.  Calculez la taille de null bitmap :  
  
     _*_Leaf_Null_Bitmap_*_  = 2 + ((_*_Num_Leaf_Cols_*_  + 7) / 8)  
  
     Seule la partie entière de l'expression précédente doit être utilisée. Omettez le reste.  
  
4.  Calculez la taille des données de longueur variable :  
  
     En présence de colonnes de longueur variable (colonnes clés ou incluses), notamment les colonnes clés de clustering nécessaires comme décrit précédemment dans l’étape 2.2, déterminez l’espace utilisé pour le stockage des colonnes dans la ligne d’index :  
  
     _*_Variable_Leaf_Size_*_  = 2 + (_*_Num_Variable_Leaf_Cols_*_  x 2) + _*_Max_Var_Leaf_Size_*_  
  
     Les octets ajoutés à _*_Max_Var_Key_Size_*_ servent à assurer le suivi de chaque colonne variable. Cette formule suppose que toutes les colonnes de longueur variable sont entièrement remplies. Si vous estimez qu’un pourcentage moins élevé de l’espace de stockage des colonnes de longueur variable sera utilisé, vous pouvez multiplier la valeur _*_Max_Var_Leaf_Size_*_ par ce pourcentage pour obtenir une estimation plus précise de la taille globale de la table.  
  
     En l’absence de colonnes de longueur variable (colonnes clés ou incluses), attribuez à _*_Variable_Leaf_Size_*_ la valeur 0.  
  
5.  Calculez la taille de la ligne d'index :  
  
     _*_Leaf_Row_Size_*_  = _*_Fixed_Leaf_Size_*_ + _*_Variable_Leaf_Size_*_ + _*_Leaf_Null_Bitmap_*_  + 1 (représentant la surcharge de l’en-tête de la ligne d’index)  
  
6.  Calculez le nombre de lignes d'index par page (8 096 octets libres par page) :  
  
     _*_Leaf_Rows_Per_Page_*_  = 8096 / (_*_Leaf_Row_Size_*_  + 2)  
  
     Comme les lignes d'index ne peuvent pas être fractionnées sur plusieurs pages de données, arrondissez le nombre de lignes d'index par page à la ligne entière inférieure. Le chiffre 2 de la formule concerne l'entrée de la ligne du tableau d'emplacement de la page.  
  
7.  Calculez le nombre de lignes libres réservées par page en fonction du taux de remplissage [Fill_Factor](../../relational-databases/indexes/specify-fill-factor-for-an-index.md) spécifié :  
  
     _*_Free_Rows_Per_Page_*_  = 8096 x ((100 - _*_Fill_Factor_*_) / 100) / (_*_Leaf_Row_Size_*_  + 2)  
  
     Le facteur de remplissage utilisé dans le calcul est un nombre et non un pourcentage. Comme les lignes ne peuvent pas être fractionnées sur plusieurs pages de données, arrondissez le nombre de lignes par page à la ligne entière inférieure. Au fur et à mesure que le facteur de remplissage s'accroît, davantage de données seront stockées sur chaque page et il y aura moins de pages. Le chiffre 2 de la formule concerne l'entrée de la ligne du tableau d'emplacement de la page.  
  
8.  Calculez ensuite le nombre de pages de données requises pour le stockage de toutes les lignes :  
  
     _*_Num_Leaf_Pages_*_  = _*_Num_Rows_*_  / (_*_Leaf_Rows_Per_Page_*_ - _*_Free_Rows_Per_Page_*_ )  
  
     Le nombre de pages de données estimé doit être arrondi à la page entière la plus proche.  
  
9. Calculez la taille de l'index (8 192 octets par page) :  
  
     _*_Leaf_Space_Used_*_  = 8192 x _*_Num_Leaf_Pages_*_  
  
## <a name="step-3-calculate-the-space-used-to-store-index-information-in-the-non-leaf-levels"></a>Étape 3. Calculer l'espace utilisé pour le stockage des informations d'index aux niveaux non-feuille  
 Utilisez la procédure suivante pour estimer la quantité d'espace nécessaire au stockage des niveaux intermédiaires et racine de l'index. Vous aurez besoin des valeurs conservées aux étapes 2 et 3 pour effectuer cette étape-ci.  
  
1.  Calculez le nombre de niveaux non-feuille contenus dans l'index :  
  
     _*_Non-leaf Levels_*_  = 1 + log( Index_Rows_Per_Page) (_*_Num_Leaf_Pages_*_ / _*_Index_Rows_Per_Page_*_)  
  
     Arrondissez cette valeur au nombre entier supérieur le plus proche. Cette valeur n'inclut pas le niveau feuille de l'index non cluster.  
  
2.  Calculez le nombre de pages non-feuille contenues dans l'index :  
  
     _*_Num_Index_Pages_*_  = ∑Level (_*_Num_Leaf_Pages/Index_Rows_Per_Page_*_^Level)where 1 <= Level <= _*_Levels_*_  
  
     Arrondissez chaque élément de la somme au nombre entier supérieur le plus proche. À titre d’exemple simple, imaginez un index où _*_Num_Leaf_Pages_*_  = 1000 et _*_Index_Rows_Per_Page_*_  = 25. Le premier niveau d'index au-dessus du niveau feuille stocke 1 000 lignes d'index, ce qui représente une ligne d'index par page feuille et 25 lignes d'index par page. Par conséquent, il faut 40 pages pour stocker ces 1 000 lignes d'index. Le niveau suivant de l'index doit stocker 40 lignes. Cela requiert donc 2 pages. Le niveau final de l'index doit stocker 2 lignes. Cela requiert donc 1 page. Il en résulte 43 pages d'index non-feuille. Lorsque ces nombres sont utilisés dans les formules précédentes, le résultat est le suivant :  
  
     _*_Non-leaf_Levels_*_  = 1 + log(25) (1000 / 25) = 3  
  
     _*_Num_Index_Pages_*_  = 1000/(25^3) + 1000/(25^2) + 1000/(25^1) = 1 + 2 + 40 = 43, ce qui correspond au nombre de pages décrit dans l’exemple.  
  
3.  Calculez la taille de l'index (8 192 octets par page) :  
  
     _*_Index_Space_Used_*_  = 8192 x _*_Num_Index_Pages_*_  
  
## <a name="step-4-total-the-calculated-values"></a>Étape 4. Faire la somme des valeurs calculées  
 Faites la somme des valeurs obtenues à partir des deux étapes précédentes :  
  
 Taille de l’index non cluster (octets) = _*_Leaf_Space_Used_*_ + _*_Index_Space_used_*_  
  
 Ce calcul ne tient pas compte des éléments suivants :  
  
-   Partitionnement  
  
     L'espace réservé pour le partitionnement est minime, mais complexe à calculer. Il n'est pas nécessaire de l'inclure.  
  
-   Pages d'allocation  
  
     Au moins une page IAM est utilisée pour assurer le suivi des pages allouées à un segment de mémoire, mais l'espace réservé est minime. De plus, il n'existe aucun algorithme capable de calculer de manière déterministe et exacte le nombre de pages IAM qui seront utilisées.  
  
-   Valeurs LOB  
  
     L’algorithme permettant de déterminer avec exactitude la quantité d’espace qui sera utilisée pour stocker les valeurs des types de données LOB _*varchar(max)**, **varbinary(max)** , **nvarchar(max)** , **text**, **ntext**, **xml** et **image** est complexe. Il suffit simplement de faire la somme de la taille moyenne des valeurs LOB attendues, de la multiplier par **_Num_Rows_**, puis d’ajouter le résultat à la taille totale de l’index non-cluster.  
  
-   Compression  
  
     Vous ne pouvez pas précalculer la taille d'un index compressé.  
  
-   Colonnes éparses  
  
     Pour plus d'informations sur l'espace nécessaire pour les colonnes éparses, consultez [Use Sparse Columns](../../relational-databases/tables/use-sparse-columns.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Description des index cluster et non-cluster](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)   
 [Créez des index non-cluster](../../relational-databases/indexes/create-nonclustered-indexes.md)   
 [Créer des index cluster](../../relational-databases/indexes/create-clustered-indexes.md)   
 [Estimer la taille d'une table](../../relational-databases/databases/estimate-the-size-of-a-table.md)   
 [Estimer la taille d’un index cluster](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)   
 [Estimer la taille d’un segment de mémoire](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [Estimer la taille d'une base de données](../../relational-databases/databases/estimate-the-size-of-a-database.md)  
  
  
