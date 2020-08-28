---
description: ConnectOptionEnum
title: ConnectOptionEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: b924acf0f41ead3025197bade8bcc2d459508f2a
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974690"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Spécifie si la méthode [Open](./open-method-ado-connection.md) d’un objet [Connection](./connection-object-ado.md) doit être retournée après l’établissement de la connexion (de façon synchrone) ou avant (de façon asynchrone).  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|Ouvre la connexion de manière asynchrone. L’événement [ConnectComplete](./connectcomplete-and-disconnect-events-ado.md) peut être utilisé pour déterminer quand la connexion est disponible.|  
|**adConnectUnspecified**|-1|Par défaut. Ouvre la connexion de façon synchrone.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constante|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED|  
  
## <a name="applies-to"></a>S'applique à  
 [Open, méthode (objet Connection ADO)](./open-method-ado-connection.md)