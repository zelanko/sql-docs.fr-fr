---
title: Modifier la Partition DirectQuery (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: f9df1e66-dd23-41b4-95eb-af110d10eda4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b247bd63087003b1c9205719a6d1cb0563390cc3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48161537"
---
# <a name="change-the-directquery-partition-ssas-tabular"></a>Modifier la partition DirectQuery (SSAS Tabulaire)
  Dans la mesure où une seule partition d'une table peut être désignée en tant que partition DirectQuery, par défaut, Analysis Services utilise la première partition qui a été créée dans la table. Pendant la création du projet de modèle, vous pouvez modifier la partition DirectQuery à l'aide de la boîte de dialogue Gestionnaire de partitions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Pour les modèles déployés, vous pouvez modifier la partition DirectQuery à l'aide de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
### <a name="change-the-directquery-partition-for-a-tabular-model-project"></a>Modifier la partition DirectQuery pour un projet de modèle tabulaire  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le générateur de modèles, cliquez sur la table (l'onglet) qui contient la table partitionnée.  
  
2.  Cliquez sur le menu **Table** , puis sur **Partitions**.  
  
3.  Dans le **Gestionnaire de partitions**, la partition correspondant à la partition de requête directe active est indiquée par le préfixe **(DirectQuery)** dans le nom de la partition.  
  
     Sélectionnez une autre partition dans la liste **Partitions** , puis cliquez sur **Définir comme DirectQuery**. Le bouton **Définir comme DirectQuery** n'est pas activé lorsque la partition DirectQuery active est sélectionnée, et n'est pas visible si le modèle n'a pas été activé pour le mode de requête directe.  
  
4.  Si nécessaire, modifiez les options de traitement, puis cliquez sur **OK**.  
  
### <a name="change-the-directquery-partition-for-a-deployed-tabular-model"></a>Modifier la partition DirectQuery pour un modèle tabulaire déployé  
  
1.  Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], ouvrez la base de données model dans l'Explorateur d'objets.  
  
2.  Développez le nœud **Tables** , cliquez avec le bouton droit sur la table partitionnée, puis sélectionnez **Partitions**.  
  
     La partition qui est indiquée pour être utilisée avec le mode DirectQuery a le préfixe (DirectQuery) sur le nom de partition.  
  
3.  Pour passer à une autre partition, cliquez sur l'icône de la barre d'outils **Requête directe** pour ouvrir la boîte de dialogue **Définir une partition DirectQuery** . L'icône de la barre d'outils DirectQuery n'est pas disponible sur les modèles qui n'ont pas été activés pour la requête directe.  
  
4.  Choisissez une autre partition dans la liste déroulante **Nom de la partition** , puis modifiez les options de traitement sur la partition, si nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions &#40;SSAS tabulaire&#41;](tabular-models/partitions-ssas-tabular.md)  
  
  
