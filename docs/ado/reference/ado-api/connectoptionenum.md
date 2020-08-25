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
ms.openlocfilehash: 73fb0218b9a4a9437dbe8c103c8496f0a209e9b1
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775808"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Spécifie si la méthode [Open](./open-method-ado-connection.md) d’un objet [Connection](./connection-object-ado.md) doit être retournée après l’établissement de la connexion (de façon synchrone) ou avant (de façon asynchrone).  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|Ouvre la connexion de manière asynchrone. L’événement [ConnectComplete](./connectcomplete-and-disconnect-events-ado.md) peut être utilisé pour déterminer quand la connexion est disponible.|  
|**adConnectUnspecified**|-1|Par défaut. Ouvre la connexion de façon synchrone.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED|  
  
## <a name="applies-to"></a>S'applique à  
 [Open, méthode (objet Connection ADO)](./open-method-ado-connection.md)