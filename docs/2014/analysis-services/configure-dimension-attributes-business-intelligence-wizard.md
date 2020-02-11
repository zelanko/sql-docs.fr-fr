---
title: Configurer les attributs de la dimension (Assistant Business Intelligence) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.acctintelligence.selectattributes.f1
ms.assetid: 3d046e63-bcb1-4ab1-9c37-652463fa68c3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5fe43b53878744586c3d0d8ec5719d6241b0a302
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087447"
---
# <a name="configure-dimension-attributes-business-intelligence-wizard"></a>Configurer les attributs de la dimension (Assistant Business Intelligence)
  Utilisez la page **Configurer les attributs de la dimension** pour associer les attributs de dimensions aux types d'attributs qu'utilise [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pour identifier les attributs des dimensions de compte.  
  
## <a name="options"></a>Options  
 **Type de dimension**  
 Affiche le type de dimension sélectionné.  
  
> [!NOTE]  
>  Cette option n’est pas disponible, `Type` car la propriété de la dimension ne peut pas être remplacée par une valeur autre que *compte* pour les dimensions de compte.  
  
 **Attributs de dimensions**  
 Affiche les types d'attributs valides qui peuvent être associés aux attributs de dimension existants dans la dimension.  
  
 **Inclusion**  
 Activez une case à cocher pour inclure le type d'attribut correspondant dans la dimension.  
  
 **Type d’attribut**  
 Affiche les types d'attributs qui peuvent être associés aux attributs de dimension existants dans la dimension.  
  
 **Attribut de dimension**  
 Sélectionnez l'attribut de dimension qui doit être associé au type d'attribut correspondant.  
  
 **Définissez les mesures semi-additives en fonction du type de compte**  
 Sélectionnez cette option pour changer chaque mesure associée à cette dimension à agréger par type de compte.  
  
> [!NOTE]  
>  Cette option ne s'affiche pas si l'Assistant Business Intelligence a été démarré à partir du Concepteur de dimensions ou en cliquant avec le bouton droit sur une dimension dans l'Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant Business Intelligence](business-intelligence-wizard-f1-help.md)   
 [Concepteur de cube &#40;Analysis Services-données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Concepteur de dimensions &#40;Analysis Services-données multidimensionnelles&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
