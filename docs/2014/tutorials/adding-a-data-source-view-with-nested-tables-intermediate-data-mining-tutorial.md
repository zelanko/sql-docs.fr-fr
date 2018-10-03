---
title: Ajout d’un Data Source View avec des Tables imbriquées (didacticiel d’exploration de données intermédiaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: a14cd7f1-7a10-4ec6-af6a-f5f0676a0308
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 70db9a9ff6ed8aa5c9a960ae40009369341b99b4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068039"
---
# <a name="adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial"></a>Ajout d'une vue de source de données avec les tables imbriquées (Didacticiel intermédiaire sur l'exploration de données)
  Pour créer un modèle de panier d'achat, vous devez utiliser une vue de source de données qui prend en charge les données associatives. Cette vue de source de données sera également utilisée pour le scénario Sequence Clustering.  
  
 Cette vue de source de données est différente des autres que vous avez travaillé, car elle contient un *table imbriquée*. Un *table imbriquée* est une table qui contient plusieurs lignes d’informations sur une seule ligne dans la table de cas. Par exemple, si votre modèle analyse le comportement d'achat de clients, vous utilisez généralement une table qui a une ligne unique pour chaque client comme table de cas. Toutefois, chaque client peut faire plusieurs achats, et vous pouvez analyser la séquence des achats, ou les produits qui sont fréquemment achetés ensemble. Pour représenter de façon logique ces achats dans votre modèle, vous ajoutez une autre table à la vue de source de données qui répertorie les achats pour chaque client.  
  
 Cette table des achats imbriquée présente une relation plusieurs-à-un avec la table des clients. La table imbriquée peut contenir de nombreuses lignes pour chaque client, chaque ligne contenant un produit unique ayant été acheté, ainsi que des informations supplémentaires éventuelles sur l'ordre dans lequel les achats ont été effectués, le prix au moment de la commande ou les promotions appliquées. Vous pouvez utiliser les informations dans la table imbriquée comme entrées au modèle, ou comme attribut prédictible.  
  
 Dans cette leçon, vous effectuez les tâches suivantes :  
  
-   Vous ajoutez une vue de source de données pour le [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] source de données.  
  
-   Vous ajoutez à cette vue la table de cas et la table imbriquée.  
  
-   Vous spécifiez la relation plusieurs-à-un entre la table de cas et la table imbriquée.  
  
    > [!NOTE]  
    >  . Il est essentiel de suivre exactement la procédure décrite, afin de spécifier correctement la relation entre la table de cas et la table imbriquée, et ainsi éviter les erreurs lorsque vous traiterez le modèle.  
  
-   Vous définissez le mode d'utilisation des colonnes de données dans le modèle.  
  
 Pour plus d’informations sur l’utilisation de cas et des tables imbriquées et comment choisir une clé de table imbriquée, consultez [des Tables imbriquées &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).  
  
### <a name="to-add-a-data-source-view"></a>Pour ajouter une vue de source de données  
  
1.  Dans l’Explorateur de solutions, cliquez sur **les vues de sources de données**, puis sélectionnez **nouvelle vue de Source de données**.  
  
     L'Assistant Vue de source de données s'ouvre.  
  
2.  Dans la page **Assistant Vue de source de données** , cliquez sur **Suivant**.  
  
3.  Sur le **sélectionner une Source de données** page sous **sources de données relationnelles**, sélectionnez le [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] source de données que vous avez créé dans le didacticiel d’exploration de données base de données. Cliquez sur **Suivant**.  
  
4.  Sur le **sélectionner des Tables et vues** page, sélectionnez les tables suivantes, puis cliquez sur la flèche droite pour les inclure dans la nouvelle vue de source de données :  
  
    -   `vAssocSeqOrders`  
  
    -   `vAssocSeqLineItems`  
  
5.  Cliquez sur **Suivant**.  
  
6.  Sur le **fin de l’Assistant** page, la vue de source de données est nommée par défaut [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. Remplacez le nom par `Orders`, puis cliquez sur **Terminer**.  
  
     Concepteur de vue de Source de données s’ouvre et le `Orders` vue de source de données s’affiche.  
  
### <a name="to-create-a-relationship-between-tables"></a>Pour créer une relation entre des tables  
  
1.  Dans le Concepteur de vue de source de données, positionnez les deux tables afin que les tables soient alignées horizontalement, avec la table vAssocSeqLineItems sur le côté gauche et la table vAssocSeqOrders sur le côté droit.  
  
2.  Sélectionnez le **OrderNumber** colonne dans la table vAssocSeqLineItems.  
  
3.  Faites glisser la colonne vers la table vAssocSeqOrders et la placer dans le **OrderNumber** colonne.  
  
    > [!IMPORTANT]  
    >  Veillez à faire glisser le **OrderNumber** colonne à partir de la table imbriquée vAssocSeqLineItems, qui représente le côté « plusieurs » de la jointure, à la table de cas vAssocSeqOrders, qui représente un côté de la jointure.  
  
     Un nouveau *relation plusieurs-à-un* existe maintenant entre les tables vAssocSeqLineItems et vAssocSeqOrders. Si vous avez joint les tables correctement, la vue de source de données doit apparaître comme suit :  
  
     ![jointure de plusieurs-à-un attendue sur la table de cas ou imbriquée](../../2014/tutorials/media/dsv-nestedjoin-illustration.gif "attendu jointure plusieurs-à-un sur la table de cas ou imbriquée")  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création d’un modèle et la Structure Market Basket &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’exploration de données intermédiaire &#40;Analysis Services - Exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
