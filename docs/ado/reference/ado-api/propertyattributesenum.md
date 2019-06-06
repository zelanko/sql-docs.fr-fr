---
title: PropertyAttributesEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PropertyAttributesEnum
helpviewer_keywords:
- PropertyAttributesEnum enumeration [ADO]
ms.assetid: 96a01955-a6b4-4cbf-9c73-52bcd1e9fb25
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 99acfb2507701f0e4b47aff5b0595b61fc45c425
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719139"
---
# <a name="propertyattributesenum"></a>PropertyAttributesEnum
Spécifie les attributs d’un [propriété](../../../ado/reference/ado-api/property-object-ado.md) objet.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adPropNotSupported**|0|Indique que la propriété n’est pas pris en charge par le fournisseur.|  
|**adPropRequired**|1|Indique que l’utilisateur doit spécifier une valeur pour cette propriété avant l’initialisation de la source de données.|  
|**adPropOptional**|2|Indique que l’utilisateur n’a pas besoin de spécifier une valeur pour cette propriété avant l’initialisation de la source de données.|  
|**adPropRead**|512|Indique que l’utilisateur peut lire la propriété.|  
|**adPropWrite**|1024|Indique que l’utilisateur peut définir la propriété.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.PropertyAttributes.NOTSUPPORTED|  
|AdoEnums.PropertyAttributes.REQUIRED|  
|AdoEnums.PropertyAttributes.OPTIONAL|  
|AdoEnums.PropertyAttributes.READ|  
|AdoEnums.PropertyAttributes.WRITE|  
  
## <a name="applies-to"></a>S'applique à  
 [Attributes, propriété (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
