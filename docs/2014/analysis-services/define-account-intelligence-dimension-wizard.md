---
title: Définir l’intelligence comptable (Assistant Dimension) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.accountintelligencetypemapping.f1
ms.assetid: cbcff072-3a7e-4e98-858f-1b4265461561
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e7bbc2b890c61e2864aa727f42276f01c87e94a7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66082159"
---
# <a name="define-account-intelligence-dimension-wizard"></a>Définir l'intelligence comptable (Assistant Dimension)
  Utilisez la page **Définir l'intelligence comptable** pour faire correspondre les types de comptes définis dans l'instance [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] avec ceux définis dans l'attribut de dimension associé à l'attribut **Type de compte** de la dimension.  
  
> [!NOTE]  
>  Cette page s’affiche uniquement si vous avez sélectionné **Dimension standard** dans la page **Sélectionner le type de la dimension** et si vous avez mappé un attribut de dimension au type d’attribut **Type de compte** dans la page **Spécifier le type de la dimension** .  
  
## <a name="options"></a>Options  
 **Types de comptes de la table source**  
 Affiche les valeurs contenues dans l’attribut de dimension affecté au type d’attribut du **Type de compte** dans la page **Spécifier la clé et le type de la dimension** .  
  
 **Types de comptes intégrés**  
 Sélectionnez le type de compte défini dans l'instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui correspond aux types de comptes de la table source.  
  
 Le tableau ci-dessous répertorie les types de comptes définis dans une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Asset**|Valeur des biens possédés à un moment donné.|  
|**Balance**|Comptage d'une grandeur à un moment donné.|  
|**Dépensé**|Valeur des dépenses engagées.|  
|**Organigramme**|Comptage incrémental de biens.|  
|**Produits**|Valeur des biens reçus.|  
|**Pourra**|Valeur des biens dus à un moment donné.|  
|**Statistique**|Rapport calculé d'une grandeur, ou comptage d'une grandeur qu'il n'est pas possible d'agréger.|  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant Dimension](dimension-wizard-f1-help.md)   
 [Dimensions &#40;Analysis Services-données multidimensionnelles&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
