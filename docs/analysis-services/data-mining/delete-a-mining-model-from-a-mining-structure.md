---
title: "Supprimer un modèle d’exploration de données à partir d’une Structure d’exploration de données | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 363ac575844136dee04f9cf249253479e64836dd
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>supprimer un modèle d'exploration de données d'une structure d'exploration de données
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Vous pouvez supprimer les modèles d’exploration de données en utilisant le Concepteur d’exploration de données, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou des instructions DMX.  
  
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
  
-   [SUPPRIMER LES MODÈLES D’EXPLORATION DE DONNÉES &#40; DMX &#41;](../../dmx/drop-mining-model-dmx.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches liées aux modèles d’exploration de données et procédures](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
