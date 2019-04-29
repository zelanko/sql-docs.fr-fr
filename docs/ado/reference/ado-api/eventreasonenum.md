---
title: EventReasonEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EventReasonEnum
helpviewer_keywords:
- EventReasonEnum enumeration [ADO]
ms.assetid: 7d4a5496-ec2d-4936-b36a-7049a82be4b4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 743e36e379760cb2c148c5484bb7b49b08d1d27e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63070853"
---
# <a name="eventreasonenum"></a>EventReasonEnum
Spécifie la raison pour laquelle un événement se produise.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adRsnAddNew**|1|Une opération a ajouté un nouvel enregistrement.|  
|**adRsnClose**|9|Une opération a fermé le **Recordset**.|  
|**adRsnDelete**|2|Une opération a supprimé un enregistrement.|  
|**adRsnFirstChange**|11|Une opération effectuée la première modification à un enregistrement.|  
|**adRsnMove**|10|Une opération a déplacé le pointeur d’enregistrement au sein de la **Recordset**.|  
|**adRsnMoveFirst**|12|Une opération a déplacé le pointeur vers le premier enregistrement dans le **Recordset**.|  
|**adRsnMoveLast**|15|Une opération a déplacé le pointeur vers le dernier enregistrement dans le **Recordset**.|  
|**adRsnMoveNext**|13|Une opération a déplacé le pointeur vers l’enregistrement suivant dans le **Recordset**.|  
|**adRsnMovePrevious**|14|Une opération a déplacé le pointeur vers l’enregistrement précédent dans le **Recordset**.|  
|**adRsnRequery**|7|Une opération à nouveau interrogée le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).|  
|**adRsnResynch**|8|Une opération a resynchronisé les **Recordset** avec la base de données.|  
|**adRsnUndoAddNew**|5|Une opération a annulé l’ajout d’un nouvel enregistrement.|  
|**adRsnUndoDelete**|6|Une opération a annulé la suppression d’un enregistrement.|  
|**adRsnUndoUpdate**|4|Une opération a annulé la mise à jour d’un enregistrement.|  
|**adRsnUpdate**|3|Une opération de mise à jour un enregistrement existant.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.EventReason.ADDNEW|  
|AdoEnums.EventReason.CLOSE|  
|AdoEnums.EventReason.DELETE|  
|AdoEnums.EventReason.FIRSTCHANGE|  
|AdoEnums.EventReason.MOVE|  
|AdoEnums.EventReason.MOVEFIRST|  
|AdoEnums.EventReason.MOVELAST|  
|AdoEnums.EventReason.MOVENEXT|  
|AdoEnums.EventReason.MOVEPREVIOUS|  
|AdoEnums.EventReason.REQUERY|  
|AdoEnums.EventReason.RESYNCH|  
|AdoEnums.EventReason.UNDOADDNEW|  
|AdoEnums.EventReason.UNDODELETE|  
|AdoEnums.EventReason.UNDOUPDATE|  
|AdoEnums.EventReason.UPDATE|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[WillChangeRecord et RecordChangeComplete, événements (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[WillChangeRecordset et RecordsetChangeComplete, événements (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[WillMove et MoveComplete, événements (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)||
