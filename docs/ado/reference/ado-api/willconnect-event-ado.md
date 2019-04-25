---
title: WillConnect, événement (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- WillConnect
- Connection::WillConnect
helpviewer_keywords:
- WillConnect event [ADO]
ms.assetid: da561d58-eb58-446c-a4fd-1838c76073c0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22d30e389c61a66d417ad5baec99a8834a754047
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642519"
---
# <a name="willconnect-event-ado"></a>WillConnect, événement (ADO)
Le **WillConnect** événement est appelé avant le début d’une connexion.  
  
 **S’applique à :** [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
WillConnect ConnectionString, UserID, Password, Options, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ConnectionString*  
 Un **chaîne** qui contient des informations de connexion pour la connexion en attente.  
  
 *UserID*  
 Un **chaîne** qui contient un nom d’utilisateur pour la connexion en attente.  
  
 *Mot de passe*  
 Un **chaîne** qui contient un mot de passe pour la connexion en attente.  
  
 *Options*  
 Un **Long** valeur qui indique la manière dont le fournisseur doit évaluer le *ConnectionString*. Votre seule option est **adAsyncOpen**.  
  
 *adStatus*  
 Un [il ne](../../../ado/reference/ado-api/eventstatusenum.md) valeur d’état.  
  
 Lorsque cet événement est appelé, ce paramètre est défini sur **adStatusOK** par défaut. Il est défini sur **adStatusCantDeny** si l’événement ne peut pas demander l’annulation de l’opération en attente.  
  
 Avant le retour de cet événement, définissez ce paramètre sur **adStatusUnwantedEvent** pour éviter toute notification. Définissez ce paramètre sur **adStatusCancel** pour demander l’opération de connexion qui a provoqué l’annulation de cette notification.  
  
 *pConnection*  
 Le [connexion](../../../ado/reference/ado-api/connection-object-ado.md) de l’objet pour lequel cette notification d’événement s’applique. Modifications apportées aux paramètres de la **connexion** par le **WillConnect** Gestionnaire d’événements n’a aucun effet le **connexion**.  
  
## <a name="remarks"></a>Notes  
 Lorsque **WillConnect** est appelée, le *ConnectionString*, *UserID*, *mot de passe*, et *Options* paramètres sont définis sur les valeurs établies par l’opération qui a provoqué cet événement (la connexion en attente) et peut être modifiée avant le retour de l’événement. **WillConnect** peut retourner une demande d’annulation de la connexion en attente.  
  
 Lorsque cet événement est annulé, **ConnectComplete** sera appelé avec son *ne* paramètre défini sur **contraire**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)
