---
title: Création d’une structure et d’un modèle de panier d’un marché (Didacticiel intermédiaire sur l’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 659b7a4e-f687-44d9-a60a-86490ccbf90f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 207d82f740b7b5ff174e220e647d67d5bac7f9ea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63190835"
---
# <a name="creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial"></a>Création d'une structure et d'un modèle de panier d'achat (Didacticiel sur l'exploration de données intermédiaire)
  Maintenant que vous avez créé une vue de source de données, vous allez utiliser l'Assistant Exploration de données pour créer une structure d'exploration de données. Au cours de cette tâche, vous allez créer une structure d'exploration de données et un modèle d'exploration de données basés sur l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Association.  
  
> [!NOTE]  
>  Si vous recevez un message d'erreur stipulant que vAssocSeqLineItems ne peut pas être utilisé comme table imbriquée, revenez à la tâche précédente de la leçon et assurez-vous de créer la jointure plusieurs-à-un en faisant glisser le curseur de la table vAssocSeqLineItems (côté plusieurs) vers la table vAssocSeqOrders (côté un). Vous pouvez également modifier la relation entre les tables en cliquant avec le bouton droit sur la ligne de jointure.  
  
### <a name="to-create-an-association-mining-structure"></a>Pour créer une structure d'exploration de données d'association  
  
1.  Dans Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], cliquez avec le bouton droit sur **structures d’exploration** de données et sélectionnez **nouvelle structure d’exploration** de données pour ouvrir l’Assistant Exploration de données.  
  
2.  Dans la page **Assistant Exploration de données** , cliquez sur **Suivant**.  
  
3.  Sur la page **Sélectionner la méthode de définition** , vérifiez que **à partir de la base de données relationnelle ou de l’entrepôt de données existant** est sélectionné, puis cliquez sur **suivant**.  
  
4.  Dans la page **créer la structure d’exploration de données** , sous **quelle technique d’exploration de données voulez-vous utiliser ?**, sélectionnez **règles d’association Microsoft** dans la liste, puis cliquez sur **suivant**. La page **Sélectionner une vue de source de données** s’affiche.  
  
5.  Sélectionnez **Orders**sous **vues de sources de données disponibles**, puis cliquez sur **suivant**.  
  
6.  Dans la page **spécifier les types des tables** , dans la ligne de la table vAssocSeqLineItems, activez la case à cocher **imbriqué** , puis dans la ligne de la table imbriquée vAssocSeqOrders, activez la case à cocher **cas** . Cliquez sur **Suivant**.  
  
7.  Dans la page **spécifier les données d’apprentissage** , désactivez toutes les cases qui peuvent être activées. Définissez la clé pour la table de cas, vAssocSeqOrders, en activant la case à cocher **clé** en regard de OrderNumber.  
  
     Étant donné que l’objectif de l’analyse du panier d’opérations est de déterminer quels produits sont inclus dans une transaction unique, il n’est pas nécessaire d’utiliser le champ **CustomerKey** .  
  
8.  Définissez la clé pour la table imbriquée, vAssocSeqLineItems, en activant la case à cocher **clé** en regard de modèle. La case à cocher **entrée** est également automatiquement activée lorsque vous effectuez cette opération. Activez également la case à cocher `Model` **prévisible** .  
  
     Dans un modèle de panier d’achat, vous ne vous souciez pas de la séquence de produits dans le panier d’achat. par conséquent, vous ne devez pas inclure **LineNumber** comme clé pour la table imbriquée. Vous pouvez utiliser **LineNumber** comme clé uniquement dans un modèle où la séquence est importante. Vous allez créer un modèle qui utilise l'algorithme MSC ([!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering) au cours de la leçon 4.  
  
9. Activez la case à cocher située à gauche d'IncomeGroup et Region, mais ne faites pas d'autres sélections. La sélection de la colonne la plus à gauche ajoute les colonnes à la structure à des fins de référence ultérieure, mais les colonnes ne sont pas utilisées dans le modèle. Vos sélections doivent ressembler aux suivantes :  
  
     ![Présentation d'une boîte de dialogue](../../2014/tutorials/media/tutorial-configassocmodel.gif "Présentation d'une boîte de dialogue")  
  
10. Cliquez sur **Suivant**.  
  
11. Dans la page **spécifier le type de contenu et de données des colonnes**, passez en revue les sélections, comme indiqué dans le tableau suivant, puis cliquez sur **suivant**.  
  
    |Colonnes|Type de contenu|Type de données|  
    |-------------|------------------|---------------|  
    |IncomeGroup|Discret|Texte|  
    |Order Number|Clé|Texte|  
    |Région|Discret|Texte|  
    |vAssocSeqLineItems|||  
    |Modèle|Clé|Texte|  
  
12. Sur la page **créer un jeu de test** , la valeur par défaut de l’option **pourcentage de données pour le test** est de 30 pour cent. Remplacez cette **valeur par 0**. Cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fournit différents graphiques pour mesurer la précision du modèle. Toutefois, certains types de graphiques d'analyse de précision, tels que le graphique de courbes d'élévation et le rapport de validation croisée, sont conçus pour la classification et l'évaluation. Elles ne sont pas prises en charge à des fins de prédiction associative.  
  
13. Dans la page **fin de l’Assistant** , dans nom de la structure `Association`d’exploration de **données**, tapez.  
  
14. Dans **nom du modèle**d’exploration `Association`de données, tapez.  
  
15. Sélectionnez l’option **autoriser l’extraction**, puis cliquez sur **Terminer**.  
  
     Le concepteur d’exploration de données s' `Association` ouvre pour afficher la structure d’exploration de données que vous venez de créer.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Modification et traitement du modèle Market Basket &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithme d’association Microsoft](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)   
 [Types de contenu &#40;l’exploration de données&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)  
  
  
