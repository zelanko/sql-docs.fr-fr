---
title: Exploration d’un modèle de règles d’association | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining model, association
- mining models, viewing
- association [data mining]
ms.assetid: faffe208-7a64-4ec6-825f-ecbaa79caff7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 30ff9705949be3fb9bf99d985d0db1aa17d93ab1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66088470"
---
# <a name="browsing-an-association-rules-model"></a>Exploration d'un modèle d'exploration de données Règles d'association
  Lorsque vous ouvrez un modèle d’association à l’aide de l’outil **Parcourir**, le modèle est affiché dans une visionneuse interactive, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]similaire à la visionneuse des règles d’association dans.  La visionneuse vous permet de voir d'un seul coup d'œil les éléments corrélés les uns aux autres, et d'afficher les règles que vous pouvez utiliser pour la prédiction ou pour formuler des recommandations.  
  
##  <a name="BKMK_ViewerTabs"></a>Explorer le modèle  
 Lorsque vous ouvrez un modèle d’exploration de données qui a [!INCLUDE[msCoName](../includes/msconame-md.md)] été créé à l’aide de l’algorithme de règles d’association, la fenêtre **Parcourir** comprend les vues suivantes, chacune conçue pour vous permettre d’explorer un aspect différent du modèle :  
  
-   [Jeux d’éléments](#BKMK_Itemsets)  
  
-   [Matière](#BKMK_Rules)  
  
-   [Réseau de dépendances](#BKMK_Dependency)  
  
 Prenez note de l’option sous chaque onglet, **afficher le nom long** . En sélectionnant cette option, vous pouvez afficher ou masquer la table d'origine du jeu d'éléments, et raccourcir ou développer le nom de la règle ou du jeu d'éléments. Cette option est particulièrement utile lorsque vos données de cas et vos données d'attribut sont issues de sources de données différentes.  
  
 Pour tester avec un modèle d'association, utilisez l'exemple de données de l'onglet Association du classeur d'exemple, et créez un modèle d'association à l'aide de toutes les valeurs par défaut. Vous pouvez également créer un modèle d’analyse de panier d’achat et l’ouvrir à l’aide de **Parcourir**.  
  
###  <a name="BKMK_Itemsets"></a>Jeux d’éléments  
 L’onglet **jeux d’éléments** est un bon point de départ pour explorer un modèle d’association. Il affiche la liste des éléments que le modèle a identifiés comme apparaissant fréquemment ensemble.  
  
 ![Liste des éléments dans un modèle d'association](media/dm13-association-itemsets.gif "Liste des éléments dans un modèle d'association")  
  
 Un exemple habituel de jeux d'éléments est un modèle de panier d'achat où un jeu d'éléments représente des paires ou des ensembles de produits que les clients achètent souvent en même temps. Cependant, en fonction de la manière dont vous regroupez et classez vos éléments, le jeu d'éléments peut contenir une série de films que les clients commandent au cours d'une certaine période, ou des événements qui tendent à se produire dans un lieu donné.  
  
 Un *jeu d’éléments* peut contenir un seul élément à deux, trois ou toutefois, un grand nombre est défini comme taille de jeu d’éléments maximale pour le modèle. Pour chaque jeu d’éléments, la visionneuse affiche la *prise en charge*, la *probabilité*et la *taille*du jeu d’éléments. Le support et la probabilité sont les statistiques principales utilisées pour classer les jeux d'éléments et les règles générées par un modèle d'association. Ces valeurs sont également utilisées pour calculer et décrire leur importance.  
  
 **Prise en charge**. La prise en charge désigne le nombre maximal de cas ou de lignes de données d'entrée de cet élément. Par exemple, si un jeu d’éléments contient deux éléments qui se trouvent dans un panier d’achat, le nombre indiqué dans la colonne **support** indique le nombre de fois que cette combinaison d’éléments s’est produite dans les données sources.  
  
 **Taille**. En modifiant la taille d'un jeu d'éléments, vous contrôlez la longueur de la liste d'éléments. Si vous ne souhaitez pas voir les produits uniques dans la liste, modifiez l’option **taille minimale du jeu d’éléments**, à 2 ou plus.  La restriction de la liste en augmentant la taille minimale des jeux d'éléments vous permet de rechercher des séquences très spécifiques. Cela peut être utile si vous utilisez un jeu de données de grande taille.  
  
 Vous pouvez filtrer le nombre de jeux d’éléments affichés dans l’onglet en modifiant les valeurs de **prise en charge minimale** et de **lignes au maximum** . Si vous augmentez la valeur de **prise en charge minimale** , la liste affichera moins de jeux d’éléments, mais le jeux d’éléments sera le plus courant dans les données d’entrée. Une autre question, que vous pouvez explorer à l’aide de l’onglet **règles** , est le même que le rôle important.  
  
 Notez que la modification de la valeur de prise en charge ou d’autres contrôles de l’onglet **jeux d’éléments** modifie uniquement les éléments affichés et n’affecte pas le modèle sous-jacent. Si vous souhaitez générer moins ou plus d’jeux d’éléments, ou limiter leur taille, vous devez utiliser les paramètres, `MINIMUM_SUPPORT` et `MAXIMUM_SUPPORT`, disponibles dans la boîte de dialogue **paramètres d’algorithme** .  
  
##### <a name="explore-the-itemsets-list"></a>Explorer la liste de jeux d'éléments  
  
1.  Cliquez sur la colonne **support** pour effectuer un tri en prenant en charge le plus élevé au plus bas. Cela vous donnera une idée de ce que les clients achètent le plus souvent.  
  
2.  Pour vous concentrer sur un jeu d’éléments particulier d’intérêt, parmi les nombreuses combinaisons possibles, tapez du texte dans la zone **filtre jeu d’éléments** .  
  
     Ici, nous `Gloves`avons tapé. Lorsque vous appliquez le filtre, la liste est actualisée pour afficher uniquement les éléments contenant des gants. Cela vous permet de vous concentrer sur les transactions où les clients ont acheté des gants et d'autres éléments.  
  
     L'option **Filtrer le jeu d'éléments** affiche également une liste des filtres que vous avez utilisés précédemment.  
  
3.  Modifiez la valeur de la **taille minimale de jeu d’éléments** pour filtrer les clients qui ont acheté uniquement des gants et aucun autre élément.  
  
4.  Cliquez sur la liste déroulante de l’option **Afficher**pour contrôler la façon dont les attributs sont affichés :  
  
    -   **Afficher le nom et la valeur de l’attribut**  
  
    -   **Afficher la valeur de l’attribut uniquement**  
  
    -   **Afficher le nom de l’attribut uniquement**  
  
     Notez comment les noms changent. Dans le cas d'un modèle de panier d'achat, créé à partir de tables imbriquées de produits achetés par plusieurs clients, le nom de l'attribut est généralement le nom du produit, et la présence du produit dans la liste est signalée comme `Existing`, indiquant que le client les a achetés.  
  
     L'opposé de `Existing` est `Missing`, qui est un attribut très utile pour approfondir l'exploration des données. Par exemple, supposons que le jeu d’éléments A + B est tellement très populaire que vous souhaitez trouver les clients qui ont acheté l’article A mais pas l’article B. Vous pouvez effectuer cette opération en utilisant une requête de prédiction et en récupérant les transactions avec l’une, mais pas l’autre, et effectuer d’autres analyses sur celles-ci. Pour plus d’informations sur la création de requêtes de prédiction sur des modèles d’association, consultez [exemples de requêtes de modèle d’association](data-mining/association-model-query-examples.md) dans documentation en ligne de SQL Server  
  
5.  Pour forcer la réaffichage de la liste des jeux d’éléments à l’aide de vos nouveaux critères de filtre, vous pouvez activer ou désactiver la case à cocher **afficher le nom long** .  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Rules"></a>Matière  
 L’onglet **règles** combine des informations sur les jeux d’éléments et leur valeur relative.  
  
 ![Liste des règles créées par un modèle d'association](media/dm13-association-rules.gif "Liste des règles créées par un modèle d'association")  
  
 La *probabilité* représente la fraction des cas du jeu de données qui contiennent la combinaison ciblée d’éléments. La probabilité est semblable au concept statistique de *confiance*et vous donne une indication de la probabilité que le résultat d’une règle se produise. Vous pouvez modifier la valeur de **probabilité minimale** dans ce volet pour filtrer les règles affichées.  
  
 La valeur de **probabilité minimale** que vous voyez initialement est la valeur de seuil qui a été utilisée par l’algorithme lors de la génération du modèle. Une fois le modèle terminé, vous ne pouvez pas réduire cette valeur, mais vous pouvez l’augmenter pour afficher uniquement les éléments de probabilité plus élevée.  
  
 L' *importance* est conçue pour mesurer l’utilité d’une règle. Une règle très courante peut être si omniprésente qu'elle n'a qu'une valeur d'information minime. Plus l'importance est élevée, plus la règle est utile pour prédire le résultat. Dans l’outil [analyse du panier d’achat &#40;table outils pour Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) , l’importance peut être associée au prix des articles pour déterminer les offres qui sont potentiellement plus précieuses en termes de ventes.  
  
##### <a name="explore-the-rules-list"></a>Explorer la liste de règles  
  
1.  Essayez de cliquer sur les en-têtes de colonne- **probabilité**, **importance**et **règle** pour voir comment les données sont modifiées.  
  
2.  Utilisez l’option de **règle de filtre** pour saisir des valeurs et vous concentrer sur les règles ciblées.  
  
     Par exemple, si vous souhaitez voir toutes les règles qui prédisent ce que les clients sont susceptibles d’acheter avec des gants, tapez « gants » dans la zone de texte et actualisez le volet.  
  
     L'option **Filtrer le jeu d'éléments** affiche également une liste des filtres que vous avez utilisés précédemment.  
  
3.  Pour forcer la réaffichage de la liste des règles à l’aide des critères de filtre, vous pouvez activer ou désactiver la case à cocher **afficher le nom long** .  
  
4.  Utilisez l’option **Afficher** pour contrôler le mode d’affichage des noms de règles.  
  
5.  Définissez la valeur de l’option **nombre maximal de lignes** sur 100, puis cliquez sur **copier dans Excel**.  
  
     Notez que la modification de cette valeur n’a aucun effet sur la quantité de données dans le modèle ; il contrôle simplement le nombre de lignes dans la liste d’affichage. Cette option est utile si vous travaillez sur de très grands modèles.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Dependency"></a>Réseau de dépendances  
 L’onglet **réseau de dépendances** est une carte visuelle des corrélations entre les éléments. Chaque ovale dans le graphique (désigné sous le terme de *nœud*) représente une paire attribut-valeur, telle que « veste = existing » ou « Age = 1-30 ».  Chaque ligne reliant les ovales (appelée *arête*) représente un type de corrélation.  
  
 ![Diagramme de réseau de dépendances pour un modèle d'association](media/dm13-association-dependencynetwork.gif "Diagramme de réseau de dépendances pour un modèle d'association")  
  
##### <a name="explore-the-dependency-network"></a>Explorer le réseau de dépendances  
  
1.  Cliquez sur le bouton **Rechercher** et utilisez la boîte de dialogue **Rechercher un nœud** pour saisir un élément d’intérêt.  
  
     Par exemple, tapez « gants », puis agrandissez le graphique dans la fenêtre pour voir facilement les résultats.  
  
     Le nœud qui contient les éléments est mis en surbrillance tandis que les flèches qui pointent sur le nœud représentent les règles qui relient les éléments.  
  
     La direction de la flèche indique la direction de la règle. Par exemple, si une personne qui achète des gants est également susceptible d’acheter une veste, la flèche commence à partir du nœud « gant » et se termine sur le nœud « veste ».  
  
     Pour obtenir des statistiques supplémentaires sur cette règle, vous pouvez cliquer sur l’onglet **règles** et rechercher une règle avec la description « gant-existing »-> « veste-Existing ».  
  
2.  Cliquez sur le curseur à gauche de la visionneuse et faites-le glisser.  
  
     Le curseur sert à filtrer en fonction de la probabilité des règles. Le déplacement du curseur vers le bas affiche uniquement les règles les plus fortes.  
  
3.  Cliquez sur **copier dans Excel** pour copier une capture instantanée de la fenêtre active dans Excel.  
  
     Vous ne pouvez pas utiliser le graphique que vous copiez dans Excel ; Si vous avez besoin d’un graphique de réseau interactif, utilisez l' [affichage des modèles d’exploration de données dans Visio &#40;compléments d’exploration de données&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md).  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
## <a name="more-about-association-models"></a>Pour plus d'informations sur les modèles d'association  
 Vous pouvez utiliser la fonctionnalité **Parcourir** pour ouvrir et explorer tout modèle qui a été créé à l’aide de l’algorithme Microsoft Association Rules. Cela comprend les modèles créés à l’aide de l' [analyse du panier d’achat &#40;la table outils pour Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) outil, dans le [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]ruban outils d’analyse de **table** ou dans.  
  
 Si vous créez un modèle de règles d'association à l'aide de l'outil Analyse du panier d'achat, de nombreuses options avancées sont configurées automatiquement.  
  
 Si vous souhaitez définir des paramètres avancés ou modifier la probabilité et la prise en charge minimale, utilisez l' [Assistant association &#40;assistant&#41;client d’exploration de données pour excel](associate-wizard-data-mining-client-for-excel.md) de l’Assistant, ou créez votre propre modèle à l’aide de l’option [Ajouter un modèle à la structure &#40;les compléments d’exploration de données pour la modélisation Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md) .  
  
-   **Jeux d’éléments :** Lorsque vous créez le modèle, vous pouvez également contrôler le nombre de jeux d’éléments générés en assignant une valeur au paramètre MINIMUM_PROBABILITY. Ce paramètre est disponible dans la Boîte de dialogue Paramètres d'algorithme.  
  
-   **Règles :** L' [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme de règles d’association utilise des valeurs de probabilité pour limiter le nombre de règles générées. Vous pouvez contrôler le nombre de règles en définissant les paramètres `MINIMUM_PROBABILITY` ou `MINIMUM _IMPORTANCE`.  
  
 Pour plus d’informations sur la configuration des paramètres avancés, consultez [algorithmes d’exploration de données &#40;SQL Server compléments d’exploration de données&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exploration des modèles dans Excel &#40;SQL Server les compléments d’exploration de données&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
