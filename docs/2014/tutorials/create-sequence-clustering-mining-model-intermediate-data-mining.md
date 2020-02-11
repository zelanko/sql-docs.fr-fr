---
title: Création d’une structure de modèle d’exploration de données Sequence Clustering (Didacticiel intermédiaire sur l’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9339227-6c2e-4c4b-8be2-8c1960bc4a8d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b7f4f543952fd86cf6c3c66f9f4b2c51019b1869
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63273480"
---
# <a name="creating-a-sequence-clustering-mining-model-structure-intermediate-data-mining-tutorial"></a>Création d'une structure de modèle d'exploration de données Sequence Clustering (Didacticiel intermédiaire sur l'exploration de données)
  La première étape pour créer un modèle d'exploration de données Sequence Clustering est d'utiliser l'Assistant Exploration de données pour créer une nouvelle structure d'exploration de données et un modèle d'exploration de données selon l'algorithme MSC ([!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering).  
  
 Vous utiliserez la même vue de source de données que vous avez utilisée pour l'analyse du panier d'achat, mais vous ajouterez une colonne qui contient l'identificateur `sequence`. Dans ce scénario, la séquence signifie l'ordre dans lequel le client a ajouté des éléments au panier.  
  
 Vous ajouterez également des colonnes utilisées dans l'un des modèles pour regrouper des clients par démographie.  
  
### <a name="to-create-a-sequence-clustering-structure-and-model"></a>Pour créer un modèle et une structure Sequence Clustering  
  
1.  Dans Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], cliquez avec le bouton droit sur **structures d’exploration de données** et sélectionnez **nouvelle structure d’exploration de données**.  
  
2.  Dans la page **Assistant Exploration de données** , cliquez sur **Suivant**.  
  
3.  Sur la page **Sélectionner la méthode de définition** , vérifiez que **à partir de la base de données relationnelle ou de l’entrepôt de données existant** est sélectionné, puis cliquez sur **suivant**.  
  
4.  Dans la page **créer la structure d’exploration de données** , vérifiez que l’option **créer une structure d’exploration de données avec un modèle d’exploration** de données est sélectionnée. Ensuite, cliquez sur la liste déroulante de l’option, **quelle technique d’exploration de données voulez-vous utiliser ?**, puis sélectionnez **Microsoft Sequence Clustering**. Cliquez sur **Suivant**.  
  
     La page **Sélectionner une vue de source de données** s’affiche. Sous **vues de sources de données disponibles**, sélectionnez `Orders`.  
  
     Orders est la même vue de source de données que vous avez utilisée pour le scénario d'analyse de panier. Si vous n’avez pas créé cette vue de source de données, consultez [Ajout d’une vue de source de données avec des tables imbriquées &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md).  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans la **page spécifier les types des tables** , activez la case à cocher **cas** en regard de la table **vAssocSeqOrders** , puis activez la case à cocher **imbriquée** en regard de la table **vAssocSeqLineItems** . Cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  Si une erreur se produit lorsque vous activez les cases à cocher **cas** ou **imbriquées** , il se peut que la jointure dans la vue de source de données ne soit pas correcte. La table imbriquée, **vAssocSeqLineItems**, doit être connectée à la table de cas, **vAssocSeqOrders,** par une jointure plusieurs-à-un. Vous pouvez modifier la relation en cliquant avec le bouton droit sur la ligne de jointure et en inversant la direction de la jointure. Pour plus d’informations, consultez [boîte de dialogue créer ou modifier une relation &#40;Analysis Services-&#41;de données multidimensionnelles ](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md).  
  
7.  Dans la page **spécifier les données d’apprentissage** , choisissez les colonnes à utiliser dans le modèle en activant une case à cocher comme suit :  
  
    -   **IncomeGroup** Activez la case à cocher **entrée** .  
  
         Cette colonne contient des informations pertinentes sur les clients que vous pouvez utiliser pour le clustering. Vous les utiliserez dans le premier modèle puis les ignorerez dans le deuxième modèle.  
  
    -   **OrderNumber** Activez la `Key` case à cocher.  
  
         Ce champ sera utilisé comme l'identificateur de la table de cas, ou `Key`. En général, vous ne devez jamais utiliser le champ clé de la table de cas comme entrée, parce que la clé contient des valeurs uniques qui ne sont pas utiles pour le clustering.  
  
    -   **Région** Activez la case à cocher **entrée** .  
  
         Cette colonne contient des informations pertinentes sur les clients que vous pouvez utiliser pour le clustering. Vous les utiliserez dans le premier modèle puis les ignorerez dans le deuxième modèle.  
  
    -   **LineNumber** Activez les `Key` cases à cocher et **d’entrée** .  
  
         Le champ **LineNumber** sera utilisé comme identificateur pour la table imbriquée, ou `Sequence Key`. La clé pour une table imbriquée doit toujours être utilisée pour l'entrée.  
  
    -   **Modèle** Activez les cases à cocher **entrée** et **prédiction** .  
  
     Vérifiez que les sélections sont correctes, puis cliquez sur **suivant**.  
  
8.  Dans la page **spécifier le type de contenu et de données des colonnes** , vérifiez que la grille contient les colonnes, les types de contenu et les types de données indiqués dans le tableau suivant, puis cliquez sur **suivant**.  
  
    |Tables/Colonnes|Type de contenu|Type de données|  
    |---------------------|------------------|---------------|  
    |IncomeGroup|Discret|Texte|  
    |OrderNumber|Clé|Texte|  
    |Région|Discret|Texte|  
    |vAssocSeqLineItems|||  
    |Numéro de ligne|Séquence clé|Long|  
    |Modèle|Discret|Texte|  
  
9. Sur la page **créer un jeu de test** , modifiez le **pourcentage de données pour le test** sur 20, puis cliquez sur **suivant**.  
  
10. Dans la page **fin de l’Assistant** , pour **nom**de la structure d' `Sequence Clustering with Region`exploration de données, tapez.  
  
11. Pour le **nom du modèle**d’exploration `Sequence Clustering with Region`de données, tapez.  
  
12. Cochez la case **autoriser l’extraction** , puis cliquez sur **Terminer**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Traitement du modèle Sequence Clustering](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur d’exploration de données](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Algorithme MSC (Microsoft Sequence Clustering)](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)  
  
  
