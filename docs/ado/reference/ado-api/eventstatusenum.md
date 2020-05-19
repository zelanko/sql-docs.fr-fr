---
title: EventStatusEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EventStatusEnum
helpviewer_keywords:
- EventStatusEnum enumeration [ADO]
ms.assetid: ebfd4cda-4017-4873-9d28-38b1c7db12a8
author: rothja
ms.author: jroth
ms.openlocfilehash: 1abce457e64c7f6865f94b85473fbc589e5ffb4f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82755150"
---
# <a name="eventstatusenum"></a>EventStatusEnum
Spécifie l’état actuel de l’exécution d’un événement.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adStatusCancel**|4|Demande l’annulation de l’opération qui a provoqué l’événement.|  
|**adStatusCantDeny**|3|Indique que l’opération ne peut pas demander l’annulation de l’opération en attente.|  
|**adStatusErrorsOccurred**|2|Indique que l’opération à l’origine de l’événement a échoué en raison d’une erreur ou d’erreurs.|  
|**adStatusOK**|1|Indique que l’opération qui a provoqué l’événement a réussi.|  
|**adStatusUnwantedEvent**|5|Empêche les notifications suivantes avant la fin de l’exécution de la méthode d’événement.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.EventStatus.CANCEL|  
|AdoEnums.EventStatus.CANTDENY|  
|AdoEnums.EventStatus.ERRORSOCCURRED|  
|AdoEnums.EventStatus.OK|  
|AdoEnums.EventStatus.UNWANTEDEVENT|  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Événements BeginTransComplete, CommitTransComplete et RollbackTransComplete (ADO)](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|[ConnectComplete et Disconnect, événements (ADO)](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|[EndOfRecordset, événement (ADO)](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|  
|[ExecuteComplete, événement (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)|[FetchComplete, événement (ADO)](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|[InfoMessage, événement (ADO)](../../../ado/reference/ado-api/infomessage-event-ado.md)|  
|[WillChangeField et FieldChangeComplete, événements (ADO)](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|[WillChangeRecord et RecordChangeComplete, événements (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[WillChangeRecordset et RecordsetChangeComplete, événements (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[WillConnect, événement (ADO)](../../../ado/reference/ado-api/willconnect-event-ado.md)|[WillExecute, événement (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|[WillMove et MoveComplete, événements (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|
