---
title: Tri interactif (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 00cafed5-1a3c-4ce0-a1fb-ff1e2613f495
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2f3e427e0bc407167f25d679954a8506256300fc
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56294320"
---
# <a name="interactive-sort-report-builder-and-ssrs"></a>Tri interactif (Générateur de rapports et SSRS)
  Vous pouvez ajouter des boutons de tri interactifs pour permettre à un utilisateur de basculer entre l'ordre croissant et l'ordre décroissant pour les lignes d'une table ou pour les lignes et les colonnes d'une matrice. L'utilisation la plus courante du tri interactif consiste à ajouter un bouton de tri à chaque en-tête de colonne. L'utilisateur peut alors choisir la colonne en fonction de laquelle trier le contenu.  
  
 Toutefois, vous pouvez ajouter un bouton de tri interactif à n'importe quelle zone de texte, pas seulement les en-têtes de colonne. Par exemple, pour une zone de texte placée à l'extérieur d'un groupe de lignes, vous pouvez préciser un tri pour les lignes ou les colonnes du groupe parent, pour les lignes ou les colonnes du groupe enfant ou pour les lignes ou colonnes de détails. Vous pouvez également combiner des champs en une expression de groupe unique, puis trier en fonction de plusieurs champs.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Lorsque vous ajoutez un tri interactif, vous devez spécifier les éléments suivants :  
  
-   **Les éléments à trier :** Lignes ou colonnes ?  
  
-   **Les éléments à trier par :** Un champ qui s’affiche dans une colonne de table ? Un champ non affiché ?  
  
-   **Quel contexte trier :** Par exemple, vous pouvez trier sur les lignes associées aux groupes de lignes ; colonnes associées à des groupes de colonnes ; lignes de détails ; groupes enfants dans un groupe parent ; ou le groupe parent et enfant ensemble.  
  
-   **Quelle zone de texte pour ajouter le bouton de tri :** Dans l’en-tête de colonne ou dans l’en-tête de ligne de groupe ?  
  
-   **Si vous souhaitez synchroniser le tri pour plusieurs régions de données :** Vous pouvez concevoir un rapport afin que lorsque l’utilisateur bascule l’ordre de tri, autres régions de données avec le même ancêtre soient également triées.  
  
 Pour obtenir des instructions détaillées, consultez [Ajouter un tri interactif à un tableau ou une matrice &#40;Générateur de rapports et SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).  
  
 Le tableau suivant récapitule les effets que vous pouvez obtenir en utilisant des boutons de tri interactifs.  
  
|Action|Que trier|Où ajouter le bouton de tri|Sur quel élément trier|Étendue du tri|  
|------------|------------------|----------------------------------|---------------------|----------------|  
|Tri des lignes de détails dans une table sans groupe|Détails|En-tête de colonne|Champ Dataset lié à cette colonne|Région de données|  
|Tri des instances de groupe de niveau supérieur pour une matrice|Groupes|En-tête de colonne|Expression de groupe pour un groupe parent|Région de données|  
|Tri des lignes de détails pour un groupe enfant dans une table|Détails|Ligne d'en-tête de groupe enfant|Champ Dataset sur lequel trier|Groupe enfant|  
|Tri de lignes pour plusieurs groupes de lignes et lignes de détails dans une table|Groupes, mais vous devez redéfinir l'expression de groupe|En-tête de colonne|Agrégation du champ de dataset sur lequel trier|Région de données|  
|Synchroniser l’ordre de tri pour plusieurs régions de données|Groupes|En principe, en-tête de la colonne|Expression de groupe|Dataset|  
  
 Le processeur de rapport applique le tri interactif après que toutes les expressions de tri des groupes et régions de données ont été appliquées. Pour plus d’informations, consultez [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
## <a name="adding-interactive-sort-for-multiple-groups"></a>Ajout du tri interactif à plusieurs groupes  
 Dans une table comportant des groupes de lignes imbriqués basés chacun sur un champ de dataset unique, vous pouvez ajouter un bouton de tri interactif qui trie les valeurs du groupe parent, les valeurs du groupe enfant ou les lignes de détails. Toutefois, vous pouvez souhaiter permettre à l'utilisateur de trier la table à la fois par les valeurs des groupes parent et enfant sans devoir cliquer plusieurs fois.  
  
 Pour ce faire, vous devez modifier la conception de la table pour effectuer le groupement sur une expression qui combine plusieurs champs. Par exemple, pour un dataset comprenant des éléments d'inventaire, si la table d'origine est regroupée par taille puis par couleur, vous pouvez spécifier un groupe unique avec une expression de groupe qui est une combinaison de taille et couleur. Pour plus d’informations, consultez [Ajouter un tri interactif à un tableau ou une matrice &#40;Générateur de rapports et SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Trier des données dans une région de données &#40;Générateur de rapports et SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md)   
 [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Ajouter un tri interactif à un tableau ou une matrice &#40;Générateur de rapports et SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md)  
  
  
