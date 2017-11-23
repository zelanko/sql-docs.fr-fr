---
title: PropertyAttributesEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: PropertyAttributesEnum
helpviewer_keywords: PropertyAttributesEnum enumeration [ADO]
ms.assetid: 96a01955-a6b4-4cbf-9c73-52bcd1e9fb25
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 853e63dcd520ab45a26f98091a3e48a816350d0b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="propertyattributesenum"></a>PropertyAttributesEnum
Spécifie les attributs d’un [propriété](../../../ado/reference/ado-api/property-object-ado.md) objet.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adPropNotSupported**|0|Indique que la propriété n’est pas pris en charge par le fournisseur.|  
|**adPropRequired**|1|Indique que l’utilisateur doit spécifier une valeur pour cette propriété avant l’initialisation de la source de données.|  
|**adPropOptional**|2|Indique que l’utilisateur n’a pas besoin de spécifier une valeur pour cette propriété avant l’initialisation de la source de données.|  
|**adPropRead**|512|Indique que l’utilisateur peut lire la propriété.|  
|**adPropWrite**|1024|Indique que l’utilisateur peut définir la propriété.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
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
