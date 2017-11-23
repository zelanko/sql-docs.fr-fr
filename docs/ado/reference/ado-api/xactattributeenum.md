---
title: XactAttributeEnum | Documents Microsoft
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
f1_keywords: XactAttributeEnum
helpviewer_keywords: XactAttributeEnum enumeration [ADO]
ms.assetid: e7dcecd3-7dc7-445c-b922-f700c3067fbc
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5e04aa9490ee8fbaa81e17f3ef1f29a68dc6e370
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="xactattributeenum"></a>XactAttributeEnum
Spécifie les attributs de transaction d’un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adXactAbortRetaining**|262144|Exécute un abandons en conservant en appelant [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) pour démarrer automatiquement une nouvelle transaction. Tous les fournisseurs prennent en charge ce comportement.|  
|**adXactCommitRetaining**|131072|Effectue des validations de conservation en appelant [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) pour démarrer automatiquement une nouvelle transaction. Tous les fournisseurs prennent en charge ce comportement.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.XactAttribute.ABORTRETAINING|  
|AdoEnums.XactAttribute.COMMITRETAINING|  
  
## <a name="applies-to"></a>S'applique à  
 [Attributes, propriété (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
