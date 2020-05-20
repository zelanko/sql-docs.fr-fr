---
title: CursorLocationEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorLocationEnum
helpviewer_keywords:
- CursorLocationEnum enumeration [ADO]
ms.assetid: acb255ff-1734-4b70-89bb-aef862b4c63b
author: rothja
ms.author: jroth
ms.openlocfilehash: 278f69e504ed4af7589b7e2be2c281e5de5957fa
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760175"
---
# <a name="cursorlocationenum"></a>CursorLocationEnum
Spécifie l’emplacement du service de curseur.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adUseClient**|3|Utilise des curseurs côté client fournis par une bibliothèque de curseurs locale. Les services de curseur locaux autorisent souvent de nombreuses fonctionnalités que les curseurs fournis par le pilote peuvent ne pas. l’utilisation de ce paramètre peut donc offrir un avantage en ce qui concerne les fonctionnalités qui seront activées. Pour la compatibilité descendante, le synonyme **adUseClientBatch** est également pris en charge.|  
|**adUseNone**|1|N’utilise pas les services de curseur. (Cette constante est obsolète et s’affiche uniquement pour des raisons de compatibilité descendante.)|  
|**adUseServer**|2|Par défaut. Utilise des curseurs fournis par le fournisseur de données ou le pilote. Ces curseurs sont parfois très flexibles et permettent de renforcer la sensibilité aux modifications apportées par d’autres personnes à la source de données. Toutefois, certaines fonctionnalités du [service de curseur Microsoft pour OLE DB](../../../ado/guide/data/the-microsoft-cursor-service-for-ole-db.md), telles que dissociées<br /><br /> Les objets [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) ne peuvent pas être simulés avec des curseurs côté serveur et ces fonctionnalités ne seront pas disponibles avec ce paramètre.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums. CursorLocation. CLIENT|  
|AdoEnums.CursorLocation.NONE|  
|AdoEnums.CursorLocation.SERVER|  
  
## <a name="applies-to"></a>S'applique à  
 [CursorLocation, propriété (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)
