---
title: "Importer à partir d’Analysis Services (SSAS tabulaire) | Documents Microsoft"
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
ms.assetid: b9a21b23-3a06-4ef8-bc06-9c79cdc54870
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 81cee939240fd9379f2c521443272ae478de6243
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="import-from-analysis-services-ssas-tabular"></a>Importer à partir d'Analysis Services (SSAS Tabulaire)
  Cette rubrique explique comment créer un nouveau projet de modèle tabulaire en important les métadonnées d'un modèle tabulaire existant à l'aide du modèle de projet Importer à partir du serveur dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="create-a-new-model-by-importing-metadata-from-an-existing-model-in-analysis-services"></a>Créer un modèle en important des métadonnées d'un modèle existant dans Analysis Services  
 Vous pouvez utiliser le modèle de projet d'importation à partir du serveur pour créer un projet de modèle tabulaire en copiant les métadonnées d'un modèle tabulaire existant sur un serveur Analysis Services. Le nouveau projet est créé avec les mêmes connexions à la source de données, tables, relations, mesures, KPI, rôles, hiérarchies, perspectives et partitions que le modèle à partir duquel il a été importé. Toutefois, les données ne sont pas copiées depuis le modèle existant vers le nouvel espace de travail du modèle. Une fois l'importation terminée et le nouveau projet de modèle créé, vous devez exécuter une commande Traiter tout pour charger les données des sources de données dans la nouvelle base de données model de l'espace de travail du projet.  
  
#### <a name="to-create-a-new-model-by-importing-metadata-from-an-existing-model"></a>Pour créer un modèle en important des métadonnées à partir d'un modèle existant  
  
1.  Dans le menu [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]Fichier **de** , cliquez sur **Nouveau**, puis sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet** , sous **Modèles installés**, cliquez sur **Business Intelligence**puis sur **Importer à partir du serveur**.  
  
3.  Pour le **Nom**, tapez un nom pour le projet, puis spécifiez un emplacement et le nom de la solution et cliquez sur **OK**.  
  
4.  Dans la boîte de dialogue **Importer à partir d'Analysis Services** , dans la zone **Nom du serveur**tapez le nom du serveur Analysis Services qui contient les métadonnées du modèle que vous souhaitez importer.  
  
5.  Dans **Nom de la base de données**, sélectionnez la base de données du modèle tabulaire qui contient les métadonnées du modèle que vous souhaitez importer, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de projet &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/project-properties-ssas-tabular.md)  
  
  

