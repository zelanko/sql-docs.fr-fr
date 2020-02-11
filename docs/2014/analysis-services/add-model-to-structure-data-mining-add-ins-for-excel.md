---
title: Ajouter un modèle à la structure (compléments d’exploration de données pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, creating
ms.assetid: 8efd5bf4-4e6a-4ee8-971a-6efaed5f3b76
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ce68071f27897e181063299e561dfaa7d9f8aab7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66062877"
---
# <a name="add-model-to-structure-data-mining-add-ins-for-excel"></a>Ajouter le modèle à la structure (Compléments d'exploration de données pour Excel)
  ![Bouton Ajouter le modèle à la structure](media/dmc-addmodel.gif "Bouton Ajouter le modèle à la structure")  
  
 Lorsque vous cliquez sur **Ajouter un modèle à la structure**, un Assistant démarre et vous aide à créer un nouveau modèle d’exploration de données à utiliser avec une structure d’exploration de données existante. Cette option est utile, car elle vous permet de comparer les modèles basés sur les mêmes données, ou de créer des modèles personnalisés.  
  
 Si l’instance de Analysis Services ne contient pas déjà les données dont vous avez besoin, utilisez l’Assistant Création d’une [structure d’exploration de données &#40;SQL Server des compléments d’exploration de données&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) pour configurer une structure d’exploration de données. Ou, exécutez un des Assistants de modélisation, puis ajoutez un modèle à la structure créée par l'Assistant.  
  
 Pour créer des modèles avancés à l’aide d’algorithmes non pris en charge par les assistants, créez une structure d’exploration de données, puis ajoutez un modèle à l’aide de l' **éditeur de requêtes avancé d’exploration de données**.  
  
## <a name="add-a-new-model-to-an-existing-structure"></a>Ajouter un nouveau modèle à une structure existante  
  
1.  Sur le ruban **exploration de données** , cliquez sur la flèche sous **avancé**, puis sélectionnez **Ajouter le modèle à la structure**.  
  
2.  Dans la boîte de dialogue **Sélectionner la structure** , choisissez la structure qui contient les données que vous souhaitez utiliser, puis cliquez sur **suivant**.  
  
     **Conseil**: Si vous n’êtes pas sûr de la structure d’exploration de données qui contient les données dont vous avez besoin, utilisez l’Assistant **modèle de document** pour afficher les colonnes et les statistiques de base sur les données.  
  
     Si vous ne trouvez pas de structure d’exploration de données, vérifiez la connexion que vous utilisez actuellement. Vous devrez peut-être établir une connexion à un serveur différent.  
  
3.  Dans la boîte de dialogue **Sélectionner l’algorithme d’exploration** de données, choisissez un algorithme d’exploration de données à utiliser dans le nouveau modèle d’exploration de données.  
  
     Notez que la boîte de dialogue fournit beaucoup plus d’options que celles que vous verrez dans les assistants. Vous pouvez créer un modèle à l'aide de n'importe quel algorithme pris en charge sur votre serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], si vos données sont compatibles.  
  
4.  Nous vous recommandons également de cliquer sur le bouton **paramètres** pour ouvrir la boîte de dialogue **paramètres d’algorithme** et personnaliser les paramètres de l’algorithme. Cette option est la méthode la plus facile pour créer des modèles d'exploration de données personnalisés.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans la boîte de dialogue **Sélectionner les colonnes** , passez en revue la liste des colonnes et, si nécessaire, modifiez l’utilisation des colonnes en l’une des valeurs suivantes :  
  
    -   **Entrée**. Indique que la colonne contient des variables qui peuvent affecter les résultats et doivent être utilisées comme entrées dans le modèle.  
  
    -   **Entrée et prédire**. Indique que les données doivent être utilisées comme entrée, et que vous souhaitez également prédire ces valeurs.  
  
    -   **Prédire uniquement**. Indique que les données ne doivent pas être utilisées en tant qu'entrée du modèle.  
  
    -   **Clé**. Chaque modèle requiert au moins une clé. Selon le type de modèle, vous pouvez également avoir la possibilité d’ajouter des touches spéciales, telles que **SequenceKey** ou **TimeKey**.  
  
    -   **N’utilisez pas**. Indique que les données ne doivent pas être utilisées dans le modèle, même si elles sont présentes dans la structure.  
  
7.  Cliquez sur le bouton Parcourir **(...)** pour ouvrir la boîte de dialogue **définir les indicateurs de modèle de colonne** .  
  
     Prenez quelques instants pour vérifier que l'utilisation de chaque colonne de données est appropriée pour ce modèle. Il s'agit d'une étape importante pour éviter des erreurs lors du traitement du modèle.  
  
     Par exemple, si vous réutilisez une structure créée pour un modèle d'arbre de décision et appliquez l'algorithme Naïve Bayes, les colonnes avec le type de données `Numeric` et le type de contenu `Continuous` devront être placées dans un conteneur ou remplacées par des variables discrètes.  
  
     Si les colonnes de la structure ne sont pas applicables au nouvel algorithme, vous pouvez les ignorer en sélectionnant **ne pas utiliser**.  
  
8.  Dans la boîte de dialogue **définir les indicateurs de modèle de colonne** , examinez ou définissez les indicateurs de modélisation, le cas échéant.  
  
     Les indicateurs de modélisation vous permettent de contrôler la façon dont les valeurs NULL sont gérées, entre autres choses. Pour plus d’informations, consultez [Indicateurs de modélisation &#40;Exploration de données&#41;](data-mining/modeling-flags-data-mining.md).  
  
     Lorsque vous avez terminé, cliquez sur **OK** pour fermer la boîte de dialogue.  
  
9. Dans la boîte de dialogue **Terminer** , tapez un nom et une description pour le nouveau modèle d’exploration de données.  
  
     Selon le type de modèle que vous avez créé, vous pouvez également disposer des options suivantes :  
  
    -   Parcourez le modèle d'exploration de données terminé.  
  
    -   Utilisez l'extraction dans les données source à partir du modèle.  
  
         Pour plus d’informations, consultez [extraction sur les modèles d’exploration de données](data-mining/drillthrough-on-mining-models.md).  
  
10. Cliquez sur **Terminer** pour enregistrer vos modifications. Ce faisant, le modèle est déployé sur le serveur et traité.  
  
### <a name="related-options"></a>Options connexes  
  
|Option|Commentaires|  
|------------|--------------|  
|Boîte **de dialogue Sélectionner une structure ou un modèle**|Choisissez la structure d'exploration de données existante à utiliser en tant que base pour générer un nouveau modèle.  La structure que vous choisissez doit se trouver sur la connexion actuelle. Si ce n’est pas le cas, modifiez les connexions à l’aide de l’outil [se connecter à la source de données &#40;Data Mining client pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md) .|  
|Boîte de dialogue **Sélectionner l’algorithme d’exploration de données**|La liste des algorithmes d'exploration de données varie selon le serveur auquel vous êtes connecté. 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fournit différents algorithmes dans les éditions Standard et Enterprise. L'administrateur peut également avoir ajouté des algorithmes personnalisés.<br /><br /> Si vous ne voyez aucun algorithme, vérifiez que vous êtes connecté à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|  
|**Paramètres d’algorithme** Boîte de dialogue|Dans ces paramètres, vous pouvez personnaliser chaque algorithme en utilisant des paramètres spécifiques à la méthode analytique. Vous pouvez également définir une valeur initiale afin de garantir que les résultats du modèle peuvent être reproduits sur plusieurs passes d'apprentissage.<br /><br /> Pour plus d’informations, consultez [paramètres d’algorithme &#40;SQL Server compléments d’exploration de données&#41;](algorithm-parameters-sql-server-data-mining-add-ins.md).|  
|**Définir les indicateurs de modèle de colonne** Boîte de dialogue|Les indicateurs de modélisation permettent d'améliorer le modèle en spécifiant la façon dont les données manquantes doivent être gérées. Pour plus d’informations, consultez [Indicateurs de modélisation &#40;Exploration de données&#41;](data-mining/modeling-flags-data-mining.md).|  
  
###  <a name="Bkmk_mdlcolumn"></a>Définition de l’utilisation des colonnes  
 Lorsque vous ajoutez un nouveau modèle à une structure d'exploration de données existante, vous devez spécifier la façon dont le modèle utilisera chaque colonne de données dans la structure d'exploration de données. Vous observerez probablement que les options de cet Assistant sont beaucoup plus détaillées que les options de la structure d’exploration de données. Pourquoi ?  
  
 En effet, lorsque vous créez un modèle et une structure en utilisant un Assistant, la plupart des options qui contrôlent la manière dont les données sont exploitées par l'algorithme sont définies automatiquement. Toutefois, lorsque vous ajoutez un modèle à une structure existante, vous devez consulter ces options manuellement, puis spécifier si les données doivent être utilisées pour l'analyse, si le type de données est correct, et ainsi de suite.  
  
 Vous pouvez obtenir des messages d'erreur lors de l'application de nouveaux algorithmes aux données existantes, mais ces messages sont généralement des informations détaillées sur les corrections que vous devez établir pour permettre le traitement du modèle. Voici quelques problèmes classiques de cette situation :  
  
-   Le modèle attend un type de données différent de celui contenu dans la structure.  
  
     Certains algorithmes peuvent uniquement utiliser des nombres, tandis que d'autre peuvent uniquement utiliser du texte. Si vos données sont de type incorrect pour le nouveau modèle, vous devrez peut-être modifier la structure pour permettre le traitement du modèle.  
  
-   La structure d'exploration de données ne contient pas d'attribut prédictible.  
  
     Les modèles de clustering peuvent être créés sans valeur prévisible, mais d'autres modèles exigent généralement que vous spécifiiez une colonne unique pour la prédiction.  
  
-   La composition des données est incompatible avec l’algorithme que vous avez choisi.  
  
     Certains types d'analyses requièrent des données structurées avec soin d'après des règles uniques. Par exemple, les modèles de prévision et les modèles d'association. Vous pouvez ajouter facilement des modèles du même type, éventuellement avec des personnalisations, mais les données ne fonctionnent pas avec d'autres algorithmes.  
  
### <a name="requirements"></a>Spécifications  
 Pour créer des modèles d'exploration de données, vous devez disposer d'une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Pour plus d’informations sur la création ou la modification d’une connexion, consultez [se connecter à des données sources &#40;client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Si la structure d'exploration de données que vous voulez utiliser n'est pas visible, il se peut qu'elle ait été enregistrée dans une autre instance ou une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] différente. Pour plus d’informations sur la façon de passer à une autre connexion d’exploration de données, consultez [se connecter à un serveur d’exploration de données](connect-to-a-data-mining-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d'un modèle d'exploration de données](creating-a-data-mining-model.md)   
