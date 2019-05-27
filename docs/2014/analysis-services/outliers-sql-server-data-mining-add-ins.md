---
title: Valeurs hors norme (SQL Server Data Mining Add-ins) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 3043c8f63433396f059f5c456512ad4ba2bffd93
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66072138"
---
# <a name="outliers-sql-server-data-mining-add-ins"></a>Valeurs hors norme (Compléments d'exploration de données SQL Server)
  ![Assistant valeurs hors norme dans le ruban Exploration de données](media/dmc-outliers.gif "Assistant valeurs hors norme dans le ruban Exploration de données")  
  
 Un *observation ABERRANTE* signifie une valeur de données qui pose problème pour l’une des raisons suivantes :  
  
-   La valeur se trouve en dehors de la plage prévue.  
  
-   Les données ont été entrées de façon incorrecte.  
  
-   La valeur est manquante.  
  
-   Les données se composent d'un espace ou de tout autre chaîne de valeur NULL.  
  
-   La valeur est exacte, mais à l'extérieure de la distribution et peut avoir un impact significatif sur le modèle.  
  
 Le Client d'exploration de données pour Excel vous aide à détecter ces données, puis met à jour les valeurs ou les supprime. Par exemple, remplacez des valeurs hors normes par une moyenne mathématique ou supprimez des lignes qui contiennent des valeurs potentiellement incorrectes.  
  
## <a name="handling-outliers"></a>Gestion des observations aberrantes  
 Le **suppression des observations aberrantes** Assistant vous propose plusieurs outils pour gérer les observations aberrantes :  
  
-   Tout d'abord, vous pouvez explorer les données afin de mieux comprendre la distribution des valeurs et la relation des observations aberrantes et des autres données.  
  
     Par exemple, vous pouvez utiliser la **Explorer les données** tâche pour examiner et corriger les valeurs. Le **suppression des observations aberrantes** Assistant affiche également un graphique, une ligne ou un graphique à barres, pour vous aider à mieux comprendre la distribution de toutes les valeurs.  
  
-   Ensuite, vous pouvez utiliser la **valeurs hors norme** Assistant pour supprimer ou modifier des valeurs hors norme. La méthode qui vous utilisez varie selon que les valeurs sont discrètes ou continues.  
  
     L'Assistant affiche des valeurs discrètes dans un graphique à barres, où chaque barre représente une valeur spécifique et la hauteur de la barre indique le nombre de cas pour chaque valeur. En faisant glisser le contrôle de seuil sur le graphique, vous pouvez éliminer les barres qui représentent des groupes de valeurs extrêmes ou mauvaises.  
  
-   L'Assistant affiche ou des valeurs continues sur un graphique à barres ou un graphique en courbes. Dans le graphique en courbes, la valeur est représentée sur l'axe des abscisses (X) et le nombre de valeurs sur l'axe des ordonnées (Y).  
  
     Vous pouvez contrôler s’il faut supprimer ou conserver les valeurs aux extrémités supérieure et inférieure du graphique en modifiant le **Minimum** et **maximale** valeurs, ou en faisant glisser les barres. Lorsque vous modifiez les paramètres de valeurs minimales et maximales, les données qui seront supprimées sont signalées par un ombrage dans le graphique.  
  
 Après avoir sélectionné les observations aberrantes à utiliser, vous indiquez à l'Assistant comment les gérer. Vous pouvez supprimer les lignes qui contiennent les valeurs d'observation aberrante ou vous pouvez spécifier une valeur de remplacement, telle qu'une moyenne, une valeur null ou une autre valeur de votre choix.  
  
 Enfin, l'Assistant vous propose des options pour afficher les nouvelles données. Vous pouvez remplacer les données d'origine par les nouvelles valeurs, ajouter une nouvelle colonne au tableau qui contient les nouvelles valeurs ou créer une nouvelle feuille de calcul qui contient les données mises à jour.  
  
### <a name="using-the-outlier-wizard"></a>Utilisation de l'Assistant Suppression des observations aberrantes  
  
1.  Dans le **d’exploration de données** ruban, cliquez sur **nettoyer les données**, puis sélectionnez **valeurs hors norme**.  
  
2.  Dans le **sélectionner les données Source** boîte de dialogue, sélectionnez une table de données Excel ou une plage de cellules, puis cliquez sur **suivant**.  
  
    > [!WARNING]  
    >  Vous ne pouvez pas utiliser le **valeurs hors norme** Assistant sur des données externes, sauf si vous le copiez tout d’abord dans Excel.  
  
3.  Dans le **sélectionner la colonne** boîte de dialogue, sélectionnez un **unique** colonne.  
  
     Cliquer sur **Suivant**.  
  
4.  Dans le **spécifier les seuils** boîte de dialogue zone, passez en revue la distribution des données.  
  
    -   Si la colonne contient des valeurs discrètes, l'Assistant affiche un histogramme contenant le nombre de chaque valeur discrète.  
  
         En supposant que les valeurs hors norme est des valeurs rares, vous pouvez les filtrer en modifiant le **Minimum** valeur.  
  
    -   Si la colonne contient des données numériques, vous pouvez cliquer sur le **vue comme discrètes** bouton ou le **afficher sous la forme numérique** bouton pour basculer entre l’affichage des valeurs dans un graphique à barres ou un graphique en courbes.  
  
5.  Dans le **spécifier les seuils** boîte de dialogue, sélectionnez la plage de données que vous souhaitez conserver en tapant une valeur minimale et maximale, ou en faisant glisser les barres de curseur. Cliquer sur **Suivant**.  
  
6.  Dans le **gestion des observations aberrantes** boîte de dialogue, spécifiez si vous souhaitez que les valeurs soient supprimées ou remplacées, puis cliquez sur **suivant**.  
  
7.  Dans le **sélectionner la Destination** boîte de dialogue, spécifiez où vous souhaitez les nouvelles données à enregistrer.  
  
### <a name="related-options"></a>Options connexes  
 L'Assistant fournit ces options :  
  
|**Options**|**Commentaire**|  
|-----------------|-----------------|  
|**Sélectionnez la colonne**|Vous pouvez travailler avec une seule colonne à la fois.|  
|**Spécifier la gestion des seuils**|Définir un seuil à l’aide **Minimum** pour exclure les valeurs qui sont trouvent dans moins de lignes que la valeur de seuil.<br /><br /> Initialement, la valeur **minimale** est égale à la valeur avec le moins de lignes, et vous ne pouvez pas la valeur minimale inférieure à cette valeur.|  
|**Gestion des valeurs hors norme**|Si vous décidez de supprimer des valeurs hors norme, modifiez les données dans la feuille de calcul active, ou créez une copie des données dans une nouvelle feuille de calcul.|  
  
## <a name="see-also"></a>Voir aussi  
 [Explorer les données &#40;compléments d’exploration de données SQL Server&#41;](explore-data-sql-server-data-mining-add-ins.md)  
  
  
