---
title: IsolationLevelEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- IsolationLevelEnum
helpviewer_keywords:
- IsolationLevelEnum enumeration [ADO]
ms.assetid: 8e17a7bc-b8a3-4ae2-b6c9-ce088ad31fdf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 15ae2aac2851c496b6cac9e47d37fe5fa26b8e34
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918373"
---
# <a name="isolationlevelenum"></a>IsolationLevelEnum
Spécifie le niveau d’isolation des transactions pour un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adXactUnspecified**|-1|Indique que le fournisseur utilise un niveau d’isolation différent que le nombre spécifié, mais que le niveau ne peut pas être déterminé.|  
|**adXactChaos**|16|Indique que les modifications en attente de transactions d’isolation plus grande ne peuvent pas être remplacés.|  
|**adXactBrowse**|256|Indique qu’à partir d’une seule transaction vous pouvez visualiser les modifications non validées dans d’autres transactions.|  
|**adXactReadUncommitted**|256|Identique à **à adXactBrowse**.|  
|**adXactCursorStability**|4096|Indique qu’à partir d’une seule transaction vous pouvez visualiser les modifications dans d’autres transactions uniquement une fois qu’ils ont été validées.|  
|**adXactReadCommitted**|4096|Identique à **à adXactCursorStability**.|  
|**adXactRepeatableRead**|65536|Indique que vous ne voyez pas les modifications apportées dans d’autres transactions à partir d’une seule transaction, mais qu’une nouvelle requête peut récupérer les nouvelles **Recordset** objets.|  
|**adXactIsolated**|1048576|Indique que les transactions sont effectuées de manière isolée des autres transactions.|  
|**adXactSerializable**|1048576|Identique à **à adXactIsolated**.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.IsolationLevel.UNSPECIFIED|  
|AdoEnums.IsolationLevel.CHAOS|  
|AdoEnums.IsolationLevel.BROWSE|  
|AdoEnums.IsolationLevel.READUNCOMMITTED|  
|AdoEnums.IsolationLevel.CURSORSTABILITY|  
|AdoEnums.IsolationLevel.READCOMMITTED|  
|AdoEnums.IsolationLevel.REPEATABLEREAD|  
|AdoEnums.IsolationLevel.ISOLATED|  
|AdoEnums.IsolationLevel.SERIALIZABLE|  
  
## <a name="applies-to"></a>S'applique à  
 [IsolationLevel, propriété](../../../ado/reference/ado-api/isolationlevel-property.md)
