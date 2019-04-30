---
title: ExecuteComplete, événement (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- ExecuteComplete event [ADO]
ms.assetid: 62470d42-e511-494c-bec4-ad4591734b7b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec656a49963eb02cb204d5be96d403726bba8c56
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63301330"
---
# <a name="executecomplete-event-ado"></a>ExecuteComplete, événement (ADO)
Le **ExecuteComplete** événement est appelé après l’exécution d’une commande est terminée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ExecuteComplete RecordsAffected, pError, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>Paramètres  
 *RecordsAffected*  
 Un **Long** valeur indiquant le nombre d’enregistrements affectés par la commande.  
  
 *pError*  
 Un [erreur](../../../ado/reference/ado-api/error-object.md) objet. Il décrit l’erreur qui s’est produite si la valeur de **ne** est **contraire**; sinon, elle n’est pas définie.  
  
 *adStatus*  
 Un [il ne](../../../ado/reference/ado-api/eventstatusenum.md) valeur d’état. Lorsque cet événement est appelé, ce paramètre est défini sur **adStatusOK** si l’opération qui a provoqué l’événement a réussi, ou à **contraire** si l’opération a échoué.  
  
 Avant le retour de cet événement, définissez ce paramètre sur **adStatusUnwantedEvent** pour éviter toute notification.  
  
 *pCommand*  
 Le [commande](../../../ado/reference/ado-api/command-object-ado.md) objet qui a été exécutée. Contient un **commande** même lors de l’appel de l’objet **Connection.Execute** ou **Recordset.Open** sans créer explicitement un **commande** , dans quels cas le **commande** objet est créé en interne par ADO.  
  
 *pRecordset*  
 Un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet qui est le résultat de la commande exécutée. Cela **Recordset** peut être vide. Vous devez détruire jamais cet objet de jeu d’enregistrements à partir de ce gestionnaire d’événements. Cela entraîne une Violation d’accès ADO tente d’accéder à un objet qui n’existe plus.  
  
 *pConnection*  
 Un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet. La connexion sur laquelle l’opération a été exécutée.  
  
## <a name="remarks"></a>Notes  
 Un **ExecuteComplete** événement peut se produire en raison du **connexion.** [Exécuter](../../../ado/reference/ado-api/execute-method-ado-connection.md), **commande.** [Exécuter](../../../ado/reference/ado-api/execute-method-ado-command.md), **Recordset.** [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md), **Recordset.** [Requery](../../../ado/reference/ado-api/requery-method.md), ou **Recordset.** [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md) méthodes.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)
