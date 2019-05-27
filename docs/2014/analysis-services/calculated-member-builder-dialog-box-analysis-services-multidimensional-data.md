---
title: Calculé la boîte de dialogue Générateur de membres (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.calculatedmemberbuilderdialog.f1
ms.assetid: 73b89a9f-f403-4ab8-99f7-e3ceb870c260
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8046d93f28c6d7c61899bb5f9aa3598f834c0ab3
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66088381"
---
# <a name="calculated-member-builder-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Générateur de membres calculés (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Générateur de membres calculés** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour créer un membre calculé.  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Nom**|Tapez le nom du membre calculé.|  
|**Hiérarchie parente**|Sélectionnez la hiérarchie parente dans laquelle créer le membre calculé.|  
|**Membre parent**|Cette option est activée si vous sélectionnez une hiérarchie parente (différente de la dimension `Measures`) à plusieurs niveaux. Cliquez sur le bouton de sélection (**...** ) pour sélectionner un membre parent. Le membre parent détermine l'emplacement du membre calculé dans la structure de dimension.|  
|**Expression**|Tapez l'expression MDX à utiliser.|  
|**Vérifier**|Teste **Vérifier** l'expression MDX définie dans **Expression**.|  
|**Métadonnées**|Affiche les métadonnées de l'objet actif [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qu'il est possible d'inclure dans l'expression MDX définie dans **Expression**.<br /><br /> Pour copier la syntaxe MDX de l’élément sélectionné, cliquez sur l’élément avec le bouton droit et sélectionnez **Copier**ou faites glisser l’élément sélectionné vers **Expression**.|  
|**Fonctions**|Affiche les fonctions MDX disponibles dans l'instance active [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . La liste des éléments est extraite de l'ensemble de lignes du schéma MDSCHEMA_FUNCTIONS.<br /><br /> Pour copier la syntaxe MDX de l’élément sélectionné, cliquez sur l’élément avec le bouton droit et sélectionnez **Copier**ou faites glisser l’élément sélectionné vers **Expression**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les expressions multidimensionnelles &#40;MDX&#41;](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
