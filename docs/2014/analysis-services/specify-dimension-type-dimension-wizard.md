---
title: Spécifiez le Type de Dimension (Assistant Dimension) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.bidimensionproperties.f1
ms.assetid: 3215282a-532d-4ff2-b721-286f088967fc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6de1b056942673d358cec4768c6854a6966d139e
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66068367"
---
# <a name="specify-dimension-type-dimension-wizard"></a>Spécifier le type de la dimension (Assistant Dimension)
  La page **Spécifier le type de la dimension** permet de définir le type de dimension et d'ajouter à la dimension des types d'attributs spéciaux associés au type de dimension sélectionné.  
  
> [!NOTE]  
>  Cette page s’affiche uniquement si vous avez sélectionné **Dimension standard** dans la page **Sélectionner le type de la dimension** .  
  
## <a name="options"></a>Options  
 **Type de dimension**  
 Sélectionnez le type de la dimension. Le tableau suivant répertorie les types de dimensions disponibles.  
  
|Value|Description|  
|-----------|-----------------|  
|**Comptes (Accounts)**|Les dimensions de compte contiennent des données et métadonnées qui représentent une liste de comptes.<br /><br /> Pour plus d’informations sur les dimensions de compte, consultez [Créer un compte Finance de la dimension de type parent-enfant](multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md).|  
|**BillOfMaterials**|Les dimensions de nomenclature sont des dimensions régulières dans lesquelles les données et métadonnées représentent des informations sur le stock ou la fabrication (par ex., listes de pièces pour des produits).<br /><br /> Pour plus d’informations sur les dimensions régulières, consultez [Types de dimensions](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Channel**|Les dimensions de canal sont des dimensions régulières dans lesquelles les données et métadonnées représentent des informations sur les canaux.<br /><br /> Pour plus d’informations sur les dimensions régulières, consultez [Types de dimensions](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Monétaire (Currency)**|Les dimensions de devise contiennent des données et métadonnées qui représentent des informations sur les devises.<br /><br /> Pour plus d’informations sur les dimensions de devise, consultez [Créer une dimension de type devise](multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).|  
|**Customers**|Les dimensions de client sont des dimensions régulières dans lesquelles les données et métadonnées représentent des informations sur les clients ou contacts.<br /><br /> Pour plus d’informations sur les dimensions régulières, consultez [Types de dimensions](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Geography**|Les dimensions de zone géographique sont des dimensions régulières dans lesquelles les données et métadonnées représentent des informations géographiques, telles que les villes et codes postaux.<br /><br /> Pour plus d’informations sur les dimensions régulières, consultez [Types de dimensions](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Organisation**|Les dimensions d'organisation sont des dimensions régulières dans lesquelles les données et métadonnées représentent des informations organisationnelles, telles que les employés et filiales.<br /><br /> Pour plus d’informations sur les dimensions régulières, consultez [Types de dimensions](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Produits**|Les dimensions de produit sont des dimensions régulières dans lesquelles les données et métadonnées représentent des informations sur les produits.<br /><br /> Pour plus d’informations sur les dimensions régulières, consultez [Types de dimensions](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Promotion**|Les dimensions de promotion sont des dimensions régulières dans lesquelles les données et métadonnées représentent des informations sur la promotion commerciale.<br /><br /> Pour plus d’informations sur les dimensions régulières, consultez [Types de dimensions](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Quantitative**|Les dimensions quantitatives sont des dimensions régulières dans lesquelles les données et métadonnées représentent des informations quantitatives.<br /><br /> Pour plus d’informations sur les dimensions régulières, consultez [Types de dimensions](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Tarifs**|Les dimensions de taux contiennent des données et métadonnées qui représentent des informations sur le taux de change et la conversion monétaire.|  
|**Regular**|Les dimensions régulières sont le type le plus fréquent utilisé dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].<br /><br /> Pour plus d’informations sur les dimensions régulières, consultez [Types de dimensions](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Scénario**|Les dimensions de scénario sont des dimensions régulières dans lesquelles les données et métadonnées représentent des informations sur la planification ou l'analyse stratégique.<br /><br /> Pour plus d’informations sur les dimensions régulières, consultez [Types de dimensions](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Time**|Les dimensions de temps contiennent des données et métadonnées relatives au temps.<br /><br /> Pour plus d’informations sur les dimensions de temps, consultez [Créer une dimension de type date](multidimensional-models/database-dimensions-create-a-date-type-dimension.md).|  
|**Utilitaire**|Les dimensions d'utilitaire sont des dimensions régulières dans lesquelles les données et métadonnées représentent des informations qui ne correspondent pas vraiment à un autre type de dimension.<br /><br /> Pour plus d’informations sur les dimensions régulières, consultez [Types de dimensions](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
  
## <a name="dimension-attributes-options"></a>Options d'attributs de dimension  
  
> [!NOTE]  
>  Les options de cette section sont uniquement disponibles si le **type de dimension** sélectionné est associé à des types d'attributs spéciaux. Tous les types de dimensions ne sont pas associés à des types d'attributs spéciaux.  
  
 **Include**  
 Permet d'inclure le type d'attribut dans la dimension.  
  
 **Type d’attribut**  
 Affiche le type d’attribut associé au **Type de dimension** sélectionné. Pour plus d’informations sur les types d’attributs, consultez [Élément Type &#40;DimensionAttribute&#41; &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/type-element-dimensionattribute-assl).  
  
 **Attribut de dimension**  
 Sélectionnez l’attribut de dimension auquel l’Assistant Dimension affectera le type d’attribut spécial indiqué dans le champ **Type d’attribut**.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide F1 de l’Assistant Dimension](dimension-wizard-f1-help.md)   
 [Dimensions &#40;Analysis Services - données multidimensionnelles&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
