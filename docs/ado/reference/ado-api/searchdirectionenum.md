---
title: SearchDirectionEnum | Documents Microsoft
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
f1_keywords: SearchDirectionEnum
helpviewer_keywords: SearchDirectionEnum enumeration [ADO]
ms.assetid: 81272ae3-2165-4f4e-adfe-9ede0368cb17
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f4d5e78b7f636c4fb6094a217a0b1249babe9b2f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="searchdirectionenum"></a>SearchDirectionEnum
Spécifie la direction de la recherche d’un enregistrement dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adSearchBackward**|-1|Recherche en arrière, l’arrêt au début de la **Recordset**. Si une correspondance est introuvable, le pointeur est positionné à [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md).|  
|**adSearchForward**|1|Recherche vers, jusqu'à la fin de la **Recordset**. Si une correspondance est introuvable, le pointeur est positionné à [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md).|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.SearchDirection.BACKWARD|  
|AdoEnums.SearchDirection.FORWARD|  
  
## <a name="applies-to"></a>S'applique à  
 [Find, méthode (ADO)](../../../ado/reference/ado-api/find-method-ado.md)
