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
author: rothja
ms.author: jroth
ms.openlocfilehash: dcb17116d7332e9afb359a7dd47d69cb3eb75df4
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759935"
---
# <a name="propertyattributesenum"></a>PropertyAttributesEnum
Spécifie les attributs d’un objet de [propriété](../../../ado/reference/ado-api/property-object-ado.md) .  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adPropNotSupported**|0|Indique que la propriété n’est pas prise en charge par le fournisseur.|  
|**adPropRequired**|1|Indique que l’utilisateur doit spécifier une valeur pour cette propriété avant que la source de données soit initialisée.|  
|**adPropOptional**|2|Indique que l’utilisateur n’a pas besoin de spécifier une valeur pour cette propriété avant que la source de données soit initialisée.|  
|**adPropRead**|512|Indique que l’utilisateur peut lire la propriété.|  
|**adPropWrite**|1 024|Indique que l’utilisateur peut définir la propriété.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.PropertyAttributes.NOTSUPPORTED|  
|AdoEnums. PropertyAttributes. obligatoire|  
|AdoEnums.PropertyAttributes.OPTIONAL|  
|AdoEnums. PropertyAttributes. READ|  
|AdoEnums.PropertyAttributes.WRITE|  
  
## <a name="applies-to"></a>S'applique à  
 [Attributes, propriété (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
