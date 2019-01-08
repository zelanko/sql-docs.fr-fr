---
title: Analyser les facteurs d’influence clés (outils d’analyse de Table pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- key influencers
- factor analysis
ms.assetid: 54d7b4ce-7b79-407a-985c-aa655ad19280
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 672b68a1fda1013fc3ed46f9da1175ec038a8ffe
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52415556"
---
# <a name="analyze-key-influencers-table-analysis-tools-for-excel"></a>Analyser les facteurs d'influence clés (Outils d'analyse de table pour Excel)
  ![Bouton de facteurs d’influence clés analyser dans le ruban](media/tat-aki.gif "bouton analyser les facteurs d’influence clés du ruban")  
  
 Avec le **analyser les facteurs d’influence clés** outil, que vous choisissez une colonne qui contient un résultat cible, et l’algorithme détermine les facteurs qui ont eu la plus grande influence sur le résultat.  
  
 L'outil crée de nouvelles tables de données qui signalent les facteurs associés à chaque résultat et qui affichent de manière graphique la probabilité de la relation. Vous pouvez filtrer les tables en fonction de différents facteurs et résultats pour analyser les résultats de manière plus approfondie.  
  
 Vous pouvez également sélectionner une paire de résultats possibles et les comparer. Par exemple, vous pouvez comparer différents groupes de consommateurs pour déterminer les facteurs possibles de prise de décision.  
  
## <a name="using-the-analyze-key-influencers-tool"></a>Utilisation de l'outil Analyser les facteurs d'influence clés  
  
1.  Ouvrez une table de données Excel.  
  
2.  Dans **outils de tableau**, dans le **analyser** ruban, cliquez sur **analyser les facteurs d’influence clés.**  
  
3.  Sélectionnez la seule colonne qui est la cible de l'analyse.  
  
4.  Si vous le souhaitez, cliquez sur **choisir les colonnes à utiliser pour l’analyse**. Dans le **sélection avancée de colonnes** boîte de dialogue, sélectionnez les colonnes qui sont plus susceptibles de contenir des données pertinentes. Pour améliorer les performances et la précision, désélectionnez les colonnes telles que ID ou Nom qui ne sont pas importantes pour l'analyse des séquences. Cliquez sur **OK** pour fermer la **sélection avancée de colonnes** boîte de dialogue.  
  
5.  Cliquez sur **Exécuter**.  
  
     Le **analyser les facteurs d’influence clés** outil procède à une analyse des données pour déterminer les meilleurs paramètres et définit tous les paramètres automatiquement.  
  
6.  Si aucune séquence n'est détectée, l'Assistant crée une nouvelle feuille de calcul qui contient une description du problème.  
  
7.  Si des séquences sont détectées, l'Assistant crée un rapport sur une nouvelle feuille de calcul qui affiche les séquences. Le rapport est intitulé **facteurs d’influence clés pour \<colonne >**. Vous pouvez personnaliser le rapport comme indiqué dans la procédure suivante.  
  
#### <a name="create-a-custom-report"></a>Créer un rapport personnalisé  
  
1.  Dans le **Discrimination en fonction de facteurs d’influence clés** boîte de dialogue, sélectionnez les deux valeurs que vous souhaitez comparer en les sélectionnant à partir de la **Value 1** et **valeur 2** listes déroulantes . Vous pouvez, par exemple, comparer les acheteurs aux non-acheteurs.  
  
2.  Cliquez sur **ajouter rapport**.  
  
     L'Assistant crée une nouvelle feuille de calcul et ajoute une table pour chaque paire de comparaisons de facteurs clés.  
  
3.  Lorsque vous avez terminé de faire des comparaisons, cliquez sur **fermer**.  
  
## <a name="understanding-the-key-influencers-report"></a>Présentation du rapport des facteurs d'influence clés  
 Une fois que le modèle de données a été créé, le **analyser les facteurs d’influence clés** outil crée des rapports qui vous aident à Explorer et comparer les facteurs d’influence clés.  
  
-   Le rapport à gauche est celui qui est généré par défaut. Il affiche les prédicteurs les plus forts de la colonne de résultats (la variable dépendante).  
  
-   Le rapport à droite est facultatif, créez-le en comparant deux valeurs de résultat spécifiques. Ce rapport compare les acheteurs et les non acheteurs.  
  
-   Notez qu'une nouvelle feuille de calcul est ajoutée pour chaque rapport que vous créez. Déplacez les tables une fois qu'elles sont créées ; nous les avons placées côte à côte pour la comparaison.  
  
 ![DM13](media/dm13-tat-aki-report.gif "DM13")  
  
 **Impact relatif**  
 La barre grisée dans le premier rapport indique l'intensité de l'association de cet attribut avec le résultat.  
  
 La longueur de la barre indique dans quelle mesure (degré de probabilité) le facteur contribuera au résultat ; par conséquent, plus la barre ombrée est longue, plus l'association est forte.  
  
 **Privilégie**  
 Dans le deuxième rapport, les valeurs cible que vous comparez figurent dans deux colonnes, avec les facteurs connexes répertoriés par ordre de confiance décroissant.  
  
-   Le **bleu** barre affiche les attributs qui contribuent au résultat, « Non » (= n’ont pas acheté).  
  
-   Le **rouge** barre affiche les attributs qui contribuent au résultat, « Oui » (= ont acheté un vélo).  
  
 Les couleurs de la barre d'ombrage sont arbitraires. Vous pouvez modifier ces couleurs en définissant les options du mode création de table dans Excel.  
  
 Dans un rapport qui différencie deux valeurs, le deuxième rapport classe les facteurs d'influence clés en fonction de l'impact sur les valeurs cibles.  
  
 Étant donné que tous les graphiques sont basés sur des tableaux Excel, filtrez et triez pour mettre l'accent sur des facteurs ou résultats spécifiques.  
  
## <a name="more-about-the-analyze-key-influencers-tool"></a>En savoir plus sur l'outil Analyser les facteurs d'influence clés  
 Lorsque le **analyser les facteurs d’influence clés** outil analyse vos données, il effectue les opérations suivantes :  
  
-   Il crée une structure de données qui stocke des informations clés à propos de la distribution de vos données.  
  
-   Il crée un modèle d'exploration de données à l'aide de l'algorithme MNB (Microsoft Naïve Bayes).  
  
-   Il crée des prédictions qui corrèle chaque colonne de données avec les résultats spécifiés.  
  
-   Il utilise le score de confiance de chacune des prédictions pour identifier les facteurs qui ont le plus d'influence lors de l'obtention du résultat ciblé.  
  
-   Il crée un rapport décrivant les facteurs d'influence clés, classés par scores de confiance.  
  
### <a name="requirements"></a>Configuration requise  
 Si la colonne cible contient des valeurs numériques continues, l'outil segmente automatiquement les valeurs numériques dans des groupes. Ces regroupements représentent des clusters de cas possédant des caractéristiques similaires. Cependant, les valeurs numériques ne peuvent pas être divisées en groupes conviviaux. Par exemple, le rapport peut contenir un regroupement tel que «\<12.85701", tandis que les utilisateurs de rapports en général, consultez les regroupements qui utilisent des nombres entiers, tels que 10-19, 20-29 et ainsi de suite.  
  
 Si vous voulez regrouper vos données numériques d'une autre manière, vous devez segmenter les données comme vous le souhaitez avant de créer l'analyse. Par exemple, vous pouvez utiliser la [Réétiqueter](relabel-sql-server-data-mining-add-ins.md) outil dans le Client d’exploration de données pour Excel créer une nouvelle étiquette de regroupement dans une colonne distincte et ensuite utiliser cette nouvelle colonne dans l’analyse.  
  
### <a name="related-tools"></a>Outils connexes  
 Le **exploration de données** ruban fournit des outils plus avancés, y compris la possibilité de personnaliser les modèles d’exploration de données  
  
 Si vous enregistrez votre modèle à l’aide de la **analyser les facteurs d’influence clés** outil, vous pouvez utiliser le Client d’exploration de données pour parcourir le modèle et Explorer des relations plus en détail. Pour plus d’informations, consultez [exploration des modèles dans Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md). Vous pouvez également utiliser Microsoft Office Visio pour créer des graphiques et des diagrammes qui présentent les relations sous forme de réseaux de dépendances ou de clusters. Pour plus d’informations, consultez [dépannage des diagrammes d’exploration de données Visio données &#40;SQL Server Data Mining Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md).  
  
> [!NOTE]  
>  Les modèles créés lorsque vous utilisez les outils d'analyse de table sont supprimés lorsque vous fermez votre feuille de calcul ou mettez fin à la connexion avec le serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Par conséquent, vous ne pouvez parcourir les modèles que tant que la connexion reste active. Vous ne pouvez pas restituer les modèles dans Visio si vous désactivez la connexion ou fermez la feuille de calcul.  
  
 Pour plus d’informations sur l’algorithme utilisé par le **analyser les facteurs d’influence clés** , consultez « Algorithme Microsoft Naïve Bayes » dans la documentation en ligne de SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils d’analyse de table pour Excel](table-analysis-tools-for-excel.md)   
 [Création d’un modèle d’exploration de données](creating-a-data-mining-model.md)  
  
  
