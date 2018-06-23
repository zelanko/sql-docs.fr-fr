---
title: Définir le référencement pour les devises locales (Assistant Business Intelligence) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.localcurrency.f1
ms.assetid: 74993b0d-dfca-476b-acba-d66c593680a5
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 10810e19ec00aa77a14cb5a21789dfee1f9ae09a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038933"
---
# <a name="define-local-currency-reference-business-intelligence-wizard"></a>Définir le référencement pour les devises locales (Assistant Business Intelligence)
  La page **Définir le référencement pour les devises locales** permet de définir les devises locales de la fonctionnalité de conversion de devise qui couvre les types de conversion plusieurs-à-plusieurs ou plusieurs-à-un définis dans la page **Sélectionner le type de conversion** . Une devise locale est une devise dans laquelle les transactions des mesures sélectionnées dans **Sélectionnez les mesures** sont stockées.  
  
> [!NOTE]  
>  Cette page ne s’affiche pas si l’Assistant Business Intelligence a été démarré à partir du Concepteur de dimensions ou en ayant cliqué avec le bouton droit sur une dimension dans l’Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Cette page ne s’affiche pas non plus si **Un-à-plusieurs** a été sélectionné dans la page **Sélectionner le type de conversion** .  
  
## <a name="options"></a>Options  
 **Identificateurs dans la table de faits**  
 Sélectionnez cette option pour définir un attribut qui fournit des identificateurs pour les devises locales dans une dimension de devise référencée par la table de faits qui contient les mesures sélectionnées dans la page **Sélectionnez les mesures** . (Une devise de dimension dans un dont `Type` est définie sur *devise*.)  
  
 Utilisez cette option lorsque la transaction elle-même détermine la devise locale de la transaction. Par exemple, dans la base de données [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] de l'exemple[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], le groupe de mesures Internet Sales (Ventes Internet) possède une relation de dimension régulière avec la dimension monétaire. La table de faits pour ce groupe de mesures contient une colonne clé étrangère qui fait référence aux identificateurs de devises dans la table de dimensions pour cette dimension.  
  
 **Dimension de devise et attribut de devise référencés par les données de faits**  
 Sélectionnez l'attribut de devise dans une dimension de devise dont les membres représentent des identificateurs de devises locales. (Un attribut de devise est un attribut dont `Type` est définie sur *devise*.)  
  
> [!NOTE]  
>  Cette option n’est pas disponible si l’option **Identificateurs dans la table de faits** n’est pas sélectionnée.  
  
 **Attributs de la table de dimension**  
 Sélectionnez cette option pour définir un attribut depuis une dimension associée au groupe de mesures qui contient des identificateurs de devises locales.  
  
 Utilisez cette option lorsque la relation entre une transaction et une autre entité commerciale, comme un emplacement, détermine la devise locale de la transaction. Par exemple, dans l'exemple [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] de base de données[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], le groupe de mesures Financial Reporting a une relation de dimension référencée avec la dimension monétaire via la dimension Organisation. À savoir, la table de faits du groupe de mesures Financial Reporting contient une colonne clé étrangère qui fait référence à des membres dans la table de la dimension Organisation. La table de dimensions pour la dimension Organization, à son tour, contient une colonne clé étrangère qui fait référence aux identificateurs de devises dans la table de dimensions pour la dimension Currency.  
  
 **Attribut de dimension qui référence la devise**  
 Sélectionnez l'attribut dans une dimension dont les membres font référence aux identificateurs de devises locales.  
  
> [!NOTE]  
>  Cette option n’est pas disponible si l’option **Attributs de la table de dimension** n’est pas sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide F1 l’Assistant Business Intelligence](business-intelligence-wizard-f1-help.md)   
 [Concepteur de cube &#40;Analysis Services - données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Concepteur de dimensions &#40;Analysis Services - données multidimensionnelles&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  