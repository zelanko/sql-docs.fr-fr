---
title: Modification et traitement du modèle de panier d’achat (didacticiel sur l’exploration des données intermédiaires) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b6019413-aebd-4ff7-831a-644572ad88b1
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 96eb44713cd34fdcea81a7e5e4daf26739afdec1
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36311907"
---
# <a name="modifying-and-processing-the-market-basket-model-intermediate-data-mining-tutorial"></a>Modification et traitement du modèle de panier d'achat (Didacticiel intermédiaire sur l'exploration de données)
  Avant de traiter le modèle d’exploration de données d’association que vous avez créé, vous devez modifier les valeurs par défaut de deux paramètres : *prise en charge* et *probabilité*.  
  
-   *Prise en charge* définit le pourcentage de cas dans lequel une règle doit exister avant qu’il est considéré comme valide. Vous allez spécifier qu'une règle doit être présente dans au moins 1 pour cent des cas.  
  
-   *Probabilité* définit comment probablement une association doit être est considérée comme valide. Vous prendrez en compte toute association ayant une probabilité d'au moins 10 pour cent.  
  
 Pour plus d’informations sur les effets de l’augmentation ou de diminution de prise en charge et probabilité, consultez [l’algorithme Microsoft Association Technical Reference](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md).  
  
 Après avoir défini la structure et les paramètres pour le **Association** modèle d’exploration de données, vous allez traiter le modèle.  
  
### <a name="to-adjust-the-parameters-of-the-association-model"></a>Pour modifier les paramètres du modèle d'association  
  
1.  Ouvrez le **des modèles d’exploration de données** onglet du Concepteur d’exploration de données.  
  
2.  Avec le bouton droit le **Association** colonne dans la grille dans le concepteur et sélectionnez **paramètres d’algorithme défini pour ouvrir les paramètres d’algorithme** boîte de dialogue.  
  
3.  Dans le **valeur** colonne de la **paramètres d’algorithme** boîte de dialogue, définissez les paramètres suivants :  
  
     MINIMUM_PROBABILITY = 0.1  
  
     MINIMUM_SUPPORT = 0.01  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-process-the-mining-model"></a>Pour traiter le modèle d'exploration de données  
  
1.  Sur le **modèle d’exploration de données** menu de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], sélectionnez **traiter la Structure d’exploration de données et tous les modèles.**  
  
2.  Cliquez sur **Oui**pour répondre à l'avertissement qui vous invite à indiquer si vous souhaitez générer et déployer le projet.  
  
     Le **traiter la Structure d’exploration de données - Association** boîte de dialogue s’ouvre.  
  
3.  Cliquez sur **Exécuter**.  
  
     La boîte de dialogue **État d'avancement du traitement** s'affiche et présente les informations relatives au traitement du modèle. Le traitement de la nouvelle structure et du nouveau modèle peut prendre un certain temps.  
  
4.  Une fois le traitement terminé, cliquez sur **Fermer** pour quitter la boîte de dialogue **État d'avancement du traitement** .  
  
5.  Cliquez sur **fermer** pour quitter le **traiter la Structure d’exploration de données - Association** boîte de dialogue.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Exploration des modèles de panier d’achat &#40;intermédiaire Didacticiel d’exploration de données&#41;](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement de la configuration requise et considérations &#40;d’exploration de données&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  