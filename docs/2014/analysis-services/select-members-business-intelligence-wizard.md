---
title: Sélectionner les membres (Assistant Business Intelligence) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.memberconversion.f1
ms.assetid: 1a147461-d594-41e7-a41d-09d2d003e1e0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2d15a32302aa5d7a4ee3ca087944effc017ce8c1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105142"
---
# <a name="select-members-business-intelligence-wizard"></a>Sélectionner les membres (Assistant Business Intelligence)
  Utilisez la page **Sélectionner les membres** pour déterminer à quels membres l'Assistant Business Intelligence doit appliquer la fonction de conversion monétaire spécifiée à la page **Définir les options de conversion monétaire** .  
  
> [!NOTE]  
>  Cette page ne s’affiche pas si l’Assistant Business Intelligence a été démarré à partir du Concepteur de dimensions ou en cliquant avec le bouton droit sur une dimension dans l’Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="options"></a>Options  
 **Dimension de mesures**  
 Sélectionnez cette option afin d'appliquer la fonctionnalité de conversion monétaire à une ou plusieurs mesures du cube.  
  
 Une fois cette option sélectionnée, la grille affiche les options répertoriées dans le tableau suivant.  
  
|Option|Description|  
|------------|-----------------|  
|**Types de mesure intégrés**|Sélectionnez cette option afin d'inclure la fonctionnalité de conversion monétaire pour la mesure spécifiée.|  
|**Mesures**|Sélectionnez la mesure dans le groupe de mesures de taux qui contient le taux de change à utiliser lors de la conversion de la mesure sélectionnée à la section **Types de mesures intégrés** .|  
  
 **Hiérarchie de compte**  
 Sélectionnez cette option afin d'appliquer la fonctionnalité de conversion monétaire à un ou plusieurs membres dans la hiérarchie de comptes de la dimension incluse dans le cube. La hiérarchie de compte est la hiérarchie dans le compte de dimension dont la propriété `Type` propriété est définie sur *compte*.  
  
 Une fois cette option sélectionnée, la grille affiche les options répertoriées dans le tableau suivant.  
  
|Option|Description|  
|------------|-----------------|  
|**Membre du compte**|Sélectionnez cette option afin d'inclure la fonctionnalité de conversion monétaire pour le membre spécifié de la hiérarchie de comptes.|  
|**Mesures**|Sélectionnez la mesure dans le groupe de mesures Taux qui contient le taux de change à utiliser lors de la conversion des mesures relatives au membre choisi dans **Membre du compte** .|  
  
 **Selon le type de hiérarchie de compte**  
 Sélectionnez cette option pour appliquer la fonctionnalité de conversion monétaire à tous les membres des attributs dans la hiérarchie de comptes dont `Type` propriété est définie sur un type de compte spécifié.  
  
 Une fois cette option sélectionnée, la grille affiche les options répertoriées dans le tableau suivant.  
  
|Option|Description|  
|------------|-----------------|  
|**Type de compte**|Sélectionnez cette option afin d'inclure la fonctionnalité de conversion monétaire pour le type de compte spécifié.|  
|**Mesures**|Sélectionnez la mesure dans le groupe de mesures Taux qui contient le taux de change à utiliser lors de la conversion des mesures relatives aux membres d'attributs dont le type de compte correspond à celui indiqué dans **Type de compte** .|  
  
## <a name="see-also"></a>Voir aussi  
 [L’Assistant Business Intelligence F1](business-intelligence-wizard-f1-help.md)   
 [Concepteur de cube &#40;Analysis Services - données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Concepteur de dimensions &#40;Analysis Services - données multidimensionnelles&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
