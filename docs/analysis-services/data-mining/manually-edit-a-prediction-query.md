---
title: "Modifier manuellement une requête de prédiction | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying prediction queries
- Mining Model Prediction [Analysis Services], modifying prediction queries
- manual prediction query modification [Analysis Services]
ms.assetid: 9f6a9298-49d5-4675-ad49-977a47dff5a6
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 48eb031ed8d8bd7d2788f74c349d4ff03eb27bb8
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="manually-edit-a-prediction-query"></a>Modifier manuellement une requête de prédiction
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Après avoir conçu une requête à l’aide du Générateur de requêtes de prédiction, vous pouvez modifier la requête en basculant en vue de texte de la requête le **prévision de modèle d’exploration de données** onglet du Concepteur d’exploration de données. Un éditeur de texte apparaît au bas de l'écran pour afficher la requête créée par le Générateur de requêtes.  
  
 Le basculement vers le mode Texte de la requête est utile pour effectuer des ajouts à la requête. Par exemple, vous pouvez ajouter une clause WHERE ou une clause ORDER BY.  
  
 Utilisez la grille dans le Générateur de requêtes de prédiction pour insérer le nom des objets et des colonnes, ainsi que pour configurer la syntaxe de fonctions de prédiction individuelles, puis basculez vers le mode de modification manuelle pour modifier des valeurs de paramètres.  
  
> [!NOTE]  
>  Si vous repassez du mode **Texte de la requête** au mode **Conception** , toutes les modifications apportées en mode **Texte de la requête** sont perdues.  
  
### <a name="modify-a-query"></a>Modifier une requête  
  
1.  Sous l’onglet **Prédiction de modèle d’exploration de données** du Concepteur d’exploration de données de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur **SQL**.  
  
     La grille au bas de l'écran est remplacée par un éditeur de texte qui contient la requête. Vous pouvez modifier la requête dans cet éditeur.  
  
2.  Pour exécuter la requête, dans le menu **Modèle d’exploration de données** , sélectionnez **Résultat**ou cliquez sur le bouton pour passer aux résultats de la requête.  
  
    > [!NOTE]  
    >  Si la requête que vous avez créée n'est pas valide, la fenêtre Résultats n'affiche ni erreur ni résultats. Cliquez sur le bouton **Conception** ou sélectionnez **Conception** ou **Requête** dans le menu **Modèle d’exploration de données** pour résoudre le problème et réexécuter la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Requêtes d'exploration de données](../../analysis-services/data-mining/data-mining-queries.md)   
 [Générateur de requête de prédiction &#40; exploration de données &#41;](http://msdn.microsoft.com/library/12900d49-db88-48bb-a5f4-0a9a172bc126)   
 [Leçon 6 : création et utilisation de prédictions &#40;Didacticiel sur l’exploration de données de base&#41;](http://msdn.microsoft.com/library/b213cb58-2c40-4c89-b08b-d3c36a4afad3)  
  
  
