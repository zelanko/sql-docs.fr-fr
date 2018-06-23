---
title: Modifier la Partition DirectQuery (SSAS tabulaire) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9df1e66-dd23-41b4-95eb-af110d10eda4
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5c777c0ce70d06b979fbc26ac8f50df1bdbd858d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140405"
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
  
  