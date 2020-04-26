---
title: Ajout d’une vue de source de données avec des tables imbriquées (didacticiel sur l’exploration de données intermédiaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a14cd7f1-7a10-4ec6-af6a-f5f0676a0308
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 648b9d561ae340b67ed5e2d1aa878969e5a3bc47
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62822775"
---
# <a name="adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial"></a>Ajout d'une vue de source de données avec les tables imbriquées (Didacticiel intermédiaire sur l'exploration de données)
  Pour créer un modèle de panier d'achat, vous devez utiliser une vue de source de données qui prend en charge les données associatives. Cette vue de source de données sera également utilisée pour le scénario Sequence Clustering.  
  
 Cette vue de source de données est différente des autres que vous avez pu utiliser, car elle contient une *table imbriquée*. Une *table imbriquée* est une table qui contient plusieurs lignes d’informations sur une seule ligne dans la table de cas. Par exemple, si votre modèle analyse le comportement d'achat de clients, vous utilisez généralement une table qui a une ligne unique pour chaque client comme table de cas. Toutefois, chaque client peut faire plusieurs achats, et vous pouvez analyser la séquence des achats, ou les produits qui sont fréquemment achetés ensemble. Pour représenter de façon logique ces achats dans votre modèle, vous ajoutez une autre table à la vue de source de données qui répertorie les achats pour chaque client.  
  
 Cette table des achats imbriquée présente une relation plusieurs-à-un avec la table des clients. La table imbriquée peut contenir de nombreuses lignes pour chaque client, chaque ligne contenant un produit unique ayant été acheté, ainsi que des informations supplémentaires éventuelles sur l'ordre dans lequel les achats ont été effectués, le prix au moment de la commande ou les promotions appliquées. Vous pouvez utiliser les informations dans la table imbriquée comme entrées au modèle, ou comme attribut prédictible.  
  
 Dans cette leçon, vous effectuez les tâches suivantes :  
  
-   Vous ajoutez une vue de source de données [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] à la source de données.  
  
-   Vous ajoutez à cette vue la table de cas et la table imbriquée.  
  
-   Vous spécifiez la relation plusieurs-à-un entre la table de cas et la table imbriquée.  
  
    > [!NOTE]  
    >  . Il est essentiel de suivre exactement la procédure décrite, afin de spécifier correctement la relation entre la table de cas et la table imbriquée, et ainsi éviter les erreurs lorsque vous traiterez le modèle.  
  
-   Vous définissez le mode d'utilisation des colonnes de données dans le modèle.  
  
 Pour plus d’informations sur l’utilisation des tables de cas et imbriquées, ainsi que sur la façon de choisir une clé de table imbriquée, consultez [tables imbriquées &#40;Analysis Services-exploration de données&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).  
  
### <a name="to-add-a-data-source-view"></a>Pour ajouter une vue de source de données  
  
1.  Dans Explorateur de solutions, cliquez avec le bouton droit sur **vues de source de données**, puis sélectionnez **nouvelle vue de source de données**.  
  
     L'Assistant Vue de source de données s'ouvre.  
  
2.  Sur la page **Bienvenue dans l'Assistant Sources de données**, cliquez sur **Suivant**.  
  
3.  Dans la page **Sélectionner une source de données** , sous **sources de données relationnelles**, [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] sélectionnez la source de données que vous avez créée dans le didacticiel sur l’exploration de données de base. Cliquez sur **Suivant**.  
  
4.  Dans la page **Sélectionner des tables et des vues** , sélectionnez les tables suivantes, puis cliquez sur la flèche droite pour les inclure dans la nouvelle vue de source de données :  
  
    -   `vAssocSeqOrders`  
  
    -   `vAssocSeqLineItems`  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans la page **fin de l’Assistant** , la vue de source de données est [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]nommée par défaut. Remplacez le nom par `Orders`, puis cliquez sur **Terminer**.  
  
     Le concepteur de vue de source de `Orders` données s’ouvre et la vue de source de données s’affiche.  
  
### <a name="to-create-a-relationship-between-tables"></a>Pour créer une relation entre des tables  
  
1.  Dans le Concepteur de vue de source de données, positionnez les deux tables afin que les tables soient alignées horizontalement, avec la table vAssocSeqLineItems sur le côté gauche et la table vAssocSeqOrders sur le côté droit.  
  
2.  Sélectionnez la colonne **OrderNumber** dans la table vAssocSeqLineItems.  
  
3.  Faites glisser la colonne vers la table vAssocSeqOrders et placez-la sur la colonne **OrderNumber** .  
  
    > [!IMPORTANT]  
    >  Veillez à faire glisser la colonne **OrderNumber** de la table imbriquée vAssocSeqLineItems, qui représente le côté « plusieurs » de la jointure, vers la table de cas vAssocSeqOrders, qui représente le côté « un » de la jointure.  
  
     Une nouvelle *relation plusieurs-à-un* existe désormais entre les tables VAssocSeqLineItems et vAssocSeqOrders. Si vous avez joint les tables correctement, la vue de source de données doit apparaître comme suit :  
  
     ![jointure plusieurs-à-un attendue sur des tables imbriquées et des tables de cas](../../2014/tutorials/media/dsv-nestedjoin-illustration.gif "jointure plusieurs-à-un attendue sur des tables imbriquées et des tables de cas")  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création d’une structure et d’un modèle de panier d’évolution &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel sur l’exploration de données intermédiaire &#40;Analysis Services d’exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Structures d’exploration de données &#40;Analysis Services d’exploration de données&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
