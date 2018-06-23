---
title: Valeur cible scénario (outils d’analyse de Table pour Excel) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Table Analysis tools
- scenario analysis
- goal seek scenario
ms.assetid: efe50306-cf7c-46b3-9cc4-e7f0b6968b0c
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ecf3d569cdee1bf2e0ea58e8d582f6b2d3829fca
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140627"
---
# <a name="goal-seek-scenario-table-analysis-tools-for-excel"></a>Scénario Valeur cible (Outils d'analyse de table pour Excel)
  ![Bouton de recherche d’objectif dans Outils d’analyse de Table](media/tat-goalseek.gif "valeur cible de bouton dans les outils d’analyse de Table")  
  
 Le **valeur cible** outil scénario est complémentaire à la [que se passe-t-il si](what-if-scenario-table-analysis-tools-for-excel.md) outil de scénario. Le **simulation** outil vous indique l’impact d’une modification, alors que le **valeur cible** outil vous indique les facteurs sous-jacents qui doivent changer pour atteindre le résultat souhaité.  
  
 Par exemple, supposons que votre objectif est d'augmenter la satisfaction des clients. Vous pouvez utiliser **valeur cible** analyse pour déterminer les facteurs qui serait plus susceptibles d’augmenter la satisfaction des clients et de décider si ces modifications sont rentables.  
  
 Lorsqu'il termine son analyse, l'outil crée deux nouvelles colonnes dans la table de données source. Ces colonnes indiquent la *probabilité* que vous pouvez obtenir le résultat visé, ainsi que la modification recommandée, le cas échéant.  
  
 L'outil peut analyser un jeu de données et élaborer des prédictions pour le jeu entier, ou vous pouvez créer l'analyse puis tester les scénarios un par un.  
  
## <a name="using-the-goal-seek-scenario-tool"></a>Utilisation de l'outil de scénario Valeur cible  
  
1.  Ouvrez un tableau Excel.  
  
2.  Cliquez sur **scénarios**, puis sélectionnez **valeur cible**.  
  
3.  Dans le **analyse de scénario : valeur cible** boîte de dialogue, sélectionnez la colonne qui contient la cible de la valeur dans la liste.  
  
4.  Spécifiez la valeur à atteindre.  
  
     Si la cible de la colonne contient des valeurs numériques continues, vous pouvez également spécifier une hausse ou une baisse souhaitée de la valeur. Par exemple, vous pouvez choisir **Sales** en tant que la colonne et spécifier que la cible est une augmentation de 120 %.  
  
     Ou, vous pouvez spécifier la cible en tant que plage de valeurs, en tapant une limite inférieure et supérieure.  
  
5.  Spécifiez la colonne qui contient les valeurs que vous allez modifier. En d'autres termes, choisissez la colonne qui sera manipulée pour produire le résultat désiré.  
  
6.  Si vous le souhaitez, cliquez sur **choisir les colonnes à utiliser pour l’analyse**, puis sélectionnez les colonnes qui contiennent des informations utiles. Désélectionnez les colonnes qui ne contribueront pas à l'analyse.  
  
    > [!NOTE]  
    >  Ne désélectionnez pas les colonnes que vous utiliserez pour la cible ou la modification. Ces colonnes sont obligatoires.  
  
7.  Indiquez si les prédictions à effectuer doivent porter sur la table entière ou uniquement sur la ligne sélectionnée.  
  
8.  Si vous avez sélectionné le **toute table** option, l’outil ajoute les prédictions à la table source dans les deux nouvelles colonnes.  
  
9. Si vous avez sélectionné l’option **sur cette ligne**, les résultats d’analyse sont affichent dans la boîte de dialogue. La boîte de dialogue reste ouverte afin que vous puissiez continuer à essayer différentes valeurs et cibles.  
  
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
  
 Si vous testez des scénarios de valeur cible un par un, vous pouvez consulter les résultats interactivement. Il est identique à la création d’un *requête de prédiction singleton*.  
  
 L’outil de rapports dans le **résultats** volet de la boîte de dialogue zone si elle a réussi à trouver un scénario qui correspond à l’objectif souhaité. S'il trouve une solution adéquate, il émet une recommandation qui indique le changement requis. Par exemple, le **valeur cible** outil peut vous indiquer que la distance domicile-travail doit être inférieure à 5 miles.  
  
 Résultats de l'exemple :  
  
 **Valeur cible pour désir d’achat a trouvé une solution.**  
  
 **Correspondance la plus proche obtenue en remplaçant 'Distance domicile-travail' à 2 '-5 miles'.**  
  
 Ce résultat repose sur une ligne existante de la table de données. Autrement dit, si les données concernant un client lambda n'ont pas changé mais que sa distance domicile-travail a été ramenée à 3-8 km, le client sera, dans une certaine mesure, plus enclin à acheter une bicyclette.  
  
 Si vous créez des prédictions de recherche d’objectif pour toutes les lignes dans le tableau Excel en spécifiant **toute table**, thetool crée deux nouvelles colonnes dans la table de données d’origine. Dans la première colonne ajoutée à la table figure soit un cercle vert avec une coche pour indiquer que la cible a peut être atteinte, soit un cercle rouge avec un X pour indiquer qu'aucune modification permettant d'atteindre la cible ne peut être effectuée.  
  
 La deuxième colonne contient la modification recommandée.  
  
> [!NOTE]  
>  Le niveau de confiance de la recommandation et son succès sont prédéterminés par l'algorithme et ne peuvent pas être modifiés.  
  
## <a name="related-tools"></a>Outils connexes  
 Le client d'exploration de données pour Excel, un complément séparé qui fournit des fonctionnalités d'exploration de données plus avancées, comprend des Assistants pour créer des modèles d'exploration de données qui prédisent le comportement. Pour plus d’informations, consultez [création d’un modèle d’exploration de données](creating-a-data-mining-model.md).  
  
 Pour plus d’informations sur l’algorithme utilisé par le **valeur cible** scénario outil, consultez la rubrique « Algorithme de régression logistique Microsoft » dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils d’analyse de table pour Excel](table-analysis-tools-for-excel.md)  
  
  