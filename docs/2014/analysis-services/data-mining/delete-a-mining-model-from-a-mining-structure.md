---
title: Supprimer un modèle d’exploration de données à partir d’une Structure d’exploration de données | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6c9aea1e3f6bc05891544a1435704707021293f4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152922"
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
  
-   [MODÈLE D’EXPLORATION DE DONNÉES DE LISTE &AMP;#40;DMX&AMP;#41;](/sql/dmx/drop-mining-model-dmx)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et procédures des modèles d’exploration de données](mining-model-tasks-and-how-tos.md)  
  
  
