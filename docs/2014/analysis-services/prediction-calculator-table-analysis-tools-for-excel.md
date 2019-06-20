---
title: Calcul de prédiction (outils d’analyse de Table pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining model, regression
- Table Analysis tools
- scorecard
- logistic regression
- prediction calculator
ms.assetid: 8bb8c318-e85f-4fd6-b32b-4cdfb13ca1b5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e57aee7142da5c256a213ddd2eb0390a0f3b042a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66070858"
---
# <a name="prediction-calculator-table-analysis-tools-for-excel"></a>Calcul de prédiction (Outils d'analyse de table pour Excel)
  ![Outil calcul de prédiction](media/tat-predcal.gif "outil calcul de prédiction")  
  
 Le **calcul de prédiction** outil vous permet de créer une carte de performance qui peut être utilisé pour analyser les nouvelles données et évaluer des options ou risque. Par exemple, si vous avez des données historiques et socioéconomiques sur les clients, le **calcul de prédiction** outil peut vous aider à avec deux tâches principales :  
  
-   Génération d'une analyse sous-jacente de données socioéconomiques, de comportement d'achat et différents autres facteurs.  
  
-   Création d'un tableau de bord fonctionnel qui vous aide à évaluer les membres et à faire des recommandations pour de nouveaux produits ou des offres de service.  
  
 L'Assistant crée également une feuille de calcul qui stocke tous les calculs sous-jacents, afin que vous puissiez interagir avec le modèle et voir comment des valeurs d'entrée différentes affectent le score final.  
  
 Le cas échéant, l'Assistant peut également créer une version imprimée de la feuille de calcul que vous pouvez utiliser hors connexion pour l'établissement du score. Vous ne pouvez pas interagir avec le modèle comme vous le faites avec le classeur Excel en ligne, mais la version imprimée fournit tous les calculs dont vous avez besoin pour entrer des valeurs et calculer un dernier score.  
  
## <a name="using-the-prediction-calculator-tool"></a>Utilisation de l'outil de calcul de prédiction  
  
1.  Ouvrez une table Excel contenant les données à analyser.  
  
2.  Cliquez sur **calcul de prédiction** sur le **analyser** onglet.  
  
3.  Dans le **calcul de prédiction** boîte de dialogue, pour la cible, choisissez la colonne que vous souhaitez prédire, par exemple le comportement d’achat.  
  
4.  Spécifiez la valeur ciblée : Si la valeur est numérique, utilisez l’option **dans la plage**, puis tapez les valeurs minimales et maximales de la plage désirée. Si la valeur est discrète, sélectionnez le **exactement** option, puis sélectionnez la valeur dans la liste déroulante.  
  
5.  Cliquez sur **choisir les colonnes à utiliser pour l’analyse**.  
  
6.  Dans le **sélection avancée de la colonne** boîte de dialogue, sélectionnez les colonnes qui contiennent des informations utiles. Retirez les colonnes sans pertinence pour l'analyse. Cliquez sur **OK**.  
  
     Pour éviter de fausser les résultats, vous devez également supprimer les colonnes qui contiennent des informations en double. Par exemple, si vous avez une colonne Revenu qui contient des données numériques, et une colonne Revenu de groupe qui contient les étiquettes Haut, Moyen et Bas, vous ne devez pas inclure les deux colonnes dans le même modèle. Créez plutôt un modèle séparé pour chaque colonne.  
  
7.  Dans le **Options de sortie** section, sélectionnez **calcul opérationnel** pour créer l’analyse et le tableau de bord dans un classeur Excel. Sélectionnez **calculatrice de prêt à l’impression** pour créer l’analyse et également générer un rapport qui peut être imprimé et utilisé pour calculer les scores manuellement.  
  
8.  Cliquez sur **Exécuter**.  
  
     L'outil crée de nouvelles feuilles de calcul qui contiennent les rapports et les tableaux de bord.  
  
### <a name="requirements"></a>Configuration requise  
 Le **calcul de prédiction** outil utilise l’algorithme Microsoft Logistic Regression, qui peut fonctionner avec des valeurs discrètes, ainsi que des données numériques continues et discrétisées.  
  
## <a name="understanding-the-scoring-reports"></a>Présentation des rapports de score  
 Si vous sélectionnez les deux options de sortie, le Calcul de prédiction crée les trois nouvelles feuilles de calcul suivantes dans le classeur actuel :  
  
-   Un **rapport de prédiction**qui contient les résultats d’analyse, complets avec des tableaux interactifs et graphiques qui vous aident à faire des essais avec les interactions et les bénéfices.  
  
-   Interactif **calcul de prédiction** qui vous permet de créer des scores.  
  
-   Un **calcul imprimable** des instructions et des coefficients à utiliser dans les scores.  
  
-   Cette section décrit les informations dans chaque rapport et explique comment utiliser les diverses options de rapport.  
  
### <a name="prediction-report-with-graphs"></a>Rapport de prédiction avec graphiques  
 Le premier rapport de prédiction est intitulé **rapport du calcul de prédiction pour la \<état cible > de \<attribut cible >**. Il contient une table de facteurs dérivée de l'analyse, avec les outils destinés à aider à évaluer l'impact financier d'une analyse particulière.  
  
#### <a name="table-for-specifying-costs-and-profits"></a>Table pour spécifier coûts et bénéfices  
 Le premier outil dans ce rapport, en haut et à gauche du rapport, est une table où vous pouvez spécifier les coûts et bénéfices associés à la prédiction correcte et incorrecte d'une valeur.  Ces coûts et bénéfices sont nécessaires pour calculer le seuil de score optimum pour le calcul.  
  
|Élément|Description et exemple|  
|----------|-----------------------------|  
|Coût des faux positifs|Le coût d'assumer que le modèle a prédit un résultat positif correctement alors que la prédiction est en fait fausse.<br /><br /> Par exemple, le modèle prédit qu'un client achètera quelque chose, et sur la base de cela vous imaginez une campagne visant ce client. Vous pouvez entrer ici le coût de la démarche ciblant le client.|  
|Coût des faux négatifs|Le coût d'assumer que le modèle a prédit un résultat négatif correctement alors que la prédiction est en fait fausse.<br /><br /> Par exemple, le modèle peut prédire qu'il est peu probable que les vieux clients achètent un vélo, mais vous découvrez que le modèle a été faussé et que, par conséquent, vous avez raté l'occasion de viser les vieux clients. Vous pouvez assigner ici un coût d'opportunité manquée.|  
|Bénéfices des vrais positifs|Prédisez correctement un résultat positif et tirez-en parti. Par exemple, si vous ciblez les bons clients et atteignez les résultats dans une vente, vous entreriez ici le bénéfice par client.|  
|Bénéfices des vrais négatifs|Prédisez correctement un résultat négatif et tirez-en parti.<br /><br /> Par exemple, si vous pouvez identifier correctement des clients qui ne doivent pas être ciblés, vous pouvez entrer ici un budget X pour la publicité par client.|  
  
#### <a name="chart-for-viewing-maximum-profit"></a>Établir un graphique pour consulter le profit maximal  
 À mesure que vous entrez des valeurs dans le tableau, les graphiques connexes se mettent à jour automatiquement pour vous montrer le meilleur point pour maximiser le profit compte tenu du modèle actuel. Le diagramme linéaire à droite de cette table affiche le profit pour plusieurs seuils de score. Le bénéfice est estimé à l'aide des chiffres de bénéfice et de coût que vous entrez dans la table, selon les prédictions et probabilités tirées du modèle.  
  
 Par exemple, if, dans la table de gauche supérieure, la cellule pour **seuil suggéré pour augmenter les bénéfices** affiche la valeur 500, le graphique sur le côté droit affichera 500 comme le point le plus élevé sur le graphique linéaire. Cette valeur 500 signifie que pour augmenter les bénéfices, vous devez utiliser les 500 recommandations supérieures du modèle d'exploration de données, classées par probabilité.  
  
#### <a name="table-listing-scores-for-each-attribute-and-value"></a>Table qui répertorie les scores pour chaque attribut et valeur  
 La table en bas et à gauche du rapport montre une décomposition détaillée des valeurs détectées, et comment chaque valeur affecte le résultat. Vous ne pouvez pas modifier les valeurs de cette table ; elles sont affichées pour vous aider à comprendre la prédiction.  
  
 Par exemple, la table suivante montre un exemple des résultats lorsque le résultat cible équivaut à un client qui achète un vélo. La table répertorie chaque colonne d'entrée utilisée dans le modèle, que l'entrée ait affecté le modèle ou non. La table répertorie également les valeurs discrètes et les valeurs discrétisées si la colonne d'entrée contenait des données numériques continues.  
  
 Les valeurs dans le **Impact relatif** colonne sont des probabilités, représentées sous forme de pourcentages. La cellule est ombrée pour représenter visuellement l'impact de cette valeur sur les résultats.  
  
|Attribute|Value|Impact relatif|  
|---------------|-----------|---------------------|  
|Marital Status|Married|0|  
|Marital Status|Unique|71|  
|Gender|Female|13|  
|Gender|Male|0|  
  
 Vous pouvez interpréter ces facteurs comme suit :  
  
-   Le fait d'être marié n'a aucune incidence sur la probabilité du client d'acheter un vélo.  
  
-   Toutefois, être célibataire est un indicateur fort (70 pour cent) concernant la probabilité d'achat d'un vélo par le client.  
  
-   Le sexe du client n'a qu'un effet marginal (13 pour cent) sur le comportement d'achat de vélo prédit si le client est une femme, et n'a aucun effet sur le comportement d'achat de vélo prédit si le client est un homme.  
  
#### <a name="chart-of-cumulative-misclassification-cost"></a>Graphique de coût de classification incorrecte cumulé  
 Le graphique en aires en bas et à droite du rapport affiche le coût de classification incorrecte cumulé pour différents seuils de scores. Ce graphique utilise également les chiffres de coût et de bénéfice que vous entrez pour les faux positifs, les vrais positifs, les faux négatifs et les vrais négatifs.  
  
 Contrairement au graphique en haut et à droite du rapport, qui est axé sur l'augmentation des bénéfices, ce graphique incorpore le coût d'élaboration d'une fausse prédiction. Ce graphique est particulièrement utile dans les scénarios tels que la prévention, où le coût de prise d'une mauvaise décision incorrecte pèse considérablement plus lourd que le coût d'une estimation correcte.  
  
 Par exemple, bien que le premier graphique suggère que le fait de cibler les 500 premiers clients prédits par le modèle est la meilleur moyen de maximiser les bénéfices, vous pouvez décider après avoir examiné ce deuxième graphique que le risque de mal cibler les clients est trop grand et préférer limiter la campagne de marketing aux 400 premiers clients.  
  
### <a name="interactive-prediction-calculator"></a>Calcul de prédiction interactif  
 La deuxième feuille de calcul créée par l’outil de calcul de prédiction est intitulée **calcul de prédiction pour la \<état cible > de \<attribut cible >**. Il s'agit d'une feuille de calcul interactive que vous pouvez utiliser pour calculer des scores individuels. Dans la mesure où cette feuille de calcul utilise des séquences et des statistiques stockées dans le modèle, vous pouvez expérimenter avec différentes valeurs et voir comment elles affectent le score prédit. Ce rapport comporte également deux sections : l'une est interactive, l'autre sert de référence.  
  
#### <a name="first-table"></a>Première table  
 Vous pouvez sélectionner ou tapez une nouvelle valeur dans le **valeur** colonne de la table pour voir comment la modification de la valeur affecte le score.  
  
 Par exemple, si le rapport contient les valeurs suivantes, vous pouvez ramener la valeur de Voitures à 1 puis à 0 pour voir comment cela affecte le comportement d'achat du client. Lorsque vous modifiez la valeur de **voitures** à 0, la prédiction en bas passe à TRUE.  
  
|Attribute|Value|Impact relatif|  
|---------------|-----------|---------------------|  
|Marital Status|Married|0|  
|Gender|Male|0|  
|Revenu|39050 - 71062|117|  
|Children|0|157|  
|Education|Célibataires|22|  
|Occupation|Skilled Manual|33|  
|Propriétaire de base|Oui|8|  
|Voitures|2|50|  
|Commute Distance|0-1,5 km|99|  
|Région|North America|0|  
|Age|37 - 46|5|  
|Total||491|  
|Prédiction pour « oui »||FALSE|  
  
 Lorsque vous tapez dans la nouvelle valeur, le score affiché dans la cellule, prédiction pour Oui, passe à TRUE et le **Impact relatif** scores pour les différents attributs sont également mises à jour.  
  
> [!NOTE]  
>  Même si vous vous modifiez une seule valeur, telle que le nombre de voitures, les valeurs et impacts d'autres attributs peuvent changer lorsque vous agissez ainsi. Cela s'explique par le fait que les modèles d'exploration de données trouvent souvent des relations complexes entre les données, et la modification de toute variable peut avoir des effets imprévus. Pour cette raison, nous vous recommandons d'utiliser le calcul de prédiction interactif pour expérimenter avec différentes valeurs, ou de parcourir le modèle d'exploration de données pour mieux comprendre les interactions. Pour plus d’informations, consultez [parcourir les modèles](prediction-calculator-table-analysis-tools-for-excel.md).  
  
#### <a name="score-breakdown"></a>Répartition des scores  
 Cette table montre les scores individuels pour chaque état possible des colonnes d'entrée, et l'impact relatif de chaque score sur les résultats. Cette table est statique ; il est fourni à des fins de référence uniquement.  
  
### <a name="printable-prediction-calculator"></a>Calcul de prédiction imprimable  
 La troisième feuille de calcul créée par l’outil de calcul de prédiction est intitulée **calculatrice PrintablePrediction pour le \<état cible > de \<attribut cible >**. Ce tableau de bord est destiné à être imprimé afin que vous puissiez calculer des scores manuellement lorsque vous n'êtes pas devant votre ordinateur.  
  
##### <a name="to-print-and-use-the-scoring-report-generated-by-the-prediction-calculator"></a>Imprimer et utiliser le rapport de scores généré par le Calcul de prédiction  
  
1.  Cliquez sur l’onglet intitulé **calcul de prédiction imprimable pour \<attribut >**.  
  
2.  Dans le menu fichier Excel, sélectionnez **Aperçu avant impression**.  
  
3.  Modifiez l'orientation de la page, les marges et d'autres paramètres de mise en page jusqu'à ce que la table soit disposée sur la page de la façon dont vous le souhaitez.  
  
     Ce tableau de bord n'est pas dynamique et n'est connecté en aucune façon au modèle ; vous pouvez donc déplacer des colonnes ou des lignes pour améliorer la mise en forme sans affecter les données sous-jacentes.  
  
4.  Imprimez le tableau de bord.  
  
5.  Pour chaque attribut, choisissez une seule valeur. Pour la valeur vous choisissez, placez une coche dans la zone et écrire le numéro correspondant le **Score** colonne.  
  
6.  Remplissez autant d'attributs que possible afin de garantir l'exactitude.  
  
7.  Calculer la somme des scores pour chaque attribut et entrez ce numéro dans le **Total** ligne.  
  
8.  Convertissez le score pour un résultat prédit à l’aide des critères imprimés sur la feuille immédiatement après le **Total** ligne.  
  
## <a name="related-tools"></a>Outils connexes  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fournit l'algorithme MLR (Microsoft Logistic Regression) pour une utilisation dans ce type d'analyse. Si vous êtes déjà familiarisé avec la régression logistique, vous pouvez facilement créer des modèles de régression logistique à l’aide de la **avancé** option du Client d’exploration de données pour Excel. Pour plus d’informations, consultez [avancés de modélisation &#40;des compléments d’exploration de données pour Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md). Pour plus d’informations sur les options et paramètres pour les modèles de régression logistique, consultez la rubrique « Algorithme de régression logistique Microsoft » dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils d’analyse de table pour Excel](table-analysis-tools-for-excel.md)  
  
  
