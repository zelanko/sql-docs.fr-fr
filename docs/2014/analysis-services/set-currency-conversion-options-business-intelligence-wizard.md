---
title: Définir les options de conversion monétaire (Assistant Business Intelligence) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.calculationsettings.f1
ms.assetid: a49d4e1f-bdda-4a83-ab4f-ce8c500e1d6d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 998a40b507c92e3c57bb4a10ceab9f597b8156e2
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940560"
---
# <a name="set-currency-conversion-options-business-intelligence-wizard"></a>Définir les options de conversion monétaire (Assistant Business Intelligence)
  La page **Définir les options de conversion monétaire** permet de définir les calculs relatifs à la conversion monétaire pour un groupe de mesures contenant des taux de change.  
  
> [!NOTE]  
>  Cette page ne s’affiche pas si l’Assistant Business Intelligence a été démarré à partir du Concepteur de dimensions ou en cliquant avec le bouton droit sur une dimension dans l’Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="options"></a>Options  
 **Sélectionnez le groupe de mesures qui contient le taux de change**  
 Groupe de mesures contenant les taux de change que les calculs de conversion monétaire utilisent comme point de référence.  
  
 **Spécifiez la devise pivot**  
 Membre servant de devise pivot pour le groupe de mesures.  
  
 **Comment avez-vous entré vos taux de change (autrement dit, sélectionnez une devise d'exemple)**  
 Permet de sélectionner un membre représentant une devise exemple tirée de la dimension monétaire afin de changer le texte relatif à la parité de X unités de la devise pivot pour 1 unité de devise d'exemple, ainsi que la parité de X unités de la devise d'exemple pour 1 unité de la devise pivot, afin de mieux afficher le sens des taux de change.  
  
 **Devise pivot X par 1 devise d'exemple**  
 Permet d'indiquer que les taux de change dans le groupe de mesures des taux représentent un multiplicateur de la devise pivot spécifiée.  
  
 **Devise d'exemple X par 1 devise pivot**  
 Permet d'indiquer que les taux de change dans le groupe de mesures des taux représentent un multiplicateur de la devise d'exemple spécifiée.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant Business Intelligence](business-intelligence-wizard-f1-help.md)   
 [Concepteur de cube &#40;Analysis Services-données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Concepteur de dimensions &#40;Analysis Services-données multidimensionnelles&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
