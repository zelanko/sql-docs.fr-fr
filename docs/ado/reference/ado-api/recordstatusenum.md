---
title: RecordStatusEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordStatusEnum
helpviewer_keywords:
- RecordStatusEnum enumeration [ADO]
ms.assetid: 506fdd70-4452-4e83-95d5-c94311988dfa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e91f82595c8e4f6fe07969960959a12464bf53a9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63033401"
---
# <a name="recordstatusenum"></a>RecordStatusEnum
Spécifie le [état](../../../ado/reference/ado-api/status-property-ado-recordset.md) d’un enregistrement en ce qui concerne les mises à jour par lots et d’autres opérations en bloc.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adRecCanceled**|0x100|Indique que l’enregistrement n'a pas été enregistré, car l’opération a été annulée.|  
|**adRecCantRelease**|0x400|Indique que le nouvel enregistrement n'a pas été enregistré car l’enregistrement existant a été verrouillé.|  
|**adRecConcurrencyViolation**|0x800|Indique que l’enregistrement n'a pas été enregistré, car l’accès concurrentiel optimiste était en cours d’utilisation.|  
|**adRecDBDeleted**|0x40000|Indique que l’enregistrement a déjà été supprimé de la source de données.|  
|**adRecDeleted**|0x4|Indique que l’enregistrement a été supprimé.|  
|**adRecIntegrityViolation**|0x1000|Indique que l’enregistrement n'a pas été enregistré, car l’utilisateur a violé les contraintes d’intégrité.|  
|**adRecInvalid**|0x10|Indique que l’enregistrement n'a pas été enregistré, car son signet n’est pas valide.|  
|**adRecMaxChangesExceeded**|0x2000|Indique que l’enregistrement n'a pas été enregistré, car il existait trop de modifications en attente.|  
|**adRecModified**|0x2|Indique que l’enregistrement a été modifié.|  
|**adRecMultipleChanges**|0x40|Indique que l’enregistrement n'a pas été enregistré, car elle aurait affecté plusieurs enregistrements.|  
|**adRecNew**|0x1|Indique que l’enregistrement est nouveau.|  
|**adRecObjectOpen**|0x4000|Indique que l’enregistrement n’a pas été enregistré en raison d’un conflit avec un objet de stockage ouvert.|  
|**adRecOK**|0|Indique que l’enregistrement a été correctement mis à jour.|  
|**adRecOutOfMemory**|0x8000|Indique que l’enregistrement n'a pas été enregistré, car l’ordinateur a suffisamment de mémoire.|  
|**adRecPendingChanges**|0x80|Indique que l’enregistrement n'a pas été enregistré, car il fait référence à une insertion en attente.|  
|**adRecPermissionDenied**|0x10000|Indique que l’enregistrement n'a pas été enregistré, car l’utilisateur dispose d’autorisations insuffisantes.|  
|**adRecSchemaViolation**|0x20000|Indique que l’enregistrement n'a pas été enregistrée car elle ne respecte pas la structure de la base de données sous-jacente.|  
|**adRecUnmodified**|0x8|Indique que l’enregistrement n’a pas été modifié.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 AdoEnums.RecordStatus.  
  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.RecordStatus.CANCELED|  
|AdoEnums.RecordStatus.CANTRELEASE|  
|AdoEnums.RecordStatus.CONCURRENCYVIOLATION|  
|AdoEnums.RecordStatus.DBDELETED|  
|AdoEnums.RecordStatus.DELETED|  
|AdoEnums.RecordStatus.INTEGRITYVIOLATION|  
|AdoEnums.RecordStatus.INVALID|  
|AdoEnums.RecordStatus.MAXCHANGESEXCEEDED|  
|AdoEnums.RecordStatus.MODIFIED|  
|AdoEnums.RecordStatus.MULTIPLECHANGES|  
|AdoEnums.RecordStatus.NEW|  
|AdoEnums.RecordStatus.OBJECTOPEN|  
|AdoEnums.RecordStatus.OK|  
|AdoEnums.RecordStatus.OUTOFMEMORY|  
|AdoEnums.RecordStatus.PENDINGCHANGES|  
|AdoEnums.RecordStatus.PERMISSIONDENIED|  
|AdoEnums.RecordStatus.SCHEMAVIOLATION|  
|AdoEnums.RecordStatus.UNMODIFIED|  
  
## <a name="applies-to"></a>S'applique à  
 [Status, propriété (objet Recordset ADO)](../../../ado/reference/ado-api/status-property-ado-recordset.md)
