---
title: Remplir à partir de l’exemple (outils d’analyse de Table pour Excel) | Microsoft Docs
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66081319"
---
# <a name="fill-from-example-table-analysis-tools-for-excel"></a>Remplir à partir de l'exemple (Outils d'analyse de table pour Excel)
  ![Bouton remplir à partir de l’exemple dans la Table Analysis Tools](media/tat-fillex.gif "bouton remplir à partir de l’exemple dans les outils d’analyse de Table")  
  
 Le **remplir à partir de l’exemple** outil vous permet de créer de nouvelles colonnes de données selon les valeurs existantes.  
  
 Par exemple, supposons que vos données contiennent un **montant** colonne, une **quantité de commandes** colonne et un **client Premier** colonne qui est basée sur une formule à l’aide la autres colonnes. Si le **client Premier** colonne contient de nombreuses lignes vides, vous pouvez utiliser la **montant** et **quantité de commandes** colonnes comme entrées, pour déduire les valeurs manquantes. L'outil analyse les modèles existants dans les données conjointement avec les exemples entrés, et prédit quelle catégorie affecter à chaque client.  
  
 Si vous n'êtes pas satisfait des résultats, vous pouvez les affiner en fournissant des exemples supplémentaires.  
  
## <a name="using-the-fill-from-example-tool"></a>Utilisation de l'outil Remplir à partir de l'exemple  
  
1.  Dans le **analyser** ruban, cliquez sur **remplir à partir de l’exemple**.  
  
2.  L'outil choisit automatiquement une colonne à remplir en fonction de l'analyse des données et vous pouvez accepter ou ignorer cette suggestion.  
  
3.  Créez une colonne pour les nouvelles données, puis tapez des exemples de données que vous souhaitez prédire. Veillez à ce qu'il existe au moins un exemple pour chaque valeur à prédire. Si vous remplissez une colonne existante de données, sélectionnez celle dans laquelle il manque des valeurs.  
  
4.  Si vous le souhaitez, cliquez sur **choisir les colonnes à utiliser dans l’analyse**. Dans le **sélection avancée de colonnes** boîte de dialogue, spécifiez les colonnes qui sont susceptibles d’être utiles lors du remplissage des données manquantes.  
  
     Par exemple, si vous savez par expérience qu'il existe un lien de cause à effet entre une colonne déterminée et une autre dans laquelle il manque des valeurs, vous pouvez désélectionner les autres colonnes pour obtenir de meilleurs résultats.  
  
     Cliquez sur **OK**.  
  
5.  Cliquez sur **Exécuter**.  
  
     Lors de l’analyse est terminée, l’outil crée un nouveau **modèles** feuille de calcul qui contient les résultats d’analyse. Le rapport répertorie les règles, ou facteurs d'influence clés, qui ont été trouvés, et montre la probabilité de chaque règle.  
  
     L'outil ajoute également automatiquement une colonne contenant les nouvelles valeurs à la table de données d'origine. Vous pouvez examiner les valeurs et les comparer à celles d'origine.  
  
### <a name="requirements"></a>Configuration requise  
 Vous ne pouvez utiliser que des données de colonnes. Si la série que vous souhaitez remplir est stockée dans une ligne, vous pouvez utiliser la fonction de collage, transposition d'Excel pour mettre les données sous forme de colonne.  
  
## <a name="understanding-the-pattern-report"></a>Présentation du rapport de séquence  
 Lorsque vous exécutez le **remplir à partir de l’exemple** , outil de création d’un rapport qui fournit plus d’informations sur les modèles qui ont été détectées. Ces séquences servent à extrapoler les nouvelles valeurs de données.  
  
 Le rapport de séquence présente les facteurs d'influence clés de chaque valeur qui a été prédite. Chaque facteur d'influence (ou règle) est décrit comme étant la combinaison d'une colonne, de la valeur de cette colonne et de l'impact relatif de la règle sur la prédiction.  
  
 Par exemple, si vous essayez de remplir une feuille de calcul indiquant la distance de transport des marchandises commandées, vous pouvez vous attendre en toute logique à ce que la destination ait un fort impact sur cette valeur de distance. Dans ce cas, la requête peut contenir la ligne suivante :  
  
|colonne|Value|Privilèges|Impact relatif|  
|------------|-----------|------------|---------------------|  
|StateProvinceCode|AB|> 500 kilomètres|80 %|  
  
 Cela signifie que la valeur AB figurant dans le **StateProvinceCode** colonne prédit une distance de transport > 500 kilomètres.  
  
 En règle générale, les prédictions reposent sur des séquences bien plus complexes que celles présentées dans cet exemple, et le rapport peut contenir de nombreuses lignes de règles pour chaque prédiction. L'effet de toutes les règles se combine pour dériver la valeur prédite.  
  
> [!NOTE]  
>  **Impact relatif** est affichée comme une barre grisée. Plus la barre est longue, plus grande est la probabilité que cette règle est prédictive de la valeur de remplissage.  
  
 L’outil ajoute également une nouvelle colonne à la table de données d’origine, nommée \<nom de colonne > étendu.  
  
 Si la colonne de données d'origine contenait une valeur, celle-ci est copiée dans la nouvelle colonne. En revanche, si la colonne d'origine contenait une cellule vide, la nouvelle colonne contient la valeur qui a été prédite par l'Assistant.  
  
## <a name="related-tools-and-information"></a>Outils et informations connexes  
 Vous pouvez également utiliser le [Explorer les données](explore-data-sql-server-data-mining-add-ins.md) Assistant, disponible dans le Client d’exploration de données pour Excel, pour examiner la distribution des valeurs dans une colonne Excel. Pour plus d’informations, consultez [exploration et nettoyage des données](exploring-and-cleaning-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Outils d’analyse de table pour Excel](table-analysis-tools-for-excel.md)  
  
  
