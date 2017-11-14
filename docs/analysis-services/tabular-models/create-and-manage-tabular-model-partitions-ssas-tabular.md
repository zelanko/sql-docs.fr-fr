---
title: "Créer et gérer des Partitions de modèles tabulaires (SSAS tabulaire) | Documents Microsoft"
ms.custom: 
ms.date: 05/31/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dab72cf0-95bc-4b63-95dc-505b5cd881c1
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 09a6acec0d1ee91c553d748a334733faff36bc08
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-and-manage-tabular-model-partitions"></a>Créer et gérer des partitions de modèles tabulaires

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Les partitions divisent une table en sections logiques. Chaque partition peut ensuite être traitée (actualisée) indépendamment d'autres partitions. Les partitions définies pour un modèle au cours de la création de modèles sont dupliquées dans un modèle déployé. Une fois le déploiement terminé, vous pouvez gérer ces partitions à l'aide de la boîte de dialogue **Partitions** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou à l'aide d'un script. Les tâches fournies dans cette rubrique décrivent comment créer et gérer des partitions pour un modèle déployé.  
  
  > [!NOTE]  
>  Partitions dans les modèles tabulaires créés au niveau de compatibilité 1400 sont définies à l’aide d’une instruction de requête M. Pour plus d’informations, consultez [M référence](https://msdn.microsoft.com/library/mt211003.aspx). 
>
  
## <a name="tasks"></a>Tâches  
 Pour créer et gérer des partitions d'une base de données de modèle tabulaire déployée, vous utiliserez la boîte de dialogue **Partitions** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour afficher la boîte de dialogue **Partitions** , dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit sur une table, puis cliquez sur **Partitions**.  
  
###  <a name="bkmk_create_new"></a> Pour créer une nouvelle partition  
  
1.  Dans la boîte de dialogue **Partitions** , cliquez sur le bouton **Nouveau** .  
  
2.  Dans **Nom de la partition**, tapez un nom pour la partition. Par défaut, le nom de la partition par défaut est numéroté de manière incrémentielle pour chaque nouvelle partition.  
  
3.  Dans **instruction de requête**, tapez ou collez une instruction de requête SQL ou M qui définit les colonnes et toutes les clauses que vous souhaitez inclure dans la partition dans la fenêtre de requête.  
  
4.  Pour valider l'instruction, cliquez sur **Vérifier la syntaxe**.  
  
###  <a name="bkmk_copy"></a> Pour copier une partition  
  
1.  Dans la boîte de dialogue **Partitions** , dans la liste **Partitions** , sélectionnez la partition à copier, puis cliquez sur le bouton **Copier** .  
  
2.  Dans **Nom de la partition**, tapez un nouveau nom pour la partition.  
  
3.  Dans **instruction de requête**, modifiez l’instruction de requête.  
  
###  <a name="bkmk_merge"></a> Pour fusionner deux ou plusieurs partitions  
  
-   Dans la boîte de dialogue **Partitions** , dans la liste **Partitions** , utilisez Ctrl+clic pour sélectionner les partitions à fusionner, puis cliquez sur le bouton **Fusionner** .  
  
> [!IMPORTANT]  
>  Le fait de fusionner les partitions ne met pas à jour les métadonnées des partitions. Vous devez modifier l’instruction SQL ou M pour la partition résultante s’assurer que les opérations de traitement traitent toutes les données dans la partition fusionnée.  
  
###  <a name="bkmk_delete"></a> Pour supprimer une partition  
  
-   Dans la boîte de dialogue **Partitions** , dans la liste **Partitions** , sélectionnez la partition à supprimer, puis cliquez sur le bouton **Supprimer** .  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions de modèles tabulaires](../../analysis-services/tabular-models/tabular-model-partitions-ssas-tabular.md)   
 [Traiter les Partitions de modèle tabulaire](../../analysis-services/tabular-models/process-tabular-model-partitions-ssas-tabular.md)  
  
  

