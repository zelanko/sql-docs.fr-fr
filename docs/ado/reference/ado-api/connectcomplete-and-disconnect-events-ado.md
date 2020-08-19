---
description: ConnectComplete et Disconnect, événements (ADO)
title: ConnectComplete et Disconnect, événements (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Disconnect
- Connection::ConnectComplete
- ConnectComplete
- Connection::Disconnect
helpviewer_keywords:
- Disconnect event [ADO]
- ConnectComplete event [ADO]
ms.assetid: 568f5252-d069-4d99-a01b-2ada87ad1304
author: rothja
ms.author: jroth
ms.openlocfilehash: db04bbeed12f9097768763024270ece7275d5c3e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444541"
---
# <a name="connectcomplete-and-disconnect-events-ado"></a>ConnectComplete et Disconnect, événements (ADO)
L’événement **ConnectComplete** est appelé après le démarrage d’une connexion. L’événement **Disconnect** est appelé après la fin d’une connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ConnectComplete pError, adStatus, pConnection  
Disconnect adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pError*  
 Objet d' [erreur](../../../ado/reference/ado-api/error-object.md) . Il décrit l’erreur qui s’est produite si la valeur de *adStatus* est **adStatusErrorsOccurred**; dans le cas contraire, il n’est pas défini.  
  
 *adStatus*  
 Valeur [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) qui retourne toujours **adStatusOK**.  
  
 Lorsque **ConnectComplete** est appelé, ce paramètre a la valeur **adStatusCancel** si un événement **WillConnect** a demandé l’annulation de la connexion en attente.  
  
 Avant que l’un des événements soit retourné, définissez ce paramètre sur **adStatusUnwantedEvent** pour empêcher les notifications suivantes. Toutefois, la fermeture et la réouverture de la [connexion](../../../ado/reference/ado-api/connection-object-ado.md) entraînent une nouvelle exécution de ces événements.  
  
 *pConnection*  
 Objet de **connexion** pour lequel cet événement s’applique.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)
