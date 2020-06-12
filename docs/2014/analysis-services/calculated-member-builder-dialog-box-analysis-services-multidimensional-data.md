---
title: Générateur de membres calculés, boîte de dialogue (Analysis Services-données multidimensionnelles) | Microsoft Docs
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
ms.openlocfilehash: 240e2f2471bf77c403119fd51278a975badc8358
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527683"
---
# <a name="calculated-member-builder-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Générateur de membres calculés (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Générateur de membres calculés** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour créer un membre calculé.  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Nom**|Tapez le nom du membre calculé.|  
|**Hiérarchie parente**|Sélectionnez la hiérarchie parente dans laquelle créer le membre calculé.|  
|**Membre parent**|Cette option est activée si vous sélectionnez une hiérarchie parente (différente de la dimension `Measures`) à plusieurs niveaux. Cliquez sur le bouton de sélection (**...**) pour sélectionner un membre parent. Le membre parent détermine l'emplacement du membre calculé dans la structure de dimension.|  
|**Expression**|Tapez l'expression MDX à utiliser.|  
|**Vérification**|Teste **** l'expression MDX définie dans **Expression**.|  
|**Métadonnées**|Affiche les métadonnées de l'objet actif [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qu'il est possible d'inclure dans l'expression MDX définie dans **Expression**.<br /><br /> Pour copier la syntaxe MDX de l’élément sélectionné, cliquez sur l’élément avec le bouton droit et sélectionnez **Copier**ou faites glisser l’élément sélectionné vers **Expression**.|  
|**Fonctions**|Affiche les fonctions MDX disponibles dans l'instance active [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . La liste des éléments est extraite de l'ensemble de lignes du schéma MDSCHEMA_FUNCTIONS.<br /><br /> Pour copier la syntaxe MDX de l’élément sélectionné, cliquez sur l’élément avec le bouton droit et sélectionnez **Copier**ou faites glisser l’élément sélectionné vers **Expression**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence MDX &#40;Multidimensional Expressions&#41;](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
