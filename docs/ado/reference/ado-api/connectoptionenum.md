---
title: ConnectOptionEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectOptionEnum
helpviewer_keywords:
- ConnectOptionEnum enumeration [ADO]
ms.assetid: bff07eeb-dee3-4e4e-9b2d-d56061ea744d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9df3fd695e9bf281133dabf436e5e8b5de7e0b1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646617"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Spécifie si le [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) méthode d’un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet doit retourner une fois la connexion est établie (synchrone) ou avant (de façon asynchrone).  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|Ouvre la connexion de façon asynchrone. Le [ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md) événement peut être utilisé pour déterminer quand la connexion est disponible.|  
|**adConnectUnspecified**|-1|Valeur par défaut. Ouvre la connexion de façon synchrone.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED|  
  
## <a name="applies-to"></a>S'applique à  
 [Open, méthode (objet Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)
