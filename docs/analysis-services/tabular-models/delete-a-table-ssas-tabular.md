---
title: Supprimer une Table (SSAS tabulaire) | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b3d1ec8c0c56a7fd1fb83f2b0401907eb0c0302c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="delete-a-table-ssas-tabular"></a>Supprimer une table (SSAS Tabulaire)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Dans le Générateur de modèles, vous pouvez supprimer des tables dans votre base de données d’espace de travail modèle que vous n’avez plus besoin. La suppression d’une table n’affecte pas les données sources d’origine, mais uniquement les données que vous avez importées et que vous utilisiez. Vous ne pouvez pas annuler la suppression d'une table.  
  
### <a name="to-delete-a-table"></a>Pour supprimer une table  
  
-   Cliquez avec le bouton droit sur l’onglet situé au bas du générateur de modèles pour la table à supprimer, puis sélectionnez **Supprimer**.  
  
## <a name="considerations-when-deleting-tables"></a>Considérations à prendre en compte lors de la suppression de tables  
  
-   Lorsque vous supprimez une table, l'onglet tout entier sur lequel se trouvait la table est supprimé.  
  
-   Si des mesures étaient associées à cette table, la définition de la mesure est également supprimée.  
  
-   Si vous avez créé des colonnes calculées à l'aide de cette table, les colonnes de cette table sont également supprimées ; toutes les colonnes calculées dans d'autres tables qui utilisent les colonnes de la table supprimée affichent une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et colonnes &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)  
  
  
