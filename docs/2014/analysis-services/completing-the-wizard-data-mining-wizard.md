---
title: Fin de l’Assistant (Assistant exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.finish.f1
ms.assetid: 6aef1548-35eb-42fd-ae87-63650a79eda1
caps.latest.revision: 27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 729d594d2ab714770ec168a347e044aa968d9865
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278425"
---
# <a name="completing-the-wizard-data-mining-wizard"></a>Fin de l'Assistant (Assistant Exploration de données)
  Utilisez la page **Fin de l’Assistant** pour examiner la structure d’exploration de données qui sera créée à la fin de l’Assistant. Vous pouvez également définir le nom de la structure d'exploration de données.  
  
 Si vous avez choisi de créer un modèle d'exploration de données associé, vous pouvez également définir le nom du modèle d'exploration de données associé et activer l'extraction sur le modèle d'exploration de données.  
  
> [!NOTE]  
>  Cette page varie selon que vous avez choisi **À partir d’une base de données relationnelles ou d’un entrepôt de données qui existent déjà** ou **À partir d’un cube existant** dans la page **Sélectionner la méthode de définition** de l’Assistant.  
  
 **Pour plus d’informations :** [Assistant Exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Concepteur d’exploration de données](data-mining/data-mining-designer.md), [Créer une structure d’exploration de données relationnelle](data-mining/create-a-relational-mining-structure.md)  
  
## <a name="options"></a>Options  
 **Nom de la structure d’exploration de données**  
 Tapez le nom de la structure d’exploration de données définie par **l’Assistant Exploration de données**.  
  
 **Nom du modèle d’exploration de données**  
 Tapez le nom du modèle d’exploration de données défini par **l’Assistant Exploration de données**.  
  
 **Accepter l’extraction**  
 Sélectionnez cette option pour prendre en charge les fonctionnalités d'extraction du nouveau modèle d'exploration de données, si vous en avez créé un.  
  
> [!NOTE]  
>  L'extraction sur la structure d'exploration de données est activée par défaut.  
  
 Pour plus d’informations sur les options d’extraction, consultez [Requêtes d’extraction &#40;exploration de données&#41;](data-mining/drillthrough-queries-data-mining.md).  
  
 **Aperçu**  
 Affiche la structure d'exploration de données à créer.  
  
 **Créer une Dimension du modèle d’exploration de données**  
 Sélectionnez cette option pour créer une dimension basée sur le modèle d'exploration de données à créer. Après avoir sélectionné cette option, entrez le nom de la dimension à créer. La sélection de cette option va activer l’option **Créer le cube au moyen d’une dim. du mod. d’explor. de données**.  
  
> [!NOTE]  
>  Cette option est disponible si vous avez sélectionné **À partir d’un cube existant** dans la page **Sélectionner la méthode de définition** de l’Assistant.  
  
 **Créer le cube en utilisant une dimension du modèle d'exploration de données**  
 Sélectionnez cette option pour créer un cube basé sur le modèle d'exploration de données à créer. Après avoir sélectionné cette option, entrez le nom du cube à créer.  
  
> [!NOTE]  
>  Cette option est disponible si vous avez sélectionné **À partir d’un cube existant** dans la page **Sélectionner la méthode de définition** et si vous avez sélectionné **Créer une dimension du modèle d’exploration de données** dans la page active de l’Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [Données d’aide F1 de l’Assistant exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Sélectionnez la vue de Source de données &#40;Assistant exploration de données&#41;](select-data-source-view-data-mining-wizard.md)   
 [Spécifier les données d’apprentissage &#40;Assistant exploration de données&#41;](specify-the-training-data-data-mining-wizard.md)  
  
  
