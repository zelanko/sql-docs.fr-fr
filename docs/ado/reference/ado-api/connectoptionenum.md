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
ms.openlocfilehash: 819fb89d7f8c43e76ba9260a72fafa68084bf880
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67933448"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Spécifie si la méthode [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) d’un objet [Connection](../../../ado/reference/ado-api/connection-object-ado.md) doit être retournée après l’établissement de la connexion (de façon synchrone) ou avant (de façon asynchrone).  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|Ouvre la connexion de manière asynchrone. L’événement [ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md) peut être utilisé pour déterminer quand la connexion est disponible.|  
|**adConnectUnspecified**|-1|Par défaut. Ouvre la connexion de façon synchrone.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED|  
  
## <a name="applies-to"></a>S'applique à  
 [Open, méthode (objet Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)
