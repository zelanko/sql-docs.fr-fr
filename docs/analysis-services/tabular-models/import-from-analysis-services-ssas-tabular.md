---
title: Importer à partir d’Analysis Services | Documents Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b527e648912e7a7a6e11a1aea5d0c1d05d31486e
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="import-from-analysis-services"></a>Importer à partir d'Analysis Services 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Cet article décrit comment créer un nouveau projet de modèle tabulaire en important les métadonnées à partir d’un modèle tabulaire existant à l’aide de l’importation à partir du modèle de projet de serveur dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="create-a-new-model-by-importing-metadata-from-an-existing-model-in-analysis-services"></a>Créer un modèle en important des métadonnées d'un modèle existant dans Analysis Services  
 Vous pouvez utiliser le modèle de projet d'importation à partir du serveur pour créer un projet de modèle tabulaire en copiant les métadonnées d'un modèle tabulaire existant sur un serveur Analysis Services. Le nouveau projet est créé avec les mêmes connexions à la source de données, tables, relations, mesures, KPI, rôles, hiérarchies, perspectives et partitions que le modèle à partir duquel il a été importé. Toutefois, les données ne sont pas copiées depuis le modèle existant vers le nouvel espace de travail du modèle. Une fois l'importation terminée et le nouveau projet de modèle créé, vous devez exécuter une commande Traiter tout pour charger les données des sources de données dans la nouvelle base de données model de l'espace de travail du projet.  
  
#### <a name="to-create-a-new-model-by-importing-metadata-from-an-existing-model"></a>Pour créer un modèle en important des métadonnées à partir d'un modèle existant  
  
1.  Dans le menu [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]Fichier **de** , cliquez sur **Nouveau**, puis sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet** , sous **Modèles installés**, cliquez sur **Business Intelligence**puis sur **Importer à partir du serveur**.  
  
3.  Pour le **Nom**, tapez un nom pour le projet, puis spécifiez un emplacement et le nom de la solution et cliquez sur **OK**.  
  
4.  Dans la boîte de dialogue **Importer à partir d'Analysis Services** , dans la zone **Nom du serveur**tapez le nom du serveur Analysis Services qui contient les métadonnées du modèle que vous souhaitez importer.  
  
5.  Dans **Nom de la base de données**, sélectionnez la base de données du modèle tabulaire qui contient les métadonnées du modèle que vous souhaitez importer, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés d’un projet](../../analysis-services/tabular-models/project-properties-ssas-tabular.md)  
  
  
