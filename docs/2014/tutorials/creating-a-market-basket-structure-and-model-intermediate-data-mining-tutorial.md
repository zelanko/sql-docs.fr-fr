---
title: Création d’un modèle (didacticiel d’exploration de données intermédiaire) et la Structure Market Basket | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 659b7a4e-f687-44d9-a60a-86490ccbf90f
caps.latest.revision: 48
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 67d047a9bb78a8c85d59131407cc85c6aa4769f7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238129"
---
# <a name="creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial"></a>Création d'une structure et d'un modèle de panier d'achat (Didacticiel sur l'exploration de données intermédiaire)
  Maintenant que vous avez créé une vue de source de données, vous allez utiliser l'Assistant Exploration de données pour créer une structure d'exploration de données. Au cours de cette tâche, vous allez créer une structure d'exploration de données et un modèle d'exploration de données basés sur l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Association.  
  
> [!NOTE]  
>  Si vous recevez un message d'erreur stipulant que vAssocSeqLineItems ne peut pas être utilisé comme table imbriquée, revenez à la tâche précédente de la leçon et assurez-vous de créer la jointure plusieurs-à-un en faisant glisser le curseur de la table vAssocSeqLineItems (côté plusieurs) vers la table vAssocSeqOrders (côté un). Vous pouvez également modifier la relation entre les tables en cliquant avec le bouton droit sur la ligne de jointure.  
  
### <a name="to-create-an-association-mining-structure"></a>Pour créer une structure d'exploration de données d'association  
  
1.  Dans l’Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], avec le bouton droit **des Structures d’exploration de données** et sélectionnez **nouvelle Structure d’exploration de données** pour ouvrir l’Assistant exploration de données.  
  
2.  Dans la page **Assistant Exploration de données** , cliquez sur **Suivant**.  
  
3.  Sur le **sélectionner la méthode de définition** page, vérifiez que **à partir de l’entrepôt de données ou de la base de données relationnelle existant** est sélectionnée, puis cliquez sur **suivant**.  
  
4.  Sur le **créer la Structure d’exploration de données** page sous **quelle technique d’exploration de données voulez-vous utiliser ?**, sélectionnez **Microsoft Association Rules** dans la liste, puis cliquez sur **Suivant**. Le **sélectionner une vue de Source de données** page s’affiche.  
  
5.  Sélectionnez **commandes**sous **vues de sources de données disponibles**, puis cliquez sur **suivant**.  
  
6.  Sur le **spécifier les Types de Table** , dans la ligne de la table vAssocSeqLineItems, sélectionnez le **Nested** et dans la ligne de la table imbriquée vAssocSeqOrders, cochez la **cas** case à cocher. Cliquez sur **Suivant**.  
  
7.  Sur le **spécifier les données d’apprentissage** page, désactivez les cases qui peuvent être archivés. Définissez la clé pour la table de cas vAssocSeqOrders en activant le **clé** case à cocher en regard d’OrderNumber.  
  
     Étant donné que l’objectif de l’analyse du panier consiste à déterminer quels produits sont inclus dans une transaction unique, il est inutile d’utiliser le **CustomerKey** champ.  
  
8.  Définissez la clé de la table imbriquée, vAssocSeqLineItems, en activant le **clé** case à cocher en regard du modèle. Le **entrée** case à cocher est activée automatiquement lorsque vous effectuez cette opération. Sélectionnez le **prédictible** case à cocher pour `Model` également.  
  
     Dans un modèle de panier d’achat, vous ne se souciez pas sur la séquence de produits dans le panier d’achat, et par conséquent, vous ne devez pas inclure **LineNumber** en tant que clé pour la table imbriquée. Vous utiliseriez **LineNumber** en tant que clé uniquement dans un modèle où l’ordre est important. Vous allez créer un modèle qui utilise l'algorithme MSC ([!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering) au cours de la leçon 4.  
  
9. Activez la case à cocher située à gauche d'IncomeGroup et Region, mais ne faites pas d'autres sélections. La sélection de la colonne la plus à gauche ajoute les colonnes à la structure à des fins de référence ultérieure, mais les colonnes ne sont pas utilisées dans le modèle. Vos sélections doivent ressembler aux suivantes :  
  
     ![aspect de la boîte de dialogue](../../2014/tutorials/media/tutorial-configassocmodel.gif "aspect de la boîte de dialogue")  
  
10. Cliquez sur **Suivant**.  
  
11. Sur le **colonnes spécifier Type de contenu et données**page, passez en revue les sélections, qui doivent être comme indiqué dans le tableau suivant, puis cliquez sur **suivant**.  
  
    |Colonnes|Type de contenu|Type de données|  
    |-------------|------------------|---------------|  
    |IncomeGroup|Discret|Texte|  
    |Numéro de commande|Key|Texte|  
    |Région|Discret|Texte|  
    |vAssocSeqLineItems|||  
    |Modèle|Key|Texte|  
  
12. Sur le **créer le test défini** page, la valeur par défaut pour l’option **pourcentage des données de test** 30 pour cent. Modifier ce paramètre pour **0**. Cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fournit différents graphiques pour mesurer la précision du modèle. Toutefois, certains types de graphiques d'analyse de précision, tels que le graphique de courbes d'élévation et le rapport de validation croisée, sont conçus pour la classification et l'évaluation. Elles ne sont pas prises en charge à des fins de prédiction associative.  
  
13. Sur le **fin de l’Assistant** page **nom de la structure d’exploration de données**, type `Association`.  
  
14. Dans **nom du modèle d’exploration de données**, type `Association`.  
  
15. Sélectionnez l’option **accepter l’extraction**, puis cliquez sur **Terminer**.  
  
     Concepteur d’exploration de données s’ouvre et affiche le `Association` structure d’exploration de données que vous venez de créer.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Modification et traitement du modèle de panier &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithme Microsoft Association](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)   
 [Types de contenu &#40;exploration de données&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)  
  
  
