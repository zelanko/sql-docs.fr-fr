---
title: ConnectComplete et Disconnect, événements (ADO) | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 268f9bb86667b94437ea2745753a823b4fdb9dbe
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="connectcomplete-and-disconnect-events-ado"></a>ConnectComplete et Disconnect, événements (ADO)
Le **ConnectComplete** événement est appelé après le début d’une connexion. Le **déconnexion** événement est appelé après la fin d’une connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ConnectComplete pError, adStatus, pConnection  
Disconnect adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pError*  
 Un [erreur](../../../ado/reference/ado-api/error-object.md) objet. Elle décrit l’erreur qui s’est produite si la valeur de *ne* est **contraire**; sinon, elle n’est pas définie.  
  
 *adStatus*  
 Un [il ne](../../../ado/reference/ado-api/eventstatusenum.md) retourne toujours la valeur **adStatusOK**.  
  
 Lorsque **ConnectComplete** est appelée, ce paramètre est défini sur **adStatusCancel** si un **WillConnect** événement a demandé l’annulation de la connexion en attente.  
  
 Avant le retour de l’événement, définissez ce paramètre sur **adStatusUnwantedEvent** pour éviter toute notification. Toutefois, fermer et rouvrir le [connexion](../../../ado/reference/ado-api/connection-object-ado.md) , ces événements se produisent à nouveau.  
  
 *pConnection*  
 Le **connexion** de l’objet pour lequel cet événement s’applique.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)
