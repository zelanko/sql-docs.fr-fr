---
title: Élément (ImpersonationInfo) (ASSL) du compte | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Account Element (ImpersonationInfo)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Account element
ms.assetid: aa3a1281-e42a-4926-875b-e6b81f4599c3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f454e39a7c4ec4911f38ff070f94fcbe50a34c74
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190369"
---
# <a name="account-element-impersonationinfo-assl"></a>Élément Account (ImpersonationInfo) (ASSL)
  Contient le nom du compte d’utilisateur pour le [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md) type de données.  
  
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
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de la `Account` élément, ainsi que la valeur de la [mot de passe](password-element-assl.md) élément, est utilisé à des fins d’emprunt d’identité si la valeur de la [ImpersonationMode](impersonationmode-element-assl.md) élément pour tout élément dérivé de la `ImpersonationInfo` type de données est défini sur *ImpersonateAccount*.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément DataSourceImpersonationInfo &#40;ASSL&#41;](impersonationinfo-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
