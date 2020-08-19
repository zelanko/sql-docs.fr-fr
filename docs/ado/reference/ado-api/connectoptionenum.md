---
description: ConnectOptionEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 71142aac94003987267a6d4a6b30d2c9d17c1bfd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444421"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Spécifie si la méthode [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) d’un objet [Connection](../../../ado/reference/ado-api/connection-object-ado.md) doit être retournée après l’établissement de la connexion (de façon synchrone) ou avant (de façon asynchrone).  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|Ouvre la connexion de manière asynchrone. L’événement [ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md) peut être utilisé pour déterminer quand la connexion est disponible.|  
|**adConnectUnspecified**|-1|Par défaut. Ouvre la connexion de façon synchrone.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constante|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED|  
  
## <a name="applies-to"></a>S'applique à  
 [Open, méthode (objet Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)
