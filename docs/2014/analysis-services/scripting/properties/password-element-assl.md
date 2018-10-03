---
title: Mot de passe, élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Password Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Password element
ms.assetid: ee756b01-fb08-4a9a-8c2a-7c04af0f8658
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fcaf2b19e885577559d00337349d77cb8f732fcb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224789"
---
# <a name="password-element-assl"></a>Élément Password (ASSL)
  Contient le mot de passe du compte d’utilisateur pour le [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md) élément.  
  
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
|Élément parent|[ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de la `Password` élément, ainsi que la valeur de la [compte](account-element-impersonationinfo-assl.md) élément, est utilisé à des fins d’emprunt d’identité si la valeur de la [ImpersonationMode](impersonationmode-element-assl.md) élément pour tout élément dérivé de la `ImpersonationInfo` type de données est défini sur *ImpersonateAccount*.  
  
 Seuls les membres du rôle des administrateurs de serveur de l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] peuvent fournir une valeur vide pour l'élément `Password`  
  
## <a name="see-also"></a>Voir aussi  
 [Élément DataSourceImpersonationInfo &#40;ASSL&#41;](impersonationinfo-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
