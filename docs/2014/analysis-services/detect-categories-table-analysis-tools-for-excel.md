---
title: Détecter les catégories (outils d’analyse de table pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- clustering [data mining]
- mining model, decision tree
- category detection
ms.assetid: 3c7e9ebb-d0c9-498e-a9ba-cc13eaa43520
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1c54c6f369d519812bb79cacf51bd1ad00a1dfb5
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78175218"
---
# <a name="detect-categories-table-analysis-tools-for-excel"></a>Détecter les catégories (Outils d'analyse de table pour Excel)
  ![Bouton Détecter les catégories sur le ruban](media/tat-detectcat.gif "Bouton Détecter les catégories sur le ruban")

 L’outil **détecter les catégories** détecte automatiquement les lignes d’une table qui présentent des caractéristiques similaires.

 Lorsque l'outil a terminé, il crée un rapport répertoriant les catégories identifiées ainsi que leurs caractéristiques distinctives. Par défaut, il ajoute une nouvelle colonne à la table de données contenant la catégorie proposée pour chaque ligne de données. Vous pouvez ensuite passer les catégories en revue et les renommer.

## <a name="using-the-detect-categories-tool"></a>Utilisation de l'outil Détecter les catégories

1.  Ouvrez un tableau Excel.

2.  Cliquez sur **détecter les catégories**.

3.  Spécifiez les colonnes à utiliser dans l'analyse. Vous pouvez désélectionner les colonnes qui contiennent des valeurs distinctes, comme des noms de personnes ou des ID d'enregistrement, car ces colonnes ne sont pas utiles pour l'analyse.

4.  Si vous le souhaitez, spécifiez le nombre maximum de catégories à créer. Par défaut, l'outil crée automatiquement autant de catégories que nécessaire.

5.  Cliquez sur **Exécuter**.

6.  L'outil crée une nouvelle feuille de calcul, nommée Rapport de catégories, qui contient la liste des catégories et leurs caractéristiques.

 Pour plus d’informations sur la façon de spécifier les options de l’outil, consultez [boîte de dialogue détecter les catégories (outils d’analyse de table pour Excel)](detect-categories-table-analysis-tools-for-excel.md).

## <a name="understanding-the-categories-report"></a>Présentation du Rapport de catégories
 Le **rapport catégories** contient deux tables, **la liste des catégories** et les **caractéristiques**des catégories, ainsi qu’un graphique profils de **catégorie** .

### <a name="category-list"></a>Liste des catégories
 Le premier tableau répertorie les catégories trouvées. La colonne **nombre** de lignes indique le nombre de lignes de données qui ont été affectées à chaque catégorie.

 Le modèle crée des noms temporaires pour chaque catégorie, mais vous pouvez renommer les catégories à votre convenance. Par exemple, dans l’exemple suivant, la première catégorie a été renommée **revenu faible**, car il s’agissait de l’attribut supérieur du cluster.

 ![rapport créé par l'outil Détecter les catégories](media/dm13-tat-detectcat-report1.gif "rapport créé par l'outil Détecter les catégories")

 Lorsque vous tapez la nouvelle étiquette, le changement est propagé à tous les autres graphiques, ainsi qu'à la liste des catégories ajoutées dans la feuille de calcul des données source.

### <a name="category-characteristics"></a>Caractéristiques de la catégorie
 La deuxième table, **caractéristiques**de la catégorie, affiche des détails sur la composition de chaque catégorie. Cliquez sur le bouton **filtre** en haut de la colonne **catégorie** pour voir le focus sur une ou plusieurs catégories.

 ![rapport créé par l'outil Détecter les catégories](media/dm13-tat-detectcat-report2.gif "rapport créé par l'outil Détecter les catégories")

 L’ombrage dans la colonne, **importance relative**, indique l’importance de la combinaison de l’attribut et de la valeur en tant que facteur distinctif. Plus la barre est longue, plus il est probable que l'attribut est fortement représentatif de cette catégorie.

### <a name="categories-profile-chart"></a>Graphique des profils de catégories
 Le graphique final dans la feuille de calcul **rapport de catégories** , **profils de catégorie**, est un **graphique croisé dynamique** interactif que vous pouvez utiliser pour réorganiser et masquer des champs, filtrer sur des valeurs et personnaliser l’apparence du graphique.

 Excel 2013 fournit désormais des **styles de graphique** et des contrôles d’éléments de **graphique** directement dans l’aire de conception qui facilitent l’amélioration de la conception du graphique.

 ![rapport créé par l'outil Détecter les catégories](media/dm13-tat-detectcat-report3.gif "rapport créé par l'outil Détecter les catégories")

## <a name="requirements"></a>Spécifications
 L’outil **détecter les catégories** n’est pas requis pour la quantité ou le type de données.

> [!NOTE]
>  Lorsque vous utilisez l’outil **détecter les catégories** , il crée une nouvelle colonne, catégorie, dans la table de données d’origine. Si vous laissez cette colonne dans la table de données et que vous effectuez ensuite d'autres opérations d'exploration de données, la présence de cette colonne peut affecter vos résultats. Pour éviter que cela n'arrive, nous vous recommandons de faire une copie de la table de données sans la colonne Catégorie avant d'utiliser d'autres outils d'exploration de données.

## <a name="related-tools"></a>Outils connexes
 Lorsque l’outil **détecter les catégories** analyse vos données, il crée une structure d’exploration de données et un modèle d’exploration [!INCLUDE[msCoName](../includes/msconame-md.md)] de données à l’aide de l’algorithme de clustering.

 Une fois que vous avez créé un modèle d’exploration de données à l’aide de l’outil **analyser les influenceurs clés** , vous pouvez utiliser le client d’exploration de données pour Excel pour parcourir le modèle et explorer les relations de manière plus détaillée. Le client d'exploration de données pour Excel est un complément séparé qui fournit des fonctionnalités d'exploration de données plus avancées. Pour plus d’informations, consultez [navigation dans les modèles dans Excel &#40;SQL Server les compléments d’exploration de données&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).

 Pour plus d’informations sur l’utilisation des fonctionnalités de modélisation des données dans le client d’exploration de données pour Excel, consultez [création d’un modèle d’exploration de données](creating-a-data-mining-model.md).

 Pour plus d’informations sur l’algorithme utilisé par l’outil **détecter les catégories** , consultez la rubrique « algorithme de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] clustering Microsoft » dans la documentation en ligne de.

## <a name="see-also"></a>Voir aussi
 [Outils d'analyse de table pour Excel](table-analysis-tools-for-excel.md)


