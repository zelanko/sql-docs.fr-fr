---
title: Remplir à partir de l’exemple (outils d’analyse de table pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- fill from example
ms.assetid: dac57d8f-1c65-4878-8ea0-9c680df5e4fb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d1e09e439469f23412c84ea7bab65c0aa748f286
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66081319"
---
# <a name="fill-from-example-table-analysis-tools-for-excel"></a>Remplir à partir de l'exemple (Outils d'analyse de table pour Excel)
  ![Bouton Remplir à partir de l'exemple dans les Outils d'analyse de table](media/tat-fillex.gif "Bouton Remplir à partir de l'exemple dans les Outils d'analyse de table")  
  
 L’outil **remplir à partir de l’exemple** vous permet de créer de nouvelles colonnes de données en fonction de valeurs existantes.  
  
 Par exemple, supposons que vos données contiennent une colonne **montant d’achat** , une colonne **quantité de commandes** et une colonne **client premier** basée sur une formule utilisant les autres colonnes. Si la colonne **client premier** contient de nombreuses lignes vides, vous pouvez utiliser les colonnes **montant des achats** et quantité de **commandes** comme entrées pour déduire les valeurs manquantes. L'outil analyse les modèles existants dans les données conjointement avec les exemples entrés, et prédit quelle catégorie affecter à chaque client.  
  
 Si vous n'êtes pas satisfait des résultats, vous pouvez les affiner en fournissant des exemples supplémentaires.  
  
## <a name="using-the-fill-from-example-tool"></a>Utilisation de l'outil Remplir à partir de l'exemple  
  
1.  Dans le ruban **analyser** , cliquez sur **remplir à partir de l’exemple**.  
  
2.  L'outil choisit automatiquement une colonne à remplir en fonction de l'analyse des données et vous pouvez accepter ou ignorer cette suggestion.  
  
3.  Créez une colonne pour les nouvelles données, puis tapez des exemples de données que vous souhaitez prédire. Veillez à ce qu'il existe au moins un exemple pour chaque valeur à prédire. Si vous remplissez une colonne existante de données, sélectionnez celle dans laquelle il manque des valeurs.  
  
4.  Si vous le souhaitez, cliquez sur **choisir les colonnes à utiliser dans l’analyse**. Dans la boîte de dialogue **Sélection avancée des colonnes** , spécifiez les colonnes qui sont les plus susceptibles d’être utiles lors du remplissage des données manquantes.  
  
     Par exemple, si vous savez par expérience qu'il existe un lien de cause à effet entre une colonne déterminée et une autre dans laquelle il manque des valeurs, vous pouvez désélectionner les autres colonnes pour obtenir de meilleurs résultats.  
  
     Cliquez sur **OK**.  
  
5.  Cliquez sur **Exécuter**.  
  
     Une fois l’analyse terminée, l’outil crée une nouvelle feuille de calcul **patterns** qui contient les résultats de l’analyse. Le rapport répertorie les règles, ou facteurs d'influence clés, qui ont été trouvés, et montre la probabilité de chaque règle.  
  
     L'outil ajoute également automatiquement une colonne contenant les nouvelles valeurs à la table de données d'origine. Vous pouvez examiner les valeurs et les comparer à celles d'origine.  
  
### <a name="requirements"></a>Conditions requises  
 Vous ne pouvez utiliser que des données de colonnes. Si la série que vous souhaitez remplir est stockée dans une ligne, vous pouvez utiliser la fonction de collage, transposition d'Excel pour mettre les données sous forme de colonne.  
  
## <a name="understanding-the-pattern-report"></a>Présentation du rapport de séquence  
 Lorsque vous exécutez l’outil **remplir à partir de l’exemple** , un rapport est créé et fournit des informations supplémentaires sur les modèles qui ont été détectés. Ces séquences servent à extrapoler les nouvelles valeurs de données.  
  
 Le rapport de séquence présente les facteurs d'influence clés de chaque valeur qui a été prédite. Chaque facteur d'influence (ou règle) est décrit comme étant la combinaison d'une colonne, de la valeur de cette colonne et de l'impact relatif de la règle sur la prédiction.  
  
 Par exemple, si vous essayez de remplir une feuille de calcul indiquant la distance de transport des marchandises commandées, vous pouvez vous attendre en toute logique à ce que la destination ait un fort impact sur cette valeur de distance. Dans ce cas, la requête peut contenir la ligne suivante :  
  
|Colonne|Value|Privilèges|Impact relatif|  
|------------|-----------|------------|---------------------|  
|StateProvinceCode|AB|>500 kilomètres|80 %|  
  
 Cela signifie que la valeur AB dans la colonne **StateProvinceCode** prédit fortement une distance d’expédition de >500 kilomètres.  
  
 En règle générale, les prédictions reposent sur des séquences bien plus complexes que celles présentées dans cet exemple, et le rapport peut contenir de nombreuses lignes de règles pour chaque prédiction. L'effet de toutes les règles se combine pour dériver la valeur prédite.  
  
> [!NOTE]  
>  L' **impact relatif** est représenté sous la forme d’une barre ombrée. Plus la barre est longue, plus grande est la probabilité que cette règle est prédictive de la valeur de remplissage.  
  
 L’outil ajoute également une nouvelle colonne à la table de données d’origine \<, nom de la colonne nommée> étendu.  
  
 Si la colonne de données d'origine contenait une valeur, celle-ci est copiée dans la nouvelle colonne. En revanche, si la colonne d'origine contenait une cellule vide, la nouvelle colonne contient la valeur qui a été prédite par l'Assistant.  
  
## <a name="related-tools-and-information"></a>Outils et informations connexes  
 Vous pouvez également utiliser l’Assistant [Explorer les données](explore-data-sql-server-data-mining-add-ins.md) , disponible dans le client d’exploration de données pour Excel, pour examiner la distribution des valeurs dans une colonne Excel. Pour plus d’informations, consultez [exploration et nettoyage des données](exploring-and-cleaning-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Outils d'analyse de table pour Excel](table-analysis-tools-for-excel.md)  
  
  
