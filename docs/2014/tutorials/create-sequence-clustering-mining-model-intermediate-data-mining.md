---
title: Création d’une Structure de modèle d’exploration de données (didacticiel d’exploration de données intermédiaire) Sequence Clustering | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: e9339227-6c2e-4c4b-8be2-8c1960bc4a8d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8e91853bba6b33ed57cc0152e266994d4e0ef528
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092904"
---
# <a name="creating-a-sequence-clustering-mining-model-structure-intermediate-data-mining-tutorial"></a>Création d'une structure de modèle d'exploration de données Sequence Clustering (Didacticiel intermédiaire sur l'exploration de données)
  La première étape pour créer un modèle d'exploration de données Sequence Clustering est d'utiliser l'Assistant Exploration de données pour créer une nouvelle structure d'exploration de données et un modèle d'exploration de données selon l'algorithme MSC ([!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering).  
  
 Vous utiliserez la même vue de source de données que vous avez utilisée pour l'analyse du panier d'achat, mais vous ajouterez une colonne qui contient l'identificateur `sequence`. Dans ce scénario, la séquence signifie l'ordre dans lequel le client a ajouté des éléments au panier.  
  
 Vous ajouterez également des colonnes utilisées dans l'un des modèles pour regrouper des clients par démographie.  
  
### <a name="to-create-a-sequence-clustering-structure-and-model"></a>Pour créer un modèle et une structure Sequence Clustering  
  
1.  Dans l’Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], avec le bouton droit **des Structures d’exploration de données** et sélectionnez **nouvelle Structure d’exploration de données**.  
  
2.  Dans la page **Assistant Exploration de données** , cliquez sur **Suivant**.  
  
3.  Sur le **sélectionner la méthode de définition** page, vérifiez que **à partir de l’entrepôt de données ou de la base de données relationnelle existant** est sélectionnée, puis cliquez sur **suivant**.  
  
4.  Sur le **créer la Structure d’exploration de données** page, vérifiez que l’option **créer la structure d’exploration de données avec un modèle d’exploration de données** est sélectionné. Ensuite, cliquez sur la liste déroulante pour l’option, **quelle technique d’exploration de données voulez-vous utiliser ?**, puis sélectionnez **Microsoft Sequence Clustering**. Cliquez sur **Suivant**.  
  
     Le **sélectionner une vue de Source de données** page s’affiche. Sous **vues de sources de données disponibles**, sélectionnez `Orders`.  
  
     Orders est la même vue de source de données que vous avez utilisée pour le scénario d'analyse de panier. Si vous n’avez pas créé cette vue de source de données, consultez [Ajout d’une vue de Source de données avec des Tables imbriquées &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md).  
  
5.  Cliquez sur **Suivant**.  
  
6.  Sur le **spécifier les Types de Table** page, sélectionnez le **cas** case à cocher à côté de la **vAssocSeqOrders** de table, puis sélectionnez le **imbriqués** case à cocher à côté du **vAssocSeqLineItems** table. Cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  Si une erreur se produit lorsque vous sélectionnez le **cas** ou **Nested** cases à cocher, il peut être que la jointure dans la vue de source de données n’est pas correcte. La table imbriquée, **vAssocSeqLineItems**, doit être connectée à la table de cas **vAssocSeqOrders,** par une jointure plusieurs-à-un. Vous pouvez modifier la relation en cliquant avec le bouton droit sur la ligne de jointure et en inversant la direction de la jointure. Pour plus d’informations, consultez [créer ou modifier une boîte de dialogue relation &#40;Analysis Services - données multidimensionnelles&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md).  
  
7.  Sur le **spécifier les données d’apprentissage** page, choisissez les colonnes à utiliser dans le modèle en sélectionnant une case à cocher comme suit :  
  
    -   **IncomeGroup** sélectionner le **entrée** case à cocher.  
  
         Cette colonne contient des informations pertinentes sur les clients que vous pouvez utiliser pour le clustering. Vous les utiliserez dans le premier modèle puis les ignorerez dans le deuxième modèle.  
  
    -   **OrderNumber** sélectionner le `Key` case à cocher.  
  
         Ce champ sera utilisé comme l'identificateur de la table de cas, ou `Key`. En général, vous ne devez jamais utiliser le champ clé de la table de cas comme entrée, parce que la clé contient des valeurs uniques qui ne sont pas utiles pour le clustering.  
  
    -   **Région** sélectionner le **entrée** case à cocher.  
  
         Cette colonne contient des informations pertinentes sur les clients que vous pouvez utiliser pour le clustering. Vous les utiliserez dans le premier modèle puis les ignorerez dans le deuxième modèle.  
  
    -   **LineNumber** sélectionner le `Key` et **entrée** cases à cocher.  
  
         Le **LineNumber** champ sera utilisé comme identificateur pour la table imbriquée, ou `Sequence Key`. La clé pour une table imbriquée doit toujours être utilisée pour l'entrée.  
  
    -   **Modèle** sélectionner le **entrée** et **prédictible** cases à cocher.  
  
     Vérifiez que les sélections sont correctes, puis cliquez sur **suivant**.  
  
8.  Sur le **colonnes spécifier Type de contenu et données** page, vérifiez que la grille contient les colonnes, les types de contenu et les types de données indiqués dans le tableau suivant, puis cliquez sur **suivant**.  
  
    |Tables/Colonnes|Type de contenu|Type de données|  
    |---------------------|------------------|---------------|  
    |IncomeGroup|Discret|Texte|  
    |OrderNumber|Key|Texte|  
    |Région|Discret|Texte|  
    |vAssocSeqLineItems|||  
    |Numéro de ligne|Séquence clé|Long|  
    |Modèle|Discret|Texte|  
  
9. Sur le **créer un jeu de test** , changez le **pourcentage des données de test** sur 20, puis cliquez sur **suivant**.  
  
10. Sur le **fin de l’Assistant** page, pour le **nom de la structure d’exploration de données**, type `Sequence Clustering with Region`.  
  
11. Pour le **nom du modèle d’exploration de données**, type `Sequence Clustering with Region`.  
  
12. Vérifier le **accepter l’extraction** , puis cliquez sur **Terminer**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Traitement du modèle Sequence Clustering](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur d’exploration de données](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Algorithme MSC (Microsoft Sequence Clustering)](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)  
  
  
