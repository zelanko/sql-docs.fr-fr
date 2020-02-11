---
title: Exploration du modèle de prévision (Didacticiel intermédiaire sur l’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a00f409-050f-4b92-9763-ba31a6aa3052
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 607f300fbf2138796bb02c66c62386fcc93e6a45
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62992269"
---
# <a name="exploring-the-forecasting-model-intermediate-data-mining-tutorial"></a>Exploration du modèle de prévision (Didacticiel sur l'exploration de données intermédiaire)
  Maintenant que vous avez créé le modèle d’exploration de données prévision, vous pouvez explorer les résultats à l’aide de l’onglet **visionneuse de modèle d’exploration** de données du concepteur d’exploration de données. La [!INCLUDE[msCoName](../includes/msconame-md.md)] visionneuse de la série chronologique contient deux onglets : **graphiques** et **modèle**.  
  
 En outre, vous pouvez utiliser la visionneuse générique d'arborescences Microsoft avec tous les modèles. Chaque vue présente une image légèrement différente des informations comprises dans le modèle de série chronologique.  
  
-   [Onglet Graphiques](#bkmk_Charts)  
  
-   [Onglet Modèle](#bkmk_Model)  
  
-   [Visionneuse de contenu générique Microsoft](#bkmk_Content)  
  
##  <a name="bkmk_Charts"></a>Onglet graphiques  
 L’onglet **graphiques** de la [!INCLUDE[msCoName](../includes/msconame-md.md)] visionneuse de la série chronologique vous montre graphiquement chacune des séries, y compris les données d’historique et les prédictions. Chaque ligne dans le graphique de série chronologique représente une combinaison unique de produit, région et attribut prédictible.  
  
 La légende à droite de la visionneuse répertorie la série chronologique disponible, en fonction des sélections de la liste déroulante. Vous pouvez cocher et décocher les cases de la légende pour indiquer la série chronologique à afficher dans le graphique.  
  
 Vous pouvez également modifier les options d'affichage, telles que les couleurs utilisées pour chaque série chronologique, ou indiquer si les valeurs sont visibles sur les points du graphique.  
  
#### <a name="to-select-a-time-series"></a>Pour sélectionner une série chronologique  
  
1.  Cliquez sur l’onglet **graphiques** de l’onglet **visionneuse de modèle d’exploration de données** , s’il n’est pas visible.  
  
2.  Cliquez sur la liste déroulante située à droite du graphique, puis activez toutes les cases à cocher. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Le graphique doit à présent contenir 24 lignes de série différentes.  
  
3.  Dans les cases à cocher situées à droite du graphique, désactivez les cases à cocher pour masquer temporairement les lignes de toutes les séries basées sur le montant.  
  
     Maintenant, désactivez les cases à cocher en rapport avec les vélos R750 et R250.  
  
     Le graphique contient à présent uniquement les 6 lignes de série suivantes, afin que vous puissiez plus facilement comparer les tendances des vélos M200 et T1000.  
  
    -   **M200 Europe : quantité**  
  
    -   **M200 North America: Quantity**  
  
    -   **M200 Pacific: Quantity**  
  
    -   **T1000 Europe: Quantity**  
  
    -   **T1000 North America: Quantity**  
  
    -   **T1000 Pacific: Quantity**  
  
 ![Prédiction de la quantité des séries M200 et T1000](../../2014/tutorials/media/6series-defaultforecasting.gif "Prédiction de la quantité des séries M200 et T1000")  
  
 Le graphique affiché dans cette visionneuse comprend à la fois des données historiques et des données prédites. Les données prédites sont ombrées pour les distinguer des données historiques. Pour simplifier la comparaison de séries différentes, vous pouvez également modifier les couleurs associées à chaque ligne dans le graphique. Pour plus d’informations, consultez [Modifier les couleurs utilisées dans la visionneuse d’exploration de données](../../2014/analysis-services/data-mining/change-the-colors-used-in-the-data-mining-viewer.md).  
  
 Les lignes de tendance indiquent que le total des ventes enregistré pour toutes les régions est globalement croissant, avec une pointe tous les 12 mois, en décembre. En examinant le graphique, vous pouvez également remarquer que les données pour les vélos T1000 démarrent beaucoup plus tard que celles des séries des autres produits. Ceci est dû au fait qu'il s'agit d'un produit plus récent, mais puisque cette série est basée sur beaucoup moins de données, les prédictions peuvent ne pas être aussi précises.  
  
 Par défaut, cinq étapes de prédiction sont affichées pour chaque série chronologique, affichées sous la forme de lignes en pointillés. Vous pouvez modifier cette valeur pour afficher plus ou moins de prédictions. Vous pouvez également afficher graphiquement l'écart type des prédictions en ajoutant des barres d'erreur au graphique.  
  
#### <a name="to-change-prediction-and-display-options-in-the-chart-view"></a>Pour modifier les options de prédiction et d'affichage dans la vue Graphique  
  
1.  Essayez de modifier progressivement la valeur des **étapes de prédiction** , de la faire passer de **5** à **10**, puis de revenir à **6**.  
  
     Lorsque les données historiques fluctuent beaucoup, ces fluctuations ont tendance à se répéter ou même à s'amplifier lorsque vous augmentez le nombre de prédictions. Vous devrez éventuellement faire des recherches à ce stade, pour comprendre la cause de l'importance de l'augmentation des données historiques, puis choisir d'accepter ces résultats, de rechercher un certain type de correction des données sources, ou d'appliquer un certain type de lissage dans le modèle.  
  
2.  Activez la case à cocher **afficher les écarts** .  
  
     Cette option affiche l'estimation de la marge d'erreur pour chaque valeur prédite.  
  
3.  Notez l'échelle de l'axe des X. Les modifications portant sur les données historiques et prédites sont toujours exprimées en pourcentage, mais les valeurs réelles sont ajustées automatiquement pour correspondre à toutes les valeurs présentées sur le graphique. Vous devez donc être vigilant lorsque vous comparez les modèles à ne pas compter uniquement sur les visuels. Pour obtenir la valeur exacte, ou l’augmentation du pourcentage et la valeur des prédictions, placez le pointeur de la souris sur la ligne en pointillés ou les lignes pleines, ou cliquez sur les lignes pour afficher les valeurs dans la **légende d’exploration de données**.  
  
     **Conseil**: si la **légende d’exploration de données** n’est pas visible, basculez vers la vue de **modèle** , cliquez avec le bouton droit sur n’importe quel nœud, puis sélectionnez **afficher la légende**.  
  
 Une fois ces tendances consultées, vous vous inquiétez du manque de données pour une partie de la série et vous vous demandez si vous pouvez obtenir des prédictions plus fiables en faisant la moyenne des ventes par modèle ou peut-être en calculant la moyenne des ventes par région. Vous allez explorer cette approche lors d'une leçon ultérieure de ce didacticiel.  
  
 [Retour au début](#bkmk_Charts)  
  
##  <a name="bkmk_Model"></a>Onglet modèle  
 L’onglet **modèle** de la [!INCLUDE[msCoName](../includes/msconame-md.md)] visionneuse de la série chronologique dans le concepteur d’exploration de données vous permet d’afficher le modèle de prévision sous la forme d’un graphique d’arborescence.  
  
 D'abord, notez qu'en raison de la description faite par vos données de deux mesures différentes (Montant et Quantité) pour les ventes de plusieurs lignes de produits (T1000, etc.) dans trois régions différentes (Europe, Amérique du Nord, et Pacifique), le modèle que vous avez généré contient réellement 24 arborescences différentes, chacune représentant un modèle des modèles de ventes pour une autre combinaison de région, produit, et attribut prédictible.  
  
 Vous pouvez choisir la combinaison de la gamme de produits, de la région et de la mesure de vente que vous souhaitez afficher en sélectionnant une série dans la liste déroulante **arborescence** de l’onglet **modèle** .  
  
 Que pouvez-vous donc apprendre à partir de l'affichage du modèle sous forme d'arborescence ? À titre d’exemple, comparons deux modèles, un qui a plusieurs niveaux dans l’arborescence et un autre qui a un nœud unique.  
  
-   Lorsqu'un graphique d'arborescence contient un nœud unique, cela signifie que la tendance trouvée dans le modèle est principalement homogène avec le temps. Vous pouvez utiliser ce nœud unique, intitulé **tout**, pour afficher la formule qui décrit la relation entre les variables d’entrée et le résultat.  
  
-   Lorsqu'un graphique d'arbre pour une série chronologique a plusieurs branches, cela signifie que la série chronologique qui a été détectée est trop complexe pour être représentée sous la forme d'une équation unique. Au lieu de cela, le graphique d’arborescence peut contenir plusieurs branches, chaque branche portant les conditions qui ont provoqué le *fractionnement*de l’arborescence. Lorsque l'arborescence se fractionne, chaque branche représente un segment de temps différent, à l'intérieur duquel la tendance peut être décrite comme une équation unique.  
  
     Par exemple, si vous examinez le graphique du graphique et que vous voyez un saut soudain dans le volume des ventes à partir de septembre et que vous continuez jusqu’à la fin de l’année, vous pouvez basculer vers la vue de **modèle** pour afficher la date exacte à laquelle la tendance a changé. Les branches de l’arborescence qui représentent « avant septembre » et « après septembre » contiennent des formules différentes : une formule qui décrit mathématiquement les tendances des ventes jusqu’au fractionnement, et une autre formule qui décrit les tendances des ventes pour septembre jusqu’à vacances de fin d’année.  
  
#### <a name="to-explore-the-decision-tree-for-a-time-series-model"></a>Pour explorer l'arbre de décision d'un modèle de série chronologique  
  
1.  Dans la liste **arborescence** sous l’onglet **modèle** de la visionneuse, sélectionnez la série **T1000 Europe : amount** .  
  
     Cliquez sur le nœud intitulé **tout**.  
  
     Pour un nœud **All** , l’info-bulle qui apparaît contient des informations telles que, le nombre de cas dans la série entière et les équations de série chronologique dérivées de l’analyse des données.  
  
2.  Si la **légende d’exploration de données** n’est pas visible, cliquez avec le bouton droit sur le nœud et sélectionnez **afficher la légende**.  
  
     La **légende d’exploration** de données fournit des informations très identiques à celles de l’info-bulle. Si l'une de vos variables indépendantes est discrète, vous verrez également un histogramme indiquant la distribution des variables dans le nœud.  
  
3.  Sélectionnez à présent une série chronologique différente à afficher. À l’aide de la liste d' **arborescence** sous l’onglet **modèle** de la visionneuse, sélectionnez la série **M200 Amérique du Nord : amount** .  
  
     Le graphique d’arborescence contient maintenant un nœud **tous** et deux nœuds enfants. En examinant les étiquettes situées sur les nœuds enfants, vous pouvez comprendre le degré de modification de la ligne de tendance.  
  
     Pour chaque nœud enfant, la description dans la **légende d’exploration de données** comprend également le nombre de cas dans chaque branche de l’arborescence.  
  
 La liste suivante décrit certaines fonctionnalités supplémentaires de la visionneuse d'arborescence :  
  
-   Vous pouvez modifier la variable représentée dans le graphique à l’aide du contrôle d' **arrière-plan** . Par défaut, les nœuds qui sont plus sombres contiennent plus de cas, car la valeur de l' **arrière-plan** est définie sur **remplissage**. Pour voir le nombre de cas dans un nœud, placez le pointeur de la souris sur un nœud et affichez l’info-bulle qui s’affiche, ou cliquez sur le nœud et affichez les nombres dans la fenêtre **légende du nœud** .  
  
-   La formule de régression du nœud peut également être affichée dans l'info-bulle ou en cliquant sur le nœud. Si vous avez créé un modèle mixte, vous pouvez voir deux formules, une pour ARTXP (dans les nœuds terminaux) et une pour ARIMA (dans le nœud racine de l'arborescence).  
  
-   Les petits losanges sont utilisés dans les nœuds qui représentent des nombres continus. La plage des attributs s'affiche dans la barre sur laquelle le losange est situé. Le losange est centré sur la moyenne du nœud et la largeur du losange représente la variance de l'attribut sur ce nœud.  
  
 [Retour au début](#bkmk_Charts)  
  
##  <a name="bkmk_Content"></a>Facultatif Visionneuse de l’arborescence de contenu générique  
 En plus de la visionneuse personnalisée pour la série [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] chronologique, fournit la **visionneuse de l’arborescence de contenu MicrosoftGeneric** à utiliser avec tous les modèles d’exploration de données. Cette visionneuse offre quelques avantages :  
  
-   Visionneuse de l’algorithme **MTS (Microsoft Time Series**) : cette vue fusionne les résultats des deux algorithmes. Bien que vous puissiez afficher chaque série séparément, vous ne pouvez pas déterminer comment les résultats de chaque algorithme ont été combinés. De plus, dans cette vue, les info-bulles et la légende d'exploration de données affichent uniquement les statistiques les plus importantes.  
  
-   **Visionneuse de l’arborescence de contenu générique**: vous permet de parcourir et d’afficher toutes les séries de données qui ont été utilisées dans le modèle à un moment donné, et si vous avez créé un modèle mixte, les arbres ARIMA et ARTxp sont affichés dans le même graphique.  
  
     Vous pouvez utiliser cette visionneuse pour obtenir toutes les statistiques des deux algorithmes, ainsi que les distributions des valeurs.  
  
     Recommandé pour les utilisateurs expérimentés de l'exploration de données qui souhaitent en savoir plus sur les analyses ARIMA et ARTXP.  
  
#### <a name="to-view-details-for-a-particular-data-series-in-the-generic-content-viewer"></a>Pour consulter des détails pour une série de données particulière dans la visionneuse de contenu générique  
  
1.  Dans l’onglet **visionneuse de modèle d’exploration de données** , sélectionnez Visionneuse de l’arborescence de **contenu générique Microsoft** dans la liste déroulante **visionneuse** .  
  
2.  Dans le volet **légende du nœud** , cliquez sur le nœud de premier niveau (tout).  
  
3.  Dans le volet **Détails du nœud** , affichez la valeur de ATTRIBUTE_NAME.  
  
     Cette valeur vous indique quelle série, ou combinaison de produit et région, est contenue dans ce nœud. Dans l'exemple AdventureWorks, le nœud de premier niveau correspond à la série M200 Europe.  
  
4.  Dans le volet **légende du nœud** , localisez le premier nœud qui a des nœuds enfants.  
  
     Si un nœud de série a des enfants, l’arborescence qui s’affiche sous l’onglet **modèle** de la visionneuse de l’ensemble de temps Microsoft aura également une structure de branchement.  
  
5.  Développez le nœud et cliquez sur l'un des nœuds enfants.  
  
     La colonne NODE_DESCRIPTION du schéma contient la condition qui a provoqué le fractionnement de l'arborescence.  
  
6.  Dans le volet **légende du nœud** , cliquez sur le nœud ARIMA le plus haut, puis développez le nœud jusqu’à ce que tous les nœuds enfants soient visibles.  
  
7.  Dans le volet **Détails du nœud** , affichez la valeur de ATTRIBUTE_NAME.  
  
     Cette valeur vous indique quelle série chronologique est contenue dans ce nœud. Le nœud de premier niveau dans la section ARIMA doit correspondre au nœud de premier niveau dans la section (Tout). Dans l'exemple AdventureWorks, ce nœud contient l'analyse ARIMA de la série M200 Europe.  
  
 Pour plus d’informations, consultez [Contenu du modèle d’exploration de données pour les modèles de séries chronologiques &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md).  
  
 [Retour au début](#bkmk_Charts)  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création de prédictions de série chronologique &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes de modèle de série chronologique](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [Informations techniques de référence sur l’algorithme MTS (Microsoft Time Series)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
