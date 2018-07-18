---
title: Modèle de règles d’une Association de navigation | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining model, association
- mining models, viewing
- association [data mining]
ms.assetid: faffe208-7a64-4ec6-825f-ecbaa79caff7
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4a108693491fba5c706f48a2eaf12b57ee0f3f69
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246149"
---
# <a name="browsing-an-association-rules-model"></a>Exploration d'un modèle d'exploration de données Règles d'association
  Lorsque vous ouvrez un modèle d’association à l’aide **Parcourir**, le modèle est affiché dans une visionneuse interactive semblable à la visionneuse de règles d’Association dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  La visionneuse vous permet de voir d'un seul coup d'œil les éléments corrélés les uns aux autres, et d'afficher les règles que vous pouvez utiliser pour la prédiction ou pour formuler des recommandations.  
  
##  <a name="BKMK_ViewerTabs"></a> Explorer le modèle  
 Lorsque vous ouvrez un modèle d’exploration de données qui a été créé à l’aide de la [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme Microsoft Association Rules, le **Parcourir** fenêtre inclut les vues suivantes, chacune conçue pour vous permettre d’Explorer un aspect différent du modèle :  
  
-   [Jeux d'éléments](#BKMK_Itemsets)  
  
-   [Règles](#BKMK_Rules)  
  
-   [Réseau de dépendances](#BKMK_Dependency)  
  
 Prenez note de l’option sous chaque onglet, **afficher le nom long** . En sélectionnant cette option, vous pouvez afficher ou masquer la table d'origine du jeu d'éléments, et raccourcir ou développer le nom de la règle ou du jeu d'éléments. Cette option est particulièrement utile lorsque vos données de cas et vos données d'attribut sont issues de sources de données différentes.  
  
 Pour tester avec un modèle d'association, utilisez l'exemple de données de l'onglet Association du classeur d'exemple, et créez un modèle d'association à l'aide de toutes les valeurs par défaut. Vous pouvez également créer un modèle d’analyse de panier d’achat et l’ouvrir en utilisant **Parcourir**.  
  
###  <a name="BKMK_Itemsets"></a> Jeux d'éléments  
 Le **jeux d’éléments** onglet est un bon point pour commencer à Explorer un modèle d’association. Il affiche la liste des éléments que le modèle a identifiés comme apparaissant fréquemment ensemble.  
  
 ![Liste d’éléments dans un modèle d’association](media/dm13-association-itemsets.gif "liste d’éléments dans un modèle d’association")  
  
 Un exemple habituel de jeux d'éléments est un modèle de panier d'achat où un jeu d'éléments représente des paires ou des ensembles de produits que les clients achètent souvent en même temps. Cependant, en fonction de la manière dont vous regroupez et classez vos éléments, le jeu d'éléments peut contenir une série de films que les clients commandent au cours d'une certaine période, ou des événements qui tendent à se produire dans un lieu donné.  
  
 Un *jeu d’éléments* peut contenir qu’un seul élément à deux, trois, ou Toutefois, nombreuses est défini en tant que la taille maximale de jeu d’éléments pour le modèle. Pour chaque jeu d’éléments, la visionneuse affiche le jeu d’éléments *prennent en charge*, *probabilité*, et *taille*. Le support et la probabilité sont les statistiques principales utilisées pour classer les jeux d'éléments et les règles générées par un modèle d'association. Ces valeurs sont également utilisées pour calculer et décrire leur importance.  
  
 **Prise en charge**. La prise en charge désigne le nombre maximal de cas ou de lignes de données d'entrée de cet élément. Par exemple, si un jeu d’éléments contient deux éléments sont trouvant dans un achat au panier, le numéro dans le **prise en charge** colonne indique combien de fois qui s’est produite lors de la combinaison d’éléments dans la source de données.  
  
 **Taille**. En modifiant la taille d'un jeu d'éléments, vous contrôlez la longueur de la liste d'éléments. Si vous ne souhaitez pas voir de produit unique dans la liste, modifiez l’option **taille minimale du jeu d’éléments**, à 2 ou plus.  La restriction de la liste en augmentant la taille minimale des jeux d'éléments vous permet de rechercher des séquences très spécifiques. Cela peut être utile si vous utilisez un jeu de données de grande taille.  
  
 Vous pouvez filtrer le nombre de jeux d’éléments qui est affichés sous l’onglet en modifiant le **prise en charge minimale** et **lignes au Maximum** valeurs. Si vous augmentez le **prise en charge minimale** valeur, la liste contiendra moins de jeux d’éléments, mais ces derniers seront les plus courantes existant dans les données d’entrée. Si courants est le même aussi importante est une autre question, que vous pouvez Explorer à l’aide de la **règles** onglet.  
  
 Notez que si vous modifiez la valeur de support ou d’autres contrôles sur le **jeux d’éléments** onglet modifie uniquement les éléments qui sont affichés et n’affectent pas le modèle sous-jacent. Si vous souhaitez générer moins ou plusieurs jeux d’éléments, ou limiter leur taille, vous devez utiliser les paramètres, `MINIMUM_SUPPORT` et `MAXIMUM_SUPPORT`, disponible dans le **paramètres d’algorithme** boîte de dialogue.  
  
##### <a name="explore-the-itemsets-list"></a>Explorer la liste de jeux d'éléments  
  
1.  Cliquez sur le **prennent en charge** colonne pour trier par ordre décroissant prise en charge. Cela vous donnera une idée de ce que les clients achètent le plus souvent.  
  
2.  Pour vous concentrer sur un jeu d’éléments particulier dignes d’intérêt, de plusieurs milliers de combinaisons possibles, tapez du texte dans le **jeu d’éléments de filtre** boîte.  
  
     Ici nous avons tapé `Gloves`. Lorsque vous appliquez le filtre, la liste est actualisée pour afficher uniquement les éléments contenant des gants. Cela vous permet de vous concentrer sur les transactions où les clients ont acheté des gants et d'autres éléments.  
  
     L'option **Filtrer le jeu d'éléments** affiche également une liste des filtres que vous avez utilisés précédemment.  
  
3.  Modifiez la valeur de **taille minimale du jeu d’éléments** pour filtrer les clients qui ont acheté uniquement des gants et aucun autre élément.  
  
4.  Cliquez sur la liste déroulante pour l’option **afficher**, pour contrôler la façon dont les attributs sont affichés :  
  
    -   **Afficher le nom et la valeur de l'attribut**  
  
    -   **Afficher la valeur de l'attribut uniquement**  
  
    -   **Afficher le nom de l'attribut uniquement**  
  
     Notez comment les noms changent. Dans le cas d'un modèle de panier d'achat, créé à partir de tables imbriquées de produits achetés par plusieurs clients, le nom de l'attribut est généralement le nom du produit, et la présence du produit dans la liste est signalée comme `Existing`, indiquant que le client les a achetés.  
  
     L'opposé de `Existing` est `Missing`, qui est un attribut très utile pour approfondir l'exploration des données. Par exemple, supposons que le jeu d’éléments A + B est donc très populaire que vous souhaitez rechercher des clients qui ont acheté l’élément A mais pas l’élément B. Vous pouvez le faire à l’aide d’une requête de prédiction et récupérer les transactions avec un élément mais pas dans l’autre et effectuer des analyses supplémentaires sur ces. Pour plus d’informations sur la création de requêtes de prédiction sur les modèles d’association, consultez [Association Model Query Examples](data-mining/association-model-query-examples.md) dans la documentation en ligne de SQL Server  
  
5.  Pour forcer la liste des jeux d’éléments à afficher à nouveau à l’aide de vos nouveaux critères de filtre, vous pouvez sélectionner ou effacer la **afficher le nom long** case à cocher.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Rules"></a> Règles  
 Le **règles** onglet combine les informations sur les jeux d’éléments et leur valeur relative.  
  
 ![Liste des règles créées par un modèle d’association](media/dm13-association-rules.gif "liste des règles créées par un modèle d’association")  
  
 *Probabilité* représente la fraction des cas dans le jeu de données qui contiennent la combinaison d’éléments cible. Probabilité est similaire au concept statistique de *confiance*et vous donne une indication de la probabilité du résultat d’une règle doit se produire. Vous pouvez modifier la valeur de **probabilité minimale** dans ce volet pour filtrer les règles qui sont affichés.  
  
 La valeur de **probabilité minimale** qui apparaît initialement est la valeur de seuil qui a été utilisée par l’algorithme lors de la génération du modèle. Lorsque le modèle est terminé, vous ne pouvez plus réduire cette valeur, mais vous pouvez l'augmenter pour afficher uniquement les éléments dont la probabilité est la plus élevée.  
  
 *Importance* sert à mesurer l’utilité d’une règle. Une règle très courante peut être si omniprésente qu'elle n'a qu'une valeur d'information minime. Plus l'importance est élevée, plus la règle est utile pour prédire le résultat. Dans le [analyse de panier d’achat &#40;outils d’analyse de Table pour Excel&#41; ](shopping-basket-analysis-table-analysistools-for-excel.md) outil, importance peut être combinée avec le prix des articles pour déterminer les paquets qui sont potentiellement plus utiles en termes de ventes.  
  
##### <a name="explore-the-rules-list"></a>Explorer la liste de règles  
  
1.  Essayez de cliquer sur les en-têtes de colonne : **probabilité**, **Importance**, et **règle** — pour voir comment les données changent.  
  
2.  Utilisez le **règle de filtre** option pour entrer des valeurs et de vous concentrer sur les règles ciblées.  
  
     Par exemple, si vous souhaitez voir toutes les règles qui prédisent ce que les clients tendent à acheter avec des gants, tapez « gloves » dans la zone de texte et actualisez le volet.  
  
     L'option **Filtrer le jeu d'éléments** affiche également une liste des filtres que vous avez utilisés précédemment.  
  
3.  Pour forcer la liste des règles pour afficher de nouveau à l’aide des critères de filtre, vous pouvez sélectionner ou effacer la **afficher le nom long** case à cocher.  
  
4.  Utilisez l’option **afficher** pour contrôler la façon dont les noms de règle sont affichées.  
  
5.  Définir la valeur de la **lignes au Maximum** option à 100, puis cliquez sur **copier dans Excel**.  
  
     Notez que le fait de modifier cette valeur n'a aucun effet sur la quantité de données dans le modèle ; cela contrôle simplement le nombre de lignes dans la liste d'affichage. Cette option est utile si vous travaillez sur de très grands modèles.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Dependency"></a> Réseau de dépendances  
 Le **réseau de dépendances** onglet est une carte visuelle des corrélations entre les éléments. Chaque ovale dans le graphique (appelé un *nœud*) représente une paire attribut-valeur, telle que « gilet = Existing » ou « Age = 1-30 ».  Chaque ligne qui relie des ovales (appelée une *edge*) représente un type de corrélation.  
  
 ![Réseau de dépendances pour un modèle d’association](media/dm13-association-dependencynetwork.gif "réseau de dépendances pour un modèle d’association")  
  
##### <a name="explore-the-dependency-network"></a>Explorer le réseau de dépendances  
  
1.  Cliquez sur le **trouver** bouton et utiliser le **rechercher un nœud** boîte de dialogue permettant de taper un élément d’intérêt.  
  
     Par exemple, entrez « gloves » et agrandissez le graphique dans la fenêtre pour voir aisément les résultats.  
  
     Le nœud qui contient les éléments est mis en surbrillance tandis que les flèches qui pointent sur le nœud représentent les règles qui relient les éléments.  
  
     La direction de la flèche indique la direction de la règle. Par exemple, si une personne qui achète des gants a également une probabilité d'acheter un gilet, la flèche partira du nœud « glove » et aboutira au nœud « vest ».  
  
     Pour obtenir des statistiques supplémentaires sur cette règle, vous pouvez cliquer sur le **règles** onglet et recherchez une règle avec la description, « Glove - Existing » -> « Vest – Existing. »)  
  
2.  Cliquez sur le curseur à gauche de la visionneuse et faites-le glisser.  
  
     Le curseur sert à filtrer en fonction de la probabilité des règles. Le déplacement du curseur vers le bas affiche uniquement les règles les plus fortes.  
  
3.  Cliquez sur **copier dans Excel** pour copier un instantané de la fenêtre active dans Excel.  
  
     Vous ne pourrez plus travailler sur le graphique que vous copiez dans Excel ; Si vous avez besoin d’un graphique de réseau interactif, utilisez le [affichant les modèles d’exploration de données dans Visio &#40;Data Mining Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md).  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
## <a name="more-about-association-models"></a>Pour plus d'informations sur les modèles d'association  
 Vous pouvez utiliser la **Parcourir** fonctionnalité pour ouvrir et Explorer un modèle qui a été créé à l’aide de l’algorithme Microsoft Association Rules. Cela comprend les modèles créés à l’aide de la [analyse de panier d’achat &#40;outils d’analyse de Table pour Excel&#41; ](shopping-basket-analysis-table-analysistools-for-excel.md) de l’outil, dans le **Table Analysis Tools** ruban, ou dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Si vous créez un modèle de règles d'association à l'aide de l'outil Analyse du panier d'achat, de nombreuses options avancées sont configurées automatiquement.  
  
 Si vous souhaitez définir des paramètres avancés ou alter probabilité minimale et la prise en charge, utilisez le [Assistant associer &#40;Client d’exploration de données pour Excel&#41; ](associate-wizard-data-mining-client-for-excel.md) Assistant, ou créez votre propre modèle avec le [ajouter le modèle à Structure &#40;des compléments d’exploration de données pour Excel&#41; ](add-model-to-structure-data-mining-add-ins-for-excel.md) option de modélisation.  
  
-   **Jeux d’éléments :** lorsque vous créez le modèle, vous pouvez également contrôler le nombre de jeux d’éléments qui est générés en affectant une valeur au paramètre MINIMUM_PROBABILITY. Ce paramètre est disponible dans la boîte de dialogue Paramètres d’algorithme.  
  
-   **Règles :** le [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme de règles d’Association utilise les valeurs de probabilité pour limiter le nombre de règles qui sont générés. Vous pouvez contrôler le nombre de règles en définissant les paramètres `MINIMUM_PROBABILITY` ou `MINIMUM _IMPORTANCE`.  
  
 Pour plus d’informations sur la configuration des paramètres avancés, consultez [algorithmes d’exploration de données &#40;SQL Server Data Mining Add-ins&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exploration des modèles dans Excel &#40;compléments d’exploration de données SQL Server&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
