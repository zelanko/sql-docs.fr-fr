---
title: "Afficher le code&#160;XML d&#39;un projet Analysis Services (SSDT) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projets [Analysis Services], affichage du XML"
ms.assetid: dd1a4bc6-57b5-47df-8619-09f921aa6351
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 14
---
# Afficher le code&#160;XML d&#39;un projet Analysis Services (SSDT)
  Si vous utilisez une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode projet, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crée une définition XML pour chaque objet dans le dossier du projet. Vous pouvez afficher le contenu du fichier XML pour chaque objet dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Vous pouvez également modifier le fichier XML directement. Toutefois, nous vous déconseillons de procéder ainsi, car certaines modifications peuvent rendre le fichier XML illisible dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
> [!NOTE]  
>  Vous ne pouvez pas afficher le code XML d'un projet complet. Cependant, vous pouvez afficher le code de chaque objet car il existe un fichier distinct pour chaque objet. La seule façon d’afficher le code d’un projet complet consiste à générer le projet et à examiner le code ASSL dans le fichier \<nom_projet>.asdatabase.  
  
### Pour afficher le code XML d'un objet  
  
1.  Ouvrez le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Cliquez avec le bouton droit sur l’objet dans l’Explorateur de solutions, puis cliquez sur **Afficher le code**.  
  
     Le code XML de l’objet s’affiche dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## Voir aussi  
 [Générer des projets Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)  
  
  