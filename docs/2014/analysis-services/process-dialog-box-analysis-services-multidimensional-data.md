---
title: Boîte de dialogue traiter (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.processdialog.f1
ms.assetid: c065248c-9001-4f0c-928f-9c59eccb618b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 32411ff5b715e15fd52b832d8047d8382a603924
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66070746"
---
# <a name="process-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Traiter (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Traiter** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] et [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour traiter les objets [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Pour ouvrir la boîte de dialogue **Traiter** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] :  
  
-   cliquez avec le bouton droit sur un projet, un cube, une dimension ou une structure d’exploration de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans l’ **Explorateur de solutions** et sélectionnez **Traiter**;  
  
-   sélectionnez **Traiter** dans la barre d'outils de chaque page du **Cube Designer**ou du **Concepteur de dimensions**, ou dans les pages **Structure d'exploration de données** et **Modèles d'exploration de données** du **Concepteur de modèle d'exploration de données**;  
  
-   cliquez avec le bouton droit sur un modèle de la page **Modèles d’exploration de données** du **Concepteur de modèle d’exploration de données** et sélectionnez **Traiter l’exploration de données et tous les modèles** ou **Traiter le modèle**.  
  
 Pour ouvrir la boîte de dialogue **Traiter** de **SQL Server Management Studio** :  
  
-   cliquez avec le bouton droit sur une base de données, un cube, un groupe de mesures, une partition, une dimension ou une structure d’exploration de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans l’ **Explorateur d’objets** et sélectionnez **Traiter**.  
  
## <a name="options"></a>Options  
 **Liste d'objets**  
 Sélectionnez les objets [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à traiter, ainsi que les options et les paramètres à appliquer. Cette grille comporte les colonnes suivantes :  
  
 **Nom de l’objet**  
 Affiche le nom de l'objet à traiter. L'icône à gauche du nom indique le type de l'objet.  
  
 **Type**  
 Affiche le type de l'objet à traiter.  
  
 **Options de traitement**  
 Sélectionnez le type de traitement à effectuer sur l'objet sélectionné. Pour plus d’informations sur les options de traitement disponibles, consultez [traitement des objets de modèle multidimensionnel](multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 **Paramètres**  
 Affiche le lien hypertexte **Configurer** quand vous choisissez **Traitement incrémentiel** dans les **Options de traitement** des cubes, des groupes de mesures ou des partitions. Cliquez sur **Configurer** pour ouvrir la boîte de dialogue **Mise à jour incrémentielle** . Pour plus d’informations sur la boîte de dialogue **Mise à jour incrémentielle**, consultez [Boîte de dialogue Mise à jour incrémentielle &#40;Analysis Services - Données multidimensionnelles&#41;](incremental-update-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Remove**  
 Supprime les éléments sélectionnés de la **Liste d’objets**.  
  
 **Analyse d'impact**  
 Ouvre la boîte de dialogue **Analyse d’impact** et affiche les objets affectés par le traitement. Pour plus d’informations sur la boîte de dialogue **Analyse d’impact**, consultez [Boîte de dialogue Analyse d’impact &#40;Analysis Services - Données multidimensionnelles&#41;](impact-analysis-dialog-box-analysis-services-multidimensional-data.md).  
  
> [!NOTE]  
>  Cette option est désactivée quand l’option **Traiter les objets affectés** est sélectionnée dans la boîte de dialogue **Modifier les paramètres** .  
  
 **Modifier les paramètres**  
 Ouvre la boîte de dialogue **Modifier les paramètres** et permet de modifier les paramètres qui régissent le traitement des objets sélectionnés, notamment les paramètres de traitement par lot, d’écriture différée et des erreurs de clé de dimension. Pour plus d’informations sur la boîte de dialogue **Modifier les paramètres**, consultez [Boîte de dialogue Modifier les paramètres &#40;Analysis Services - Données multidimensionnelles&#41;](change-settings-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Exécuter**  
 Traite les objets.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Boîte de dialogue État d’avancement du traitement &#40;Analysis Services-données multidimensionnelles&#41;](process-progress-dialog-box-analysis-services-multidimensional-data.md)  
  
  
