---
title: Supprimer un modèle d’exploration de données d’une structure d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7d4e32a40946eb9e513ad22cd837773187843151
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66084782"
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>supprimer un modèle d'exploration de données d'une structure d'exploration de données
  Vous pouvez supprimer les modèles d’exploration de données en utilisant le Concepteur d’exploration de données, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ou des instructions DMX.  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a>Supprimer un modèle d'exploration de données à l'aide de des outils de données SQL Server  
  
1.  Sélectionnez l’onglet **Modèles d’exploration de données** dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Cliquez avec le bouton droit sur le modèle à supprimer, puis sélectionnez **Supprimer**.  
  
     La boîte de dialogue **Supprimer les objets** s’ouvre.  
  
3.  Cliquez sur **OK**.  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a>Supprimer un modèle d'exploration de données à l'aide de SQL Server Management Studio  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contient le modèle.  
  
2.  Développez **Structures d’exploration de données**, puis développez **Modèles d’exploration de données**.  
  
3.  Cliquez avec le bouton droit sur le modèle à supprimer, puis sélectionnez **Supprimer**.  
  
     La suppression du modèle ne supprime pas les données d'apprentissage, seuls les métadonnées et les schémas créés lorsque vous avez formé le modèle sont supprimés.  
  
### <a name="delete-a-mining-model-using-dmx"></a>Supprimer un modèle d'exploration de données à l'aide de DMX  
  
-   [DROP MINING MODEL &#40;DMX&#41;](/sql/dmx/drop-mining-model-dmx)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches du modèle d'exploration de données et procédures](mining-model-tasks-and-how-tos.md)  
  
  
