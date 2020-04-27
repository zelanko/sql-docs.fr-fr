---
title: Modification et traitement du modèle Market Basket (Didacticiel intermédiaire sur l’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b6019413-aebd-4ff7-831a-644572ad88b1
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4987e3497b7d52ff11f8f52bc403105340f7f508
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63301369"
---
# <a name="modifying-and-processing-the-market-basket-model-intermediate-data-mining-tutorial"></a>Modification et traitement du modèle de panier d'achat (Didacticiel intermédiaire sur l'exploration de données)
  Avant de traiter le modèle d’exploration de données d’association que vous avez créé, vous devez modifier les valeurs par défaut de deux des paramètres : *support* et *probabilité*.  
  
-   La *prise en charge* définit le pourcentage de cas dans lesquels une règle doit exister avant d’être considérée comme valide. Vous allez spécifier qu'une règle doit être présente dans au moins 1 pour cent des cas.  
  
-   La probabilité définit la *probabilité* d’une association avant qu’elle soit considérée comme valide. Vous prendrez en compte toute association ayant une probabilité d'au moins 10 pour cent.  
  
 Pour plus d’informations sur les effets de l’augmentation ou de la réduction de la prise en charge et de la probabilité, consultez informations techniques de référence sur l' [algorithme Microsoft Association](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md).  
  
 Une fois que vous avez défini la structure et les paramètres du modèle d’exploration de données d' **Association** , vous devez traiter le modèle.  
  
### <a name="to-adjust-the-parameters-of-the-association-model"></a>Pour modifier les paramètres du modèle d'association  
  
1.  Ouvrez l’onglet **modèles d’exploration** de données du concepteur d’exploration de données.  
  
2.  Cliquez avec le bouton droit sur la colonne **Association** dans la grille du concepteur et sélectionnez **définir les paramètres d’algorithme pour ouvrir la boîte de dialogue Paramètres d’algorithme** .  
  
3.  Dans la colonne **valeur** de la boîte de dialogue **paramètres d’algorithme** , définissez les paramètres suivants :  
  
     MINIMUM_PROBABILITY = 0.1  
  
     MINIMUM_SUPPORT = 0.01  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-process-the-mining-model"></a>Pour traiter le modèle d'exploration de données  
  
1.  Dans le menu modèle d’exploration [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]de **données** de, sélectionnez traiter l’exploration de **données et tous les modèles.**  
  
2.  Cliquez sur **Oui**pour répondre à l'avertissement qui vous invite à indiquer si vous souhaitez générer et déployer le projet.  
  
     La boîte **de dialogue traiter la structure d’exploration de données-Association** s’ouvre.  
  
3.  Cliquez sur **Exécuter**.  
  
     La boîte de dialogue **État d'avancement du traitement** s'affiche et présente les informations relatives au traitement du modèle. Le traitement de la nouvelle structure et du nouveau modèle peut prendre un certain temps.  
  
4.  Une fois le traitement terminé, cliquez sur **Fermer** pour quitter la boîte de dialogue **État d'avancement du traitement** .  
  
5.  Cliquez à nouveau sur **Fermer** pour quitter la boîte de dialogue **traiter la structure d’exploration de données-Association** .  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Exploration des modèles de panier d’évolution &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exigences et considérations concernant le traitement &#40;exploration de données&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
