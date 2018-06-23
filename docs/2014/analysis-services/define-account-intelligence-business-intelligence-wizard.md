---
title: Définir l’Intelligence comptable (Assistant Business Intelligence) | Documents Microsoft
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
- sql12.asvs.biwizard.acctintelligence.mapaccounttype.f1
ms.assetid: fe4c204b-1031-4ac4-9916-8052ce2301cc
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3b55d270b9b7ae2a2094c24e0f71bdcd0f72a0ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141911"
---
# <a name="define-account-intelligence-business-intelligence-wizard"></a>Définir l'intelligence comptable (Assistant Business Intelligence)
  Utilisez la page **Définir l'intelligence comptable** pour faire correspondre les types de comptes définis dans l'instance [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] avec ceux définis par une table source de la source de données qui fournit les données de dimension du compte.  
  
> [!NOTE]  
>  Cette page s’affiche si un attribut de dimension a été mis en correspondance avec le type d’attribut **Type de compte** dans la page **Configurer les attributs de la dimension** .  
  
## <a name="options"></a>Options  
 **Types de comptes de Table source**  
 Affiche les valeurs contenues dans l’attribut de dimension affecté au type d’attribut **Type de compte** défini dans la page **Configurer les attributs de la dimension** .  
  
 **Types de comptes intégrés**  
 Sélectionnez le type de compte défini dans l'instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui correspond aux types de comptes de la table source.  
  
 Le tableau ci-dessous répertorie les types de comptes définis dans une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Actif**|Valeur des biens possédés à un moment donné.|  
|**Balance**|Comptage d'une grandeur à un moment donné.|  
|**Dépenses**|Valeur des dépenses engagées.|  
|**Flux**|Comptage incrémental de biens.|  
|**Revenu**|Valeur des biens reçus.|  
|**Dettes**|Valeur des biens dus à un moment donné.|  
|**Statistique**|Rapport calculé d'une grandeur, ou comptage d'une grandeur qu'il n'est pas possible d'agréger.|  
  
## <a name="see-also"></a>Voir aussi  
 [Aide F1 l’Assistant Business Intelligence](business-intelligence-wizard-f1-help.md)   
 [Concepteur de cube &#40;Analysis Services - données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Concepteur de dimensions &#40;Analysis Services - données multidimensionnelles&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  