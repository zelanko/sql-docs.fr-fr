---
title: IsolationLevelEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: IsolationLevelEnum
helpviewer_keywords: IsolationLevelEnum enumeration [ADO]
ms.assetid: 8e17a7bc-b8a3-4ae2-b6c9-ce088ad31fdf
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 81659537335129e820a5bc610e05fce2d2bca081
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="isolationlevelenum"></a>IsolationLevelEnum
Spécifie le niveau d’isolation des transactions pour un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**: adXactUnspecified**|-1|Indique que le fournisseur utilise un niveau d’isolation que le nombre spécifié, mais que le niveau ne peut pas être déterminé.|  
|**adXactChaos**|16|Indique que les modifications en attente de transactions mieux isolées ne peut pas être remplacée.|  
|**à adXactBrowse**|256|Indique qu’à partir d’une transaction vous pouvez visualiser les modifications non validées dans d’autres transactions.|  
|**valeur adXactReadUncommitted**|256|Identique à **à adXactBrowse**.|  
|**à adXactCursorStability**|4096|Indique que d’une transaction vous pouvez visualiser les modifications dans d’autres transactions uniquement une fois qu’ils ont été validées.|  
|**adXactReadCommitted**|4096|Identique à **à adXactCursorStability**.|  
|**adXactRepeatableRead**|65536|Indique qu’à partir d’une transaction vous ne pouvez pas voir les modifications apportées dans d’autres transactions, mais qu’une nouvelle requête peut extraire de nouveau **Recordset** objets.|  
|**à adXactIsolated**|1048576|Indique que les transactions sont effectuées de manière isolée des autres transactions.|  
|**adXactSerializable**|1048576|Identique à **à adXactIsolated**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
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
