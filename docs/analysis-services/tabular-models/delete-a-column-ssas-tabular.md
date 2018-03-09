---
title: Supprimer une colonne | Documents Microsoft
ms.custom: 
ms.date: 02/22/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 703db83b-e554-450e-813e-23ad08c1cdad
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c18504b3e6430807f124938b60d7f022a8050379
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="delete-a-column"></a>Supprimer une colonne 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Cet article décrit comment supprimer une colonne d’une table de modèle tabulaire.  
  
## <a name="delete-a-model-table-column"></a>Supprimer une colonne de table de modèle  
  
> [!NOTE]  
>  La suppression d'une colonne d'une table de modèle ne supprime pas la colonne d'une définition de requête de partition. Si la colonne que vous supprimez fait partie d'une partition, vous devez supprimer manuellement la colonne de la définition de requête de partition. Si vous ne supprimez pas la colonne de la définition de requête de partition, la colonne sera interrogée et des données retournées, mais elles ne seront pas ajoutées la table de modèle pendant le traitement des opérations. Pour plus d’informations, consultez [Partitions](../../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
#### <a name="to-delete-a-model-table-column"></a>Pour supprimer une colonne de table de modèle  
  
-   Dans le générateur de modèles, dans la table qui contient la colonne à supprimer, cliquez avec le bouton droit sur la colonne, puis cliquez sur **Supprimer**.  
  
#### <a name="to-delete-a-model-table-column-by-using-the-table-properties-dialog-box"></a>Pour supprimer une colonne de table de modèle à l'aide de la boîte de dialogue Propriétés de la table  
  
1.  Dans le générateur de modèles, cliquez sur la table qui contient la colonne à supprimer, cliquez sur le menu **Table** , puis sur  **Propriétés de la table**.  
  
2.  Dans **Origine des noms de colonnes**, sélectionnez **Modèle** (*pour utiliser les noms de colonne de la table de modèle, si différents de la source*).  
  
3.  Dans la boîte de dialogue **Modifier les propriétés de la table** , dans la fenêtre d’aperçu de la table, décochez la colonne à supprimer, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des colonnes à une table](../../analysis-services/tabular-models/add-columns-to-a-table-ssas-tabular.md)   
 [Partitions](../../analysis-services/tabular-models/partitions-ssas-tabular.md)  
  
  
