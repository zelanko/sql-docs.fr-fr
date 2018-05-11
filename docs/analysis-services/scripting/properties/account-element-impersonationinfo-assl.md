---
title: Compte de l’élément (ImpersonationInfo) (ASSL) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c2ec7aac67cfbfc51d3677bd4175750a72cff4b5
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="account-element-impersonationinfo-assl"></a>Élément Account (ImpersonationInfo) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contient le nom du compte d’utilisateur pour le [ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md) type de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ImpersonationInfo  
   ...  
  <Account>...</Account>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Élément ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de la **compte** élément, ainsi que la valeur de la [mot de passe](../../../analysis-services/scripting/properties/password-element-assl.md) , sont utilisées à des fins d’emprunt d’identité si la valeur de la [ImpersonationMode](../../../analysis-services/scripting/properties/impersonationmode-element-assl.md) pour tout élément dérivé le **ImpersonationInfo** type de données est défini sur *ImpersonateAccount*.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément DataSourceImpersonationInfo &#40;ASSL&#41;](../../../analysis-services/scripting/properties/datasourceimpersonationinfo-element-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
