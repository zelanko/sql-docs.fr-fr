---
title: Mot de passe, élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 99d7eabdd66e6c7f036389b4825c5926873367b2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37197739"
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
  
  
