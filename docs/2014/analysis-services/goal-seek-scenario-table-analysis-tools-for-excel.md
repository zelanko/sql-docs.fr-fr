---
title: Scénario de la valeur cible (outils d’analyse de table pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- scenario analysis
- goal seek scenario
ms.assetid: efe50306-cf7c-46b3-9cc4-e7f0b6968b0c
author: minewiskan
ms.author: owend
ms.openlocfilehash: f535aa831824b2ab283b2b596d0de49ef0e72515
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544361"
---
# <a name="goal-seek-scenario-table-analysis-tools-for-excel"></a>Scénario Valeur cible (Outils d'analyse de table pour Excel)
  ![Bouton Valeur cible dans les outils d'analyse de table](media/tat-goalseek.gif "Bouton Valeur cible dans les outils d'analyse de table")  
  
 L’outil de scénario de la valeur **cible** est complémentaire à l’outil de scénario de [What If](what-if-scenario-table-analysis-tools-for-excel.md) . L’outil de **simulation** vous indique l’impact d’une modification, tandis que l’outil **objectif cible** vous indique les facteurs sous-jacents qui doivent changer pour obtenir le résultat souhaité.  
  
 Supposons, par exemple, que votre objectif est d’augmenter la satisfaction des clients. Vous pouvez utiliser l’analyse de la recherche de l' **objectif** pour déterminer les facteurs les plus susceptibles d’augmenter la satisfaction des clients et déterminer si ces modifications sont rentables.  
  
 Lorsqu'il termine son analyse, l'outil crée deux nouvelles colonnes dans la table de données source. Ces colonnes indiquent la *probabilité* que le résultat ciblé soit atteint et la modification recommandée, le cas échéant.  
  
 L'outil peut analyser un jeu de données et élaborer des prédictions pour le jeu entier, ou vous pouvez créer l'analyse puis tester les scénarios un par un.  
  
## <a name="using-the-goal-seek-scenario-tool"></a>Utilisation de l'outil de scénario Valeur cible  
  
1.  Ouvrez un tableau Excel.  
  
2.  Cliquez sur **scénarios**, puis sélectionnez valeur **cible**.  
  
3.  Dans la boîte de dialogue **analyse de scénario :** valeur cible, sélectionnez la colonne qui contient la valeur cible dans la liste.  
  
4.  Spécifiez la valeur à atteindre.  
  
     Si la cible de la colonne contient des valeurs numériques continues, vous pouvez également spécifier une hausse ou une baisse souhaitée de la valeur. Par exemple, vous pouvez choisir **Sales** comme colonne et spécifier que la cible est une augmentation de 120%.  
  
     Ou, vous pouvez spécifier la cible en tant que plage de valeurs, en tapant une limite inférieure et supérieure.  
  
5.  Spécifiez la colonne qui contient les valeurs que vous allez modifier. En d'autres termes, choisissez la colonne qui sera manipulée pour produire le résultat désiré.  
  
6.  Si vous le souhaitez, cliquez sur **choisir les colonnes à utiliser pour l’analyse**, puis sélectionnez les colonnes qui contiennent des informations utiles. Désélectionnez les colonnes qui ne contribueront pas à l'analyse.  
  
    > [!NOTE]  
    >  Ne désélectionnez pas les colonnes que vous utiliserez pour la cible ou la modification. Ces colonnes sont obligatoires.  
  
7.  Indiquez si les prédictions à effectuer doivent porter sur la table entière ou uniquement sur la ligne sélectionnée.  
  
8.  Si vous avez sélectionné l’option **table entière** , l’outil ajoute les prédictions à la table source dans deux nouvelles colonnes.  
  
9. Si vous avez sélectionné l’option **sur cette ligne**, les résultats de l’analyse sont générés dans la boîte de dialogue à des fins de vérification. La boîte de dialogue reste ouverte afin que vous puissiez continuer à essayer différentes valeurs et cibles.  
  
### <a name="requirements"></a>Spécifications  
 Cet outil utilise l'algorithme MLR (Microsoft Logistic Regression), qui peut traiter des valeurs numériques ou discrètes.  
  
 Vous pouvez exécuter la prédiction plusieurs fois et sélectionner par la suite d'autres colonnes, mais chaque combinaison de cible et de modification doit être calculée séparément.  
  
 Vous obtiendrez de meilleurs résultats en sélectionnant des colonnes contenant des informations utiles à l'analyse. Cependant, si vous incluez un nombre de colonnes trop restreint, vous aurez peut-être des difficultés à obtenir un résultat.  
  
 Lorsque vous créez des prédictions une à la fois, veillez à sélectionner une ligne qui ne contient pas déjà le résultat souhaité, sinon vous risquez d'obtenir une erreur. En d'autres termes, si l'objectif de la valeur cible est de déterminer les facteurs qui encouragent des achats de vélo, vous devez inclure uniquement les clients qui n'ont pas acheté de vélo.  
  
## <a name="understanding-the-results-of-goal-seek-analysis"></a>Interprétation des résultats d'une analyse de valeur cible  
 Lorsque vous créez un scénario de valeur cible, l'outil effectue trois opérations :  
  
-   il crée une structure d'exploration de données qui stocke des faits clés à propos des données de votre table ;  
  
-   il crée un modèle d'exploration de données de régression logistique basé sur vos données ;  
  
-   il crée une prédiction pour chaque valeur que vous spécifiez.  
  
 Si vous testez des scénarios de valeur cible un par un, vous pouvez consulter les résultats interactivement. Cela revient à créer une requête de *prédiction Singleton*.  
  
 L’outil génère un rapport dans le volet des **résultats** de la boîte de dialogue s’il a réussi à trouver un scénario qui atteint l’objectif souhaité. S'il trouve une solution adéquate, il émet une recommandation qui indique le changement requis. Par exemple, l’outil valeur **cible** peut vous indiquer que la distance de trajet doit être inférieure à 5 kilomètres.  
  
 Résultats de l'exemple :  
  
 **La valeur cible pour Désir d'achat a trouvé une solution.**  
  
 **La correspondance la plus proche obtenue en remplaçant 'distance domicile-travail' par '3-8 km'.**  
  
 Ce résultat repose sur une ligne existante de la table de données. Autrement dit, si les données concernant un client lambda n'ont pas changé mais que sa distance domicile-travail a été ramenée à 3-8 km, le client sera, dans une certaine mesure, plus enclin à acheter une bicyclette.  
  
 Si vous créez des prédictions de recherche d’objectif pour toutes les lignes de la table Excel en spécifiant la **table entière**, theTool crée deux nouvelles colonnes dans la table de données d’origine. Dans la première colonne ajoutée à la table figure soit un cercle vert avec une coche pour indiquer que la cible a peut être atteinte, soit un cercle rouge avec un X pour indiquer qu'aucune modification permettant d'atteindre la cible ne peut être effectuée.  
  
 La deuxième colonne contient la modification recommandée.  
  
> [!NOTE]  
>  Le niveau de confiance de la recommandation et son succès sont prédéterminés par l'algorithme et ne peuvent pas être modifiés.  
  
## <a name="related-tools"></a>Outils connexes  
 Le client d'exploration de données pour Excel, un complément séparé qui fournit des fonctionnalités d'exploration de données plus avancées, comprend des Assistants pour créer des modèles d'exploration de données qui prédisent le comportement. Pour plus d’informations, consultez [création d’un modèle d’exploration de données](creating-a-data-mining-model.md).  
  
 Pour plus d’informations sur l’algorithme utilisé par l’outil de scénario de la valeur **cible** , consultez la rubrique « algorithme de régression logistique Microsoft » dans la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] documentation en ligne de.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils d'analyse de table pour Excel](table-analysis-tools-for-excel.md)  
  
  
