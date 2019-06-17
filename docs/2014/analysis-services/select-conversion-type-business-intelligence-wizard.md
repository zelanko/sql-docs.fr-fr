---
title: Sélectionnez le Type de Conversion (Assistant Business Intelligence) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.conversiontype.f1
ms.assetid: 2c664138-e8a1-4c47-8e7d-ee01c57e4692
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ab618eaa2d8d54b08e3d01fa238d19451084eff8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66069617"
---
# <a name="select-conversion-type-business-intelligence-wizard"></a>Sélectionner le type de conversion (Assistant Business Intelligence)
  La page **Sélectionner le type de conversion** permet de définir la relation entre les devises locales et celles des rapports pour des transactions stockées dans plusieurs devises. Une devise locale est une devise dans laquelle les transactions des mesures sélectionnées dans **Sélectionnez les mesures** sont stockées. Une devise de rapport est celle dans laquelle sont traduites les transactions sélectionnées dans la page **Sélectionnez les mesures** .  
  
> [!NOTE]  
>  Cette page ne s’affiche pas si l’Assistant Business Intelligence a été démarré à partir du Concepteur de dimensions ou en cliquant avec le bouton droit sur une dimension dans l’Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="options"></a>Options  
 **Plusieurs-à-plusieurs**  
 Permet de stocker les transactions en utilisant des devises locales. La fonctionnalité de conversion monétaire convertit ce type de transactions dans la devise pivot spécifiée dans la page **Définir les options de conversion monétaire** , puis dans une ou plusieurs devises pour les rapports.  
  
 Par exemple, la devise pivot peut correspondre à des dollars américains (USD) et la table de faits peut stocker les transactions en euros (EUR), en dollars australiens (AUD) et en pesos mexicains (MXN). Cette option convertit ces transactions de leur devise locale dans la devise pivot. Ensuite, les transactions converties sont de nouveau converties de la devise pivot dans les devises de rapport spécifiées. Résultat : les transactions peuvent être stockées dans les devises locales spécifiées et affichées soit dans la devise pivot indiquée, soit dans l'une des devises de rapport mentionnées à la page **Spécifier les devises pour les rapports** .  
  
 **Plusieurs-à-un**  
 Permet de stocker les transactions en utilisant des devises locales. La fonctionnalité de conversion monétaire convertit ce type de transactions dans la devise pivot spécifiée dans la page **Définir les options de conversion monétaire** . La devise pivot est la seule devise pour les rapports spécifiée.  
  
> [!NOTE]  
>  La page **Spécifier les devises pour les rapports** n’apparaît pas quand cette option est sélectionnée.  
  
 Par exemple, la devise pivot peut correspondre à des dollars américains (USD) et la table de faits peut stocker les transactions en euros (EUR), en dollars australiens (AUD) et en pesos mexicains (MXN). Cette option convertit ces transactions de leurs devises locales spécifiées dans la devise pivot. Résultat : les transactions peuvent être stockées dans les devises locales spécifiées et être affichées dans la devise pivot  mentionnée.  
  
 **Un-à-plusieurs**  
 Permet de stocker les transactions en utilisant la devise pivot spécifiée dans la page **Définir les options de conversion monétaire** , puis dans une ou plusieurs devises pour les rapports.  
  
> [!NOTE]  
>  La page **Définir le référencement pour les devises locales** n’apparaît pas quand cette option est sélectionnée.  
  
 Par exemple, la devise pivot peut correspondre à des dollars américains (USD) et la table de faits peut stocker les transactions en USD. Cette option convertit ces transactions de la devise pivot dans les devises de rapport spécifiées. Résultat : les transactions peuvent être stockées dans la devise pivot spécifiée et être affichées soit dans la devise pivot indiquée, soit dans l'une des devises de rapport mentionnées à la page **Spécifier les devises pour les rapports** .  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l'Assistant Business Intelligence](business-intelligence-wizard-f1-help.md)   
 [Concepteur de cube &#40;Analysis Services - données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Concepteur de dimensions &#40;Analysis Services - données multidimensionnelles&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
