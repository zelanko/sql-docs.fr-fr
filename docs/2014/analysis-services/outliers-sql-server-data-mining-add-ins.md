---
title: Valeurs hors norme (compléments d’exploration de données SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exceptions [data mining]
- data preparation
- outliers [data mining]
- data cleaning
ms.assetid: e6fa7c62-4005-4792-9211-3b699377a517
author: minewiskan
ms.author: owend
ms.openlocfilehash: ecc7cba81a394664b2bdb6a60b6c5f8110760f44
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547276"
---
# <a name="outliers-sql-server-data-mining-add-ins"></a>Valeurs hors norme (Compléments d'exploration de données SQL Server)
  ![Assistant Valeurs hors norme sur le ruban Exploration de données](media/dmc-outliers.gif "Assistant Valeurs hors norme sur le ruban Exploration de données")  
  
 Une valeur hors *norme signifie une* valeur de données problématique pour l’une des raisons suivantes :  
  
-   La valeur se trouve en dehors de la plage prévue.  
  
-   Les données ont été entrées de façon incorrecte.  
  
-   La valeur est manquante.  
  
-   Les données se composent d'un espace ou de tout autre chaîne de valeur NULL.  
  
-   La valeur est exacte, mais à l'extérieure de la distribution et peut avoir un impact significatif sur le modèle.  
  
 Le Client d'exploration de données pour Excel vous aide à détecter ces données, puis met à jour les valeurs ou les supprime. Par exemple, remplacez des valeurs hors normes par une moyenne mathématique ou supprimez des lignes qui contiennent des valeurs potentiellement incorrectes.  
  
## <a name="handling-outliers"></a>Gestion des observations aberrantes  
 L’Assistant **suppression** des valeurs hors norme vous propose plusieurs outils pour gérer les valeurs hors norme de manière appropriée :  
  
-   Tout d'abord, vous pouvez explorer les données afin de mieux comprendre la distribution des valeurs et la relation des observations aberrantes et des autres données.  
  
     Par exemple, vous pouvez utiliser la tâche **Explorer les données** pour examiner et corriger les valeurs. L’Assistant **suppression** des valeurs hors norme affiche également un graphique, une ligne ou un graphique à barres, pour vous aider à comprendre la distribution de toutes les valeurs.  
  
-   Ensuite, vous pouvez utiliser l' **Assistant valeurs** hors norme pour supprimer ou modifier les valeurs hors norme. La méthode qui vous utilisez varie selon que les valeurs sont discrètes ou continues.  
  
     L'Assistant affiche des valeurs discrètes dans un graphique à barres, où chaque barre représente une valeur spécifique et la hauteur de la barre indique le nombre de cas pour chaque valeur. En faisant glisser le contrôle de seuil sur le graphique, vous pouvez éliminer les barres qui représentent des groupes de valeurs extrêmes ou mauvaises.  
  
-   L'Assistant affiche ou des valeurs continues sur un graphique à barres ou un graphique en courbes. Dans le graphique en courbes, la valeur est représentée sur l'axe des abscisses (X) et le nombre de valeurs sur l'axe des ordonnées (Y).  
  
     Vous pouvez contrôler s’il faut supprimer ou conserver les valeurs aux extrémités inférieure et supérieure du graphique en modifiant les valeurs **minimale** et **maximale** , ou en faisant glisser les barres. Lorsque vous modifiez les paramètres de valeurs minimales et maximales, les données qui seront supprimées sont signalées par un ombrage dans le graphique.  
  
 Après avoir sélectionné les observations aberrantes à utiliser, vous indiquez à l'Assistant comment les gérer. Vous pouvez supprimer les lignes qui contiennent les valeurs d'observation aberrante ou vous pouvez spécifier une valeur de remplacement, telle qu'une moyenne, une valeur null ou une autre valeur de votre choix.  
  
 Enfin, l'Assistant vous propose des options pour afficher les nouvelles données. Vous pouvez remplacer les données d'origine par les nouvelles valeurs, ajouter une nouvelle colonne au tableau qui contient les nouvelles valeurs ou créer une nouvelle feuille de calcul qui contient les données mises à jour.  
  
### <a name="using-the-outlier-wizard"></a>Utilisation de l'Assistant Suppression des observations aberrantes  
  
1.  Dans le ruban **exploration de données** , cliquez sur nettoyer les **données**, **puis sélectionnez valeurs**hors norme.  
  
2.  Dans la boîte de dialogue **Sélectionner les données source** , sélectionnez une table de données Excel ou une plage de cellules, puis cliquez sur **suivant**.  
  
    > [!WARNING]  
    >  Vous ne pouvez pas utiliser **l’Assistant valeurs** hors norme sur des données externes, sauf si vous le copiez d’abord dans Excel.  
  
3.  Dans la boîte de dialogue **Sélectionner une colonne** , sélectionnez une **seule** colonne.  
  
     Cliquez sur **Suivant**.  
  
4.  Dans la boîte de dialogue **spécifier les seuils** , examinez la distribution des données.  
  
    -   Si la colonne contient des valeurs discrètes, l'Assistant affiche un histogramme contenant le nombre de chaque valeur discrète.  
  
         En supposant que les valeurs hors norme sont de rares valeurs, vous pouvez les filtrer en modifiant la valeur **minimale** .  
  
    -   Si la colonne contient des données numériques, vous pouvez cliquer sur le bouton **afficher comme discret** ou sur le bouton **afficher en tant que numérique** pour basculer entre l’affichage des valeurs dans un graphique à barres ou un graphique en courbes.  
  
5.  Dans la boîte de dialogue **spécifier les seuils** , choisissez la plage de données que vous souhaitez conserver en tapant une valeur minimale et maximale, ou en faisant glisser les barres de curseur. Cliquez sur **Suivant**.  
  
6.  Dans la boîte de dialogue **gestion des** valeurs hors norme, indiquez si vous souhaitez que les valeurs soient supprimées ou remplacées, puis cliquez sur **suivant**.  
  
7.  Dans la boîte de dialogue **Sélectionner la destination** , spécifiez l’emplacement où vous souhaitez enregistrer les nouvelles données.  
  
### <a name="related-options"></a>Options connexes  
 L'Assistant fournit ces options :  
  
|**Options**|**Commentaire**|  
|-----------------|-----------------|  
|**Sélectionner une colonne**|Vous pouvez travailler avec une seule colonne à la fois.|  
|**Spécifier la gestion des seuils**|Définissez un seuil en utilisant **minimum** pour exclure les valeurs qui se trouvent dans moins de lignes que la valeur de seuil.<br /><br /> Initialement, la valeur **minimale** est égale à la valeur ayant le moins de lignes et vous ne pouvez pas définir la valeur minimale inférieure à cette valeur.|  
|**Gestion des valeurs hors norme**|Si vous décidez de supprimer des valeurs hors norme, modifiez les données dans la feuille de calcul active, ou créez une copie des données dans une nouvelle feuille de calcul.|  
  
## <a name="see-also"></a>Voir aussi  
 [Explorez les &#40;de données SQL Server les compléments d’exploration de données&#41;](explore-data-sql-server-data-mining-add-ins.md)  
  
  
