---
title: Modification et traitement du modèle de panier d’achat (didacticiel d’exploration de données intermédiaire) | Microsoft Docs
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63301369"
---
# <a name="modifying-and-processing-the-market-basket-model-intermediate-data-mining-tutorial"></a>Modification et traitement du modèle de panier d'achat (Didacticiel intermédiaire sur l'exploration de données)
  Avant de traiter le modèle d’exploration de données d’association que vous avez créé, vous devez modifier les valeurs par défaut de deux des paramètres : *Prise en charge* et *probabilité*.  
  
-   *Prise en charge* définit le pourcentage de cas dans lequel une règle doit exister avant qu’il est considéré comme valide. Vous allez spécifier qu'une règle doit être présente dans au moins 1 pour cent des cas.  
  
-   *Probabilité* définit comment probablement une association doit être avant qu’il est considéré comme valide. Vous prendrez en compte toute association ayant une probabilité d'au moins 10 pour cent.  
  
 Pour plus d’informations sur les effets de l’augmentation ou diminution de la prise en charge et probabilité, consultez [l’algorithme Microsoft Association Technical Reference](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md).  
  
 Après avoir défini la structure et les paramètres pour le **Association** modèle d’exploration de données, vous allez traiter le modèle.  
  
### <a name="to-adjust-the-parameters-of-the-association-model"></a>Pour modifier les paramètres du modèle d'association  
  
1.  Ouvrez le **des modèles d’exploration de données** onglet du Concepteur d’exploration de données.  
  
2.  Avec le bouton droit le **Association** colonne dans la grille dans le concepteur et sélectionnez **paramètres d’algorithme défini pour ouvrir les paramètres d’algorithme** boîte de dialogue.  
  
3.  Dans le **valeur** colonne de la **paramètres d’algorithme** boîte de dialogue, définissez les paramètres suivants :  
  
     MINIMUM_PROBABILITY = 0.1  
  
     MINIMUM_SUPPORT = 0.01  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-process-the-mining-model"></a>Pour traiter le modèle d'exploration de données  
  
1.  Sur le **Mining Model** menu de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], sélectionnez **traiter la Structure d’exploration de données et tous les modèles.**  
  
2.  Cliquez sur **Oui**pour répondre à l'avertissement qui vous invite à indiquer si vous souhaitez générer et déployer le projet.  
  
     Le **traiter la Structure d’exploration de données - Association** boîte de dialogue s’ouvre.  
  
3.  Cliquez sur **Exécuter**.  
  
     La boîte de dialogue **État d'avancement du traitement** s'affiche et présente les informations relatives au traitement du modèle. Le traitement de la nouvelle structure et du nouveau modèle peut prendre un certain temps.  
  
4.  Une fois le traitement terminé, cliquez sur **Fermer** pour quitter la boîte de dialogue **État d'avancement du traitement** .  
  
5.  Cliquez sur **fermer** pour quitter le **traiter la Structure d’exploration de données - Association** boîte de dialogue.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Exploration des modèles de panier &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exigences et considérations concernant le traitement &#40;exploration de données&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
