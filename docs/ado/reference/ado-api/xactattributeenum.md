---
title: XactAttributeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- XactAttributeEnum
helpviewer_keywords:
- XactAttributeEnum enumeration [ADO]
ms.assetid: e7dcecd3-7dc7-445c-b922-f700c3067fbc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d828c2b9b49138cc4dfd6345d90e70c333554fe0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67947432"
---
# <a name="xactattributeenum"></a>XactAttributeEnum
Spécifie les attributs de transaction d’un objet de [connexion](../../../ado/reference/ado-api/connection-object-ado.md) .  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adXactAbortRetaining**|262 144|Effectue des abandons de rétention en appelant [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) pour démarrer automatiquement une nouvelle transaction. Tous les fournisseurs ne prennent pas en charge ce comportement.|  
|**adXactCommitRetaining**|131 072|Effectue la conservation des validations en appelant [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) pour démarrer automatiquement une nouvelle transaction. Tous les fournisseurs ne prennent pas en charge ce comportement.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.XactAttribute.ABORTRETAINING|  
|AdoEnums.XactAttribute.COMMITRETAINING|  
  
## <a name="applies-to"></a>S'applique à  
 [Attributes, propriété (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
