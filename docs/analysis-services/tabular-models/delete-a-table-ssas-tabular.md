---
title: Supprimer une Table (SSAS tabulaire) | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1d3437449a05b5e1f60083135e020171b3d1e916
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="delete-a-table-ssas-tabular"></a>Supprimer une table (SSAS Tabulaire)
  Dans le générateur de modèles, vous pouvez supprimer des tables dont vous n'avez plus besoin dans votre base de données model de l'espace de travail. La suppression d’une table n’affecte pas les données sources d’origine, mais uniquement les données que vous avez importées et que vous utilisiez. Vous ne pouvez pas annuler la suppression d'une table.  
  
### <a name="to-delete-a-table"></a>Pour supprimer une table  
  
-   Cliquez avec le bouton droit sur l’onglet situé au bas du générateur de modèles pour la table à supprimer, puis sélectionnez **Supprimer**.  
  
## <a name="considerations-when-deleting-tables"></a>Considérations à prendre en compte lors de la suppression de tables  
  
-   Lorsque vous supprimez une table, l'onglet tout entier sur lequel se trouvait la table est supprimé.  
  
-   Si des mesures étaient associées à cette table, la définition de la mesure est également supprimée.  
  
-   Si vous avez créé des colonnes calculées à l'aide de cette table, les colonnes de cette table sont également supprimées ; toutes les colonnes calculées dans d'autres tables qui utilisent les colonnes de la table supprimée affichent une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et colonnes &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)  
  
  

