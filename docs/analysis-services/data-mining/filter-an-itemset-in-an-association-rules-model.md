---
title: Filtre de modèle de règles d’un jeu d’éléments dans une Association | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8cb507be05ae8f8ad3b25b386d55785c966f14f7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68183235"
---
# <a name="filter-an-itemset-in-an-association-rules-model"></a>Filtrer un jeu d'éléments dans un modèle de règles d'association
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez filtrer les jeux d’éléments affichés sous l’onglet **Jeux d’éléments** de la visionneuse de l’algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules).  
  
### <a name="to-filter-an-itemset"></a>Pour filtrer un jeu d'éléments  
  
1.  Sous l’onglet **Visionneuse de modèle d’exploration de données** du Concepteur d’exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur l’onglet **Jeux d’éléments** de la **Visionneuse de l’algorithme MAR (Microsoft Association Rules)** .  
  
2.  Entrez une condition de règle dans la zone **Filtrer le jeu d’éléments** . Par exemple, une condition de règle pourrait être « Touring-1000 = existing ».  
  
3.  Cliquez sur **Entrée**.  
  
 Les jeux d'éléments sont filtrés pour afficher uniquement ceux qui contiennent les éléments sélectionnés. La zone ne respecte pas la casse. Les filtres sont stockés en mémoire pour vous permettre de sélectionner un ancien filtre dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et procédures de la visionneuse de modèle d’exploration de données](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  
