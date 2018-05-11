---
title: Afficher le code XML pour un projet (SSDT) Analysis Services | Documents Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 591689e5e17a52d0b5e36ed04650f9ce82e8af88
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="view-the-xml-for-an-analysis-services-project-ssdt"></a>Afficher le code XML d'un projet Analysis Services (SSDT)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Si vous utilisez une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode projet, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crée une définition XML pour chaque objet dans le dossier du projet. Vous pouvez afficher le contenu du fichier XML pour chaque objet dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Vous pouvez également modifier le fichier XML directement. Toutefois, nous vous déconseillons de procéder ainsi, car certaines modifications peuvent rendre le fichier XML illisible dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
> [!NOTE]  
>  Vous ne pouvez pas afficher le code XML d'un projet complet. Cependant, vous pouvez afficher le code de chaque objet car il existe un fichier distinct pour chaque objet. La seule façon d’afficher le code d’un projet complet consiste à générer le projet et afficher l’ASSL de code dans le \<nom du projet > fichier .asdatabase.  
  
### <a name="to-view-the-xml-code-for-an-object"></a>Pour afficher le code XML d'un objet  
  
1.  Ouvrez le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Cliquez avec le bouton droit sur l’objet dans l’Explorateur de solutions, puis cliquez sur **Afficher le code**.  
  
     Le code XML de l’objet s’affiche dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Générer des projets Analysis Services & #40 ; SSDT & #41 ;](../../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)  
  
  
