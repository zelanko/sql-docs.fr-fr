---
title: Définir la Conversion monétaire (Assistant Business Intelligence) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.existingscriptpage.f1
ms.assetid: 37dd65b7-9d8d-44ad-b316-96a92c622472
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e7cca289615e94cd4ccfbcee038e002c33700be8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099239"
---
# <a name="define-currency-conversion-business-intelligence-wizard"></a>Définir la conversion monétaire (Assistant Business Intelligence)
  La page **Définir la conversion monétaire** permet d’examiner le script MDX (Multidimensional Expressions) qui contient la fonctionnalité de conversion monétaire générée par l’Assistant Business Intelligence. Vous pouvez utiliser ce script MDX généré par l'Assistant pour remplacer ou pour ajouter la fonctionnalité de conversion monétaire précédemment définie dans le script MDX du cube.  
  
> [!NOTE]  
>  Cette page apparaît uniquement si l'Assistant Business Intelligence détecte au moins une conversion monétaire précédemment définie dans le script MDX du cube. Dans le script MDX d'un cube, les conversions monétaires sont accompagnées des commentaires suivants :  
>   
>  `//<Currency conversion>`  
>   
>  `...`  
>   
>  `[MDX statements for the currency conversion]`  
>   
>  `...`  
>   
>  `//</Currency conversion>`  
>   
>  Si vous modifiez ou supprimez ces commentaires, il se peut que l'Assistant Business Intelligence ne soit pas en mesure de détecter les conversions monétaires précédemment définies.  
  
## <a name="options"></a>Options  
 **Nouveau script de conversion monétaire**  
 Affiche le script MDX généré par la session actuelle de l'Assistant Business Intelligence.  
  
 **Remplacer le script de conversion monétaire existant**  
 Remplace le script MDX affiché dans le champ **Script de conversion monétaire existant** par celui affiché dans le champ **Nouveau script de conversion monétaire**.  
  
 **Ajouter après**  
 Ajoute le script MDX affiché dans le champ **Nouveau script de conversion monétaire** à la fin de celui affiché dans le champ **Script de conversion monétaire existant**. Le script ajouté apparaît dans une nouvelle section.  
  
 **Script de conversion monétaire existant**  
 Sélectionne la section du script MDX existant qui contient la fonctionnalité de conversion monétaire précédemment définie à remplacer ou ajouter.  
  
## <a name="see-also"></a>Voir aussi  
 [L’Assistant Business Intelligence F1](business-intelligence-wizard-f1-help.md)   
 [Concepteur de cube &#40;Analysis Services - données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Concepteur de dimensions &#40;Analysis Services - données multidimensionnelles&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
