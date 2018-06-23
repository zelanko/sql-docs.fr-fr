---
title: Détecter les catégories (outils d’analyse de Table pour Excel) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Table Analysis tools
- clustering [data mining]
- mining model, decision tree
- category detection
ms.assetid: 3c7e9ebb-d0c9-498e-a9ba-cc13eaa43520
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d46840e2c2f7de1d56d6b528706ae908e7627a3e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043721"
---
# <a name="detect-categories-table-analysis-tools-for-excel"></a>Détecter les catégories (Outils d'analyse de table pour Excel)
  ![Bouton détecter catégories ruban](media/tat-detectcat.gif "bouton détecter les catégories de ruban")  
  
 Le **détecter les catégories** outil détecte automatiquement les lignes dans une table qui présentent des caractéristiques similaires.  
  
 Lorsque l'outil a terminé, il crée un rapport répertoriant les catégories identifiées ainsi que leurs caractéristiques distinctives. Par défaut, il ajoute une nouvelle colonne à la table de données contenant la catégorie proposée pour chaque ligne de données. Vous pouvez ensuite passer les catégories en revue et les renommer.  
  
## <a name="using-the-detect-categories-tool"></a>Utilisation de l'outil Détecter les catégories  
  
1.  Ouvrez un tableau Excel.  
  
2.  Cliquez sur **détecter les catégories**.  
  
3.  Spécifiez les colonnes à utiliser dans l'analyse. Vous pouvez désélectionner les colonnes qui contiennent des valeurs distinctes, comme des noms de personnes ou des ID d'enregistrement, car ces colonnes ne sont pas utiles pour l'analyse.  
  
4.  Si vous le souhaitez, spécifiez le nombre maximum de catégories à créer. Par défaut, l'outil crée automatiquement autant de catégories que nécessaire.  
  
5.  Cliquez sur **Exécuter**.  
  
6.  L'outil crée une nouvelle feuille de calcul, nommée Rapport de catégories, qui contient la liste des catégories et leurs caractéristiques.  
  
 Pour plus d’informations sur la façon de spécifier les options de l’outil, consultez [détecter une boîte de dialogue Catégories (outils d’analyse de Table pour Excel)](detect-categories-table-analysis-tools-for-excel.md).  
  
## <a name="understanding-the-categories-report"></a>Présentation du Rapport de catégories  
 Le **rapport de catégories** contient deux tables, **liste des catégories** et **caractéristiques de la catégorie**et un **profils de catégorie** graphique.  
  
### <a name="category-list"></a>Liste des catégories  
 Le premier tableau répertorie les catégories trouvées. Le **nombre de lignes** colonne indique le nombre de lignes de données ont été affecté à chaque catégorie.  
  
 Le modèle crée des noms temporaires pour chaque catégorie, mais vous pouvez renommer les catégories à votre convenance. Par exemple, dans l’exemple suivant, la première catégorie a été renommée **Low Income**, car il s’agit de l’attribut supérieur du cluster.  
  
 ![rapport créé par l’outil détecter les catégories](media/dm13-tat-detectcat-report1.gif "rapport créé par l’outil détecter les catégories")  
  
 Lorsque vous tapez la nouvelle étiquette, le changement est propagé à tous les autres graphiques, ainsi qu'à la liste des catégories ajoutées dans la feuille de calcul des données source.  
  
### <a name="category-characteristics"></a>Caractéristiques de la catégorie  
 La deuxième table, **caractéristiques de la catégorie**, donne des détails sur la composition de chaque catégorie. Cliquez sur le **filtre** bouton en haut de la **catégorie** colonne pour afficher le focus sur une ou plusieurs catégories.  
  
 ![rapport créé par l’outil détecter les catégories](media/dm13-tat-detectcat-report2.gif "rapport créé par l’outil détecter les catégories")  
  
 L’ombrage dans la colonne, **Importance Relative**, indique l’importance que la combinaison de l’attribut et la valeur est en tant que facteur distinctif. Plus la barre est longue, plus il est probable que l'attribut est fortement représentatif de cette catégorie.  
  
### <a name="categories-profile-chart"></a>Graphique des profils de catégories  
 Le graphique final dans le **rapport de catégories** feuille de calcul, **profils de catégorie**, est interactif **graphique croisé dynamique** que vous pouvez utiliser pour réorganiser et masquer les champs, filtrer sur des valeurs et personnaliser l’apparence du graphique.  
  
 Excel 2013 fournit maintenant **Styles de graphique** et **éléments de graphique** contrôle directement dans l’aire de conception qui facilitent l’améliorer la conception graphique.  
  
 ![rapport créé par l’outil détecter les catégories](media/dm13-tat-detectcat-report3.gif "rapport créé par l’outil détecter les catégories")  
  
## <a name="requirements"></a>Spécifications  
 Le **détecter les catégories** outil ne dispose d’aucune configuration requise pour la quantité ou le type de données.  
  
> [!NOTE]  
>  Lorsque vous utilisez la **détecter les catégories** outil, il crée une nouvelle colonne, catégorie, dans la table de données d’origine. Si vous laissez cette colonne dans la table de données et que vous effectuez ensuite d'autres opérations d'exploration de données, la présence de cette colonne peut affecter vos résultats. Pour éviter que cela n'arrive, nous vous recommandons de faire une copie de la table de données sans la colonne Catégorie avant d'utiliser d'autres outils d'exploration de données.  
  
## <a name="related-tools"></a>Outils connexes  
 Lorsque le **détecter les catégories** outil analyse vos données, il crée une structure d’exploration de données et le modèle d’exploration de données à l’aide de la [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme de Clustering.  
  
 Après avoir créé un modèle d’exploration de données à l’aide de la **analyser les facteurs d’influence clés** outil, vous pouvez utiliser le Client d’exploration de données pour Excel pour parcourir le modèle et Explorer les relations plus en détail. Le client d'exploration de données pour Excel est un complément séparé qui fournit des fonctionnalités d'exploration de données plus avancées. Pour plus d’informations, consultez [exploration des modèles dans Excel &#40;des compléments d’exploration de données SQL Server&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).  
  
 Pour plus d’informations sur l’utilisation des modélisation des données fonctionnalités dans le Client d’exploration de données pour Excel, consultez [création d’un modèle d’exploration de données](creating-a-data-mining-model.md).  
  
 Pour plus d’informations sur l’algorithme utilisé par le **détecter les catégories** outil, consultez la rubrique « Algorithme de Clustering Microsoft » dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils d’analyse de table pour Excel](table-analysis-tools-for-excel.md)  
  
  