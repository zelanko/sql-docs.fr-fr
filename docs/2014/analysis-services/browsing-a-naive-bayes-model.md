---
title: Exploration d’un modèle Naive Bayes | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9160b48-3beb-439c-9694-f084e1afa625
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 36031bb080ff80c14a4f91bca102bd859df1f539
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038485"
---
# <a name="browsing-a-naive-bayes-model"></a>Navigation dans un modèle Naive Bayes
  Lorsque vous ouvrez un modèle Naïve Bayes avec **Parcourir**, le modèle est affiché dans une visionneuse interactive avec quatre volets différents. Utilisez la visionneuse pour explorer les corrélations et obtenez des informations sur le modèle et les données sous-jacentes.  
  
-   [Réseau de dépendances](#bkmk_DepNet)  
  
-   [Profils d’attribut](#bkmk_AttProf)  
  
-   [Caractéristiques d’attribut](#bkmk_AttChar)  
  
-   [Discrimination d’attribut](#bkmk_AttDisc)  
  
##  <a name="BKMK_Tabs"></a> Explorer le modèle  
 Le but de la visionneuse est de vous aider à explorer les interactions entre les attributs d'entrée et de sortie (entrées et variables dépendantes) qui ont été découvertes par le modèle [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes.  
  
 Si vous souhaitez faire des essais avec la visionneuse Naïve Bayes, utilisez le [classer un Assistant &#40;des compléments d’exploration de données pour Excel&#41; ](classify-wizard-data-mining-add-ins-for-excel.md) Assistant dans le ruban d’exploration de données, cliquez sur le **avancé** option et modifier l’algorithme à utiliser l’algorithme Naïve Bayes  
  
 Pour ces exemples, nous avons utilisé de la Source de données dans l’exemple de classeur et regroupé la colonne **Yearly Income**, en cinq groupes de revenus, à partir de **très faible** à **très élevée**. Le modèle Naïve Bayes a ensuite analysé les facteurs corrélés à chaque catégorie de revenu.  
  
###  <a name="bkmk_DepNet"></a> Réseau de dépendances  
 La première fenêtre que vous allez utiliser est le **réseau de dépendances**. Elle vous présente d'un coup d'œil les entrées qui sont étroitement corrélées avec le résultat sélectionné.  
  
 ![réseau de dépendances dans la visionneuse Naive Bayes](media/dm13-nb.gif "réseau de dépendances dans la visionneuse Naive Bayes")  
  
##### <a name="explore-the-dependency-network"></a>Explorer le réseau de dépendances  
  
1.  Tout d’abord, cliquez sur le résultat cible, **Yearly Income**, ce qui est représenté en tant que nœud dans le graphique.  
  
     Les nœuds en surbrillance qui entourent la variable cible sont ceux qui sont statistiquement corrélés avec ce résultat. Utilisez la légende au bas de la visionneuse pour comprendre la nature de la relation.  
  
2.  Cliquez sur le curseur à gauche de la visionneuse et faites-le glisser vers le bas.  
  
     Ce contrôle filtre les variables indépendantes, en fonction de l'intensité des dépendances. Lorsque vous faites glisser le curseur vers le bas, seuls les liens les plus forts restent dans le graphique.  
  
3.  Après avoir filtré le graphique, cliquez sur le bouton, **copier la vue du graphique**. Sélectionnez ensuite une feuille de calcul dans Excel, puis appuyez sur Ctrl+V.  
  
     Cette option copie la vue sélectionnée, y compris les filtres et la mise en surbrillance.  
  
 [Retour au début](#BKMK_Tabs)  
  
###  <a name="bkmk_AttProf"></a> Profils d’attribut  
 Le **profils d’attribut** windows vous donne une indication visuelle de toutes les autres variables sont associées aux différents résultats.  
  
##### <a name="explore-the-profiles"></a>Explorer les profils  
  
1.  Pour masquer certaines valeurs de manière à pouvoir comparer plus facilement les résultats, cliquez sur l'en-tête de colonne et faites-le glisser sous une autre colonne.  
  
     ![attribut de profils dans la visionneuse Naive Bayes](media/dm13-nb-attprof.gif "dans la visionneuse Naive Bayes, les profils d’attribut")  
  
2.  Cliquez dans une cellule pour afficher la distribution des valeurs dans le **légende d’exploration de données**.  
  
     Les attributs associés à des résultats différents étant affichés visuellement, il est facile de repérer des corrélations intéressantes, telles que le mode de distribution des revenus par région.  
  
3.  Pour obtenir les données sous-jacentes à cette vue, cliquez sur **copier dans Excel**. Un tableau est généré dans une nouvelle feuille de calcul qui affiche les corrélations entre les différents attributs et résultats. Dans ce tableau Excel, vous pouvez masquer ou filtrer facilement les colonnes.  
  
 [Retour au début](#BKMK_Tabs)  
  
###  <a name="bkmk_AttChar"></a> Caractéristiques d’attribut  
 Le **caractéristiques d’attribut** est utile pour un examen détaillé d’une variable de résultat particulier et des facteurs contributifs.  
  
 ![les attributs dans la visionneuse Naive Bayes](media/dm13-nb-viewer.gif "les attributs dans la visionneuse Naive Bayes")  
  
##### <a name="explore-the-attribute-characteristics"></a>Explorer les caractéristiques d'attribut  
  
1.  Cliquez sur **valeur** et sélectionnez un élément dans le **valeur**.  
  
     À mesure que vous sélectionnez un résultat cible, le graphique est actualisé afin d'afficher les facteurs les plus fortement associés au résultat, triés par ordre d'importance.  
  
     Notez que si vous créez un modèle à l’aide de la [analyser les facteurs d’influence clés &#40;outils d’analyse de Table pour Excel&#41; ](analyze-key-influencers-table-analysis-tools-for-excel.md) option, vous pouvez créer des modèles qui ont plus d’un attribut prévisible. Cependant, tous les autres assistants des compléments d'exploration de données vous limitent à un attribut prédictible.  
  
2.  Cliquez sur **copier dans Excel** pour créer une table, dans une feuille de calcul, qui répertorie les scores pour tous les attributs associés au résultat cible sélectionné.  
  
 [Retour au début](#BKMK_Tabs)  
  
###  <a name="bkmk_AttDisc"></a> Discrimination d’attribut  
 Le **Discrimination d’attribut** affichage permet de comparer deux résultats, ou un résultat par rapport à tous les autres.  
  
 ![attribut de discrimination dans la visionneuse Naive Bayes](media/dm13-nb-attdisc.gif "attribut discrimination dans la visionneuse Naive Bayes")  
  
##### <a name="explore-attribute-discrimination"></a>Explorer la discrimination d'attribut  
  
1.  Utilisez les contrôles, **valeur 1** et **valeur 2**, pour sélectionner les résultats que vous souhaitez comparer.  
  
     Par exemple, dans ce modèle a des attributs intéressants dans le groupe de faibles revenus, nous avons choisi le groupe de revenus plus bas dans la première liste déroulante et choisissez **tous les autres États** dans la seconde liste déroulante.  
  
     Les attributs sont triés par ordre d'importance (calculée en fonction des données d'apprentissage). Par conséquent, la profession est le facteur le plus étroitement corrélé avec le revenu (du moins pour ce groupe cible),  
  
     Pour voir les chiffres exacts, cliquez sur la barre de couleur et la vue du **légende d’exploration de données**.  
  
2.  Notez que les revenus les plus bas sont également corrélés à la zone Europe.  
  
     Le modèle Naïve Bayes ne prend pas en charge l'exploration ; toutefois, si vous souhaitez analyser les cas associés à ce groupe de résultats, vous pouvez utiliser une requête. Pour plus d’informations sur les requêtes sur ce type de modèle, consultez [Naive Bayes Model Query Examples](data-mining/naive-bayes-model-query-examples.md).  
  
 [Retour au début](#BKMK_Tabs)  
  
## <a name="see-also"></a>Voir aussi  
 [Exploration des modèles dans Excel &#40;compléments d’exploration de données SQL Server&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  