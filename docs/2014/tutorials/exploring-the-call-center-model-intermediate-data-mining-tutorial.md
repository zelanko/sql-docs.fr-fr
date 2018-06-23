---
title: Présentation du modèle de centre d’appels (didacticiel sur l’exploration des données intermédiaires) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9095212c-9068-4dd8-85ce-17a467adeabb
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c3eac8634062e1c77655d78b57aaa2c1d39ce566
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312907"
---
# <a name="exploring-the-call-center-model-intermediate-data-mining-tutorial"></a>Exploration du modèle de centre d'appels (Didacticiel sur l'exploration de données intermédiaire)
  Maintenant que vous avez généré le modèle exploratoire, vous pouvez l'utiliser pour en savoir plus sur vos données à l'aide des outils suivants fournis dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
-   [Visionneuse Microsoft Neural Network](#bkmk_NNviewer) **:** cette visionneuse est disponible dans le **visionneuse de modèle d’exploration de données** onglet du Concepteur d’exploration de données et est conçu pour vous aider à faire des essais avec les interactions dans les données.  
  
-   [Visionneuse d’arborescences contenu générique Microsoft](#bkmk_genviewer) **:** cette visionneuse standard fournit des détails approfondis sur les modèles et les statistiques découverts par l’algorithme lorsqu’il a généré le modèle.  
  
##  <a name="bkmk_NNviewer"></a> Visionneuse du réseau neuronal  
 La visionneuse comporte trois volets : **entrée**, **sortie**, et **Variables**.  
  
 À l’aide de la **sortie** volet, vous pouvez sélectionner des valeurs différentes pour l’attribut prédictible, ou la variable dépendante. Si votre modèle contient plusieurs attributs prédictibles, vous pouvez sélectionner l’attribut à partir de la **attribut de sortie** liste.  
  
 Le **Variables** volet compare les deux résultats que vous avez choisis en termes d’attributs, ou de variables. Les barres de couleur représentent visuellement dans quelle mesure la variable affecte les résultats cibles. Vous pouvez également afficher les variables sous forme de scores de finesse. Un score de finesse est calculé différemment en fonction du type de modèle d'exploration de données utilisé, mais il indique généralement l'amélioration apportée au modèle lorsque cet attribut est utilisé pour la prédiction.  
  
 Le **entrée** volet vous permet d’ajouter les facteurs d’influence au modèle pour tester divers scénarios de simulation.  
  
### <a name="using-the-output-pane"></a>Utilisation du volet Sortie  
 Dans ce modèle initial, vous voulez voir comment divers facteurs affectent le niveau de service. Pour ce faire, vous pouvez sélectionner le niveau de Service à partir de la liste des attributs de sortie et ensuite comparer différents niveaux de service en sélectionnant des plages dans les listes déroulantes pour **valeur 1** et **valeur 2**.  
  
##### <a name="to-compare-lowest-and-highest-service-grades"></a>Pour comparer les niveaux de service les plus bas et les plus élevés  
  
1.  Pour **valeur 1**, sélectionnez la plage comprenant les valeurs les plus faibles. Par exemple, la plage 0-0-0.7 représente les taux d'abandon les plus bas, et par conséquent le meilleur niveau de service.  
  
    > [!NOTE]  
    >  Les valeurs exactes de cette plage peuvent varier en fonction de la façon dont vous avez configuré le modèle.  
  
2.  Pour **valeur 2**, sélectionnez la plage comprenant les valeurs les plus élevées. Par exemple, la plage comprenant la valeur >= 0.12 représente les taux d'abandon les plus élevés, et par conséquent le niveau de service le moins bon. En d'autres termes, 12 % des clients qui ont téléphoné pendant le temps de travail de cette équipe ont raccroché avant de parler à un commercial.  
  
     Le contenu de la **Variables** volet sont mises à jour pour comparer les attributs qui contribuent aux valeurs de résultat. Par conséquent, la colonne de gauche vous montre les attributs associés au meilleur niveau de service, et la colonne de droite vous montre ceux associés au niveau de service le moins bon.  
  
### <a name="using-the-variables-pane"></a>Utilisation du volet Variables  
 Dans ce modèle, il apparaît que `Average Time Per Issue` est un facteur important. Cette variable indique la durée moyenne nécessaire pour répondre à un appel, quel que soit le type d'appel.  
  
##### <a name="to-view-and-copy-probability-and-lift-scores-for-an-attribute"></a>Pour afficher et copier la probabilité et les scores de finesse pour un attribut  
  
1.  Dans le **Variables** volet, placez la souris sur la barre de couleur dans la première ligne.  
  
     Cette barre de couleur vous indique comment fortement `Average Time Per Issue` contribue vers le niveau de service. L'info-bulle affiche un score global, des probabilités et des scores de finesse pour chaque combinaison d'une variable et d'un résultat cible.  
  
2.  Dans le **Variables** volet, avec le bouton toute barre de couleur et sélectionnez **copie**.  
  
3.  Dans une feuille de calcul Excel, avec le bouton droit n’importe quelle cellule et sélectionnez **coller**.  
  
     Le rapport est collé sous forme de table HTML et affiche uniquement les scores correspondant à chaque barre.  
  
4.  Dans une autre feuille de calcul Excel, avec le bouton droit n’importe quelle cellule et sélectionnez **Collage spécial**.  
  
     Le rapport est collé au format texte et inclut les statistiques associées décrites dans la section suivante.  
  
### <a name="using-the-input-pane"></a>Utilisation du volet Entrée  
 Supposons que vous souhaitiez examiner l'incidence d'un facteur spécifique, tel que l'équipe ou le nombre d'opérateurs. Vous pouvez sélectionner une variable particulière à l’aide de la **entrée** volet et le **Variables** volet est automatiquement mis à jour pour comparer les deux groupes sélectionnés, la variable spécifiée précédemment.  
  
##### <a name="to-review-the-effect-on-service-grade-by-changing-input-attributes"></a>Pour passer en revue l'incidence de la modification des attributs d'entrée sur le niveau de service  
  
1.  Dans le **entrée** volet, pour **attribut**, sélectionnez la touche MAJ enfoncée.  
  
2.  Pour **valeur**, sélectionnez **AM**.  
  
     Le **Variables** mises à jour du volet pour montrer l’impact sur le modèle lors de l’équipe sélectionnée est **AM**. Toutes les autres sélections restent inchangées ; vous comparez toujours les niveaux de services les plus bas et les plus élevés.  
  
3.  Pour **valeur**, sélectionnez **PM1**.  
  
     Le **Variables** volet des mises à jour pour montrer l’impact sur le modèle lorsque l’équipe change.  
  
4.  Dans le **entrée** volet, cliquez sur la ligne vide suivante sous **attribut**, puis sélectionnez les appels. Pour **valeur**, sélectionnez la plage qui indique le plus grand nombre d’appels.  
  
     Une nouvelle condition d'entrée est ajoutée à la liste. Le **Variables** volet des mises à jour pour montrer l’impact sur le modèle pour une équipe particulière lorsque le volume d’appels est la plus élevé.  
  
5.  Continuez à modifier les valeurs de Shift (Équipe) et de Calls (Appels) afin de rechercher les corrélations intéressantes entre l'équipe, le volume d'appels et le niveau de service.  
  
    > [!NOTE]  
    >  Pour effacer le **entrée** volet afin que vous pouvez utiliser des attributs différents, cliquez sur **actualiser le contenu de l’Observateur**.  
  
### <a name="interpreting-the-statistics-provided-in-the-viewer"></a>Interprétation des statistiques fournies dans la visionneuse  
 Des temps d'attente plus longs sont un prédicteur fort d'un taux d'abandon élevé, ce qui correspond à un niveau de service médiocre. Cela peut sembler être une conclusion évidente ; toutefois, le modèle d'exploration de données vous fournit des données statistiques supplémentaires afin de vous aider à interpréter ces tendances.  
  
-   **Score**: valeur qui indique l’importance de cette variable pour établir une discrimination entre les résultats. Plus le score est élevé, plus l'incidence de la variable sur le résultat est importante.  
  
-   **Probabilité de value 1**: pourcentage qui représente la probabilité de cette valeur pour ce résultat.  
  
-   **Probabilité de value 2**: pourcentage qui représente la probabilité de cette valeur pour ce résultat.  
  
-   **Finesse pour Value 1** et **finesse pour Value 2**: Scores qui représentent l’impact de l’utilisation de cette variable particulière pour prévoir les résultats de la valeur 1 et valeur 2. Plus le score est élevé, plus la variable est appropriée pour prédire les résultats.  
  
 Le tableau suivant contient des exemples de valeurs pour les principaux facteurs d'influence. Par exemple, le **probabilité de value 1** est 60,6 % et **probabilité de value 2** est 8,30 %, ce qui signifie que la durée moyenne par problème lors de la plage 44-70 minutes, 60,6 % des cas ont été dans l’équipe ayant les niveaux de service la plus élevée (valeur 1) et 8,30 % des cas étaient dans l’équipe ayant les niveaux de service plus mauvais (Value 2).  
  
 Vous pouvez tirer des conclusions de cette information. Un temps de réponse aux appels plus court (plage 44-70) contribue fortement à un meilleur niveau de service (plage 0.00-0.07). Le score (92.35) vous indique que cette variable est très importante.  
  
 Toutefois, lorsque vous parcourez la liste des facteurs contributeurs, vous voyez d'autres facteurs dont les effets sont plus subtils et plus difficiles à interpréter. Par exemple, l'équipe semble avoir une influence sur le service, mais les scores de finesse et les probabilités relatives indiquent que l'équipe n'est pas un facteur majeur.  
  
|Attribute|Valeur|Privilégie \< 0.07|Privilèges >= 0.12|  
|---------------|-----------|--------------------|----------------------|  
|Average Time Per Issue|89.087-120.000||Score : 100<br /><br /> Probabilité de Value1 : 4,45 %<br /><br /> Probabilité de Value2 : 51.94 %<br /><br /> Finesse pour Value1 : 0.19<br /><br /> Finesse pour Value2 : 1,94|  
|Average Time Per Issue|44.000-70.597|Score : 92.35<br /><br /> Probabilité de Value1 : 60.06 %<br /><br /> Probabilité de Value2 : 8,30 %<br /><br /> Finesse pour Value1 : 2.61<br /><br /> Finesse pour Value2 : 0.31||  
  
 [Retour au début](#bkmk_NNviewer)  
  
##  <a name="bkmk_genviewer"></a> Visionneuse de l’arborescence de contenu générique Microsoft  
 Cette visionneuse peut être utilisée pour afficher des informations encore plus détaillées créées par l'algorithme lors du traitement du modèle. Le **visionneuse d’arborescence de contenu MicrosoftGeneric** représente le modèle d’exploration de données sous la forme d’une série de nœuds, où chaque nœud représente appris sur les données d’apprentissage. Cette visionneuse peut être utilisée avec tous les modèles, mais le contenu des nœuds est différent en fonction du type de modèle.  
  
 Pour les modèles de réseau neuronal ou les modèles de régression logistique, vous pouvez rechercher le nœud des statistiques marginales (`marginal statistics node`), qui est particulièrement utile. Ce nœud contient des statistiques dérivées sur la distribution des valeurs dans vos données. Ces informations peuvent être utiles si vous voulez obtenir un résumé des données sans avoir à écrire de nombreuses requêtes T-SQL. Le graphique des valeurs de placement dans un conteneur dans la rubrique précédente a été dérivé du nœud des statistiques marginales.  
  
#### <a name="to-obtain-a-summary-of-data-values-from-the-mining-model"></a>Pour obtenir un résumé des valeurs de données à partir du modèle d'exploration de données  
  
1.  Dans le Concepteur d’exploration de données, dans le **visionneuse de modèle d’exploration de données** onglet, sélectionnez \<nom du modèle d’exploration de données >.  
  
2.  À partir de la **visionneuse** liste, sélectionnez **visionneuse d’arborescences contenu générique Microsoft**.  
  
     La vue du modèle d'exploration de données est actualisée pour afficher une hiérarchie de nœuds dans le volet gauche et une table HTML dans le volet droit.  
  
3.  Dans le **légende du nœud** volet, cliquez sur le nœud qui possède le nom est 10000000000000000.  
  
     Le nœud de niveau supérieur de tout modèle est toujours le nœud racine du modèle. Dans un modèle de réseau neuronal ou de régression logistique, le nœud situé immédiatement sous ce nœud est le nœud des statistiques marginales.  
  
4.  Dans le **détails du nœud** volet, faites défiler vers le bas jusqu'à ce que vous trouviez la ligne NODE_DISTRIBUTION.  
  
5.  Faites défiler la table NODE_DISTRIBUTION pour afficher la distribution des valeurs telle que calculée par l’algorithme de réseau neuronal.  
  
 Pour utiliser ces données dans un rapport, vous pouvez sélectionner puis copier les informations correspondant à des lignes spécifiques, ou utiliser la requête DMX (Data Mining Extensions) suivante pour extraire le contenu complet du nœud.  
  
```  
SELECT *   
FROM [Call Center EQ4].CONTENT  
WHERE NODE_NAME = '10000000000000000'  
```  
  
 Vous pouvez également utiliser la hiérarchie de nœuds et les détails de la table NODE_DISTRIBUTION pour parcourir des chemins d'accès individuels dans le réseau neuronal et afficher des statistiques provenant de la couche masquée. Pour plus d’informations, consultez [exemples de requête de modèle de réseau neuronal](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md).  
  
 [Retour au début](#bkmk_NNviewer)  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Ajout d’un modèle de régression logistique à la Structure de centre d’appels &#40;intermédiaire Didacticiel d’exploration de données&#41;](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exploration du contenu du modèle pour les modèles de réseau neuronal &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)   
 [Exemples de requête de modèle de réseau neuronal](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)   
 [Référence technique de Microsoft Neural Network algorithme](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)   
 [Modifier la discrétisation d’une colonne dans un modèle d’exploration de données](../../2014/analysis-services/data-mining/change-the-discretization-of-a-column-in-a-mining-model.md)  
  
  