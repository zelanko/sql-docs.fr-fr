---
title: Supprimer une Table (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 85d085472a8d904efb2b33b942ba9f0a67326fed
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66067252"
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
 [Tables et colonnes &#40;SSAS Tabulaire&#41;](tables-and-columns-ssas-tabular.md)  
  
  
