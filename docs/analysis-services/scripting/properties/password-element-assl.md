---
title: Mot de passe, élément (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: cc5464e4530e00a0d12807cb0cef2c2e1aa22afa
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050667"
---
# <a name="password-element-assl"></a>Élément Password (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contient le mot de passe du compte d’utilisateur pour le [ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ImpersonationInfo  
   ...  
  <Password>...</Password>  
   ...  
</ImpersonationInfo>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de la **mot de passe** élément, ainsi que la valeur de la [compte](../../../analysis-services/scripting/properties/account-element-impersonationinfo-assl.md) élément, est utilisé à des fins d’emprunt d’identité si la valeur de la [ImpersonationMode](../../../analysis-services/scripting/properties/impersonationmode-element-assl.md) élément pour tout élément dérivé la **ImpersonationInfo** type de données est défini sur *ImpersonateAccount*.  
  
 Seuls les membres du rôle d’administrateur du serveur pour le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance peut fournir une valeur vide pour le **mot de passe** élément  
  
## <a name="see-also"></a>Voir aussi  
 [Élément DataSourceImpersonationInfo &#40;ASSL&#41;](../../../analysis-services/scripting/properties/datasourceimpersonationinfo-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
