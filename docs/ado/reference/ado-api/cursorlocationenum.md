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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 43c2043917d6b21293fea71566dfdf1202b6f59e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695652"
---
# <a name="cursorlocationenum"></a>CursorLocationEnum
Spécifie l’emplacement du service de curseur.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adUseClient**|3|Utilise des curseurs côté client fournis par une bibliothèque de curseurs locaux. Les services de curseur local souvent permettra nombreuses fonctionnalités que les curseurs de pilote fourni ne peuvent pas, donc à l’aide de ce paramètre peut fournir un avantage en ce qui concerne les fonctionnalités qui seront activées. Pour la compatibilité descendante, le synonyme **adUseClientBatch** est également pris en charge.|  
|**adUseNone**|1|N’utilisez pas les services de curseur. (Cette constante est obsolète et s’affiche uniquement pour des raisons de compatibilité descendante.)|  
|**adUseServer**|2|Valeur par défaut. Utilise des curseurs fournis par le fournisseur de données ou le pilote. Ces curseurs sont parfois très flexibles et autoriser plus facilement les modifications apportées à la source de données. Toutefois, certaines fonctionnalités de la [le Service de curseur Microsoft pour OLE DB](../../../ado/guide/data/the-microsoft-cursor-service-for-ole-db.md), telles que dissocié<br /><br /> [Jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md) objets, ne peuvent pas être simulés avec les curseurs côté serveur et de ces fonctionnalités ne seront pas disponibles avec ce paramètre.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.CursorLocation.CLIENT|  
|AdoEnums.CursorLocation.NONE|  
|AdoEnums.CursorLocation.SERVER|  
  
## <a name="applies-to"></a>S'applique à  
 [CursorLocation, propriété (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)
