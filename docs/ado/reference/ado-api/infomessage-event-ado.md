---
title: InfoMessage, événement (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::InfoMessage
- InfoMessage
helpviewer_keywords:
- InfoMessage event [ADO]
ms.assetid: 468c87dd-e3bc-4084-9941-94d10743d4e9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 25eef06b7e25538cb874d99af98aee95495b95ce
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932331"
---
# <a name="infomessage-event-ado"></a>InfoMessage, événement (ADO)
L’événement **InfoMessage** est appelé chaque fois qu’un avertissement se produit pendant une opération **ConnectionEvent** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pError*  
 Objet d' [erreur](../../../ado/reference/ado-api/error-object.md) . Ce paramètre contient toutes les erreurs retournées. Si plusieurs erreurs sont retournées, énumérez la collection **Errors** pour les Rechercher.  
  
 *adStatus*  
 Valeur d’état [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) . Si un avertissement se produit, *adStatus* est défini sur **adStatusOK** et *perror* contient l’avertissement.  
  
 Avant le retour de cet événement, définissez ce paramètre sur **adStatusUnwantedEvent** pour empêcher les notifications suivantes.  
  
 *pConnection*  
 Objet de [connexion](../../../ado/reference/ado-api/connection-object-ado.md) . Connexion pour laquelle l’avertissement s’est produit. Par exemple, des avertissements peuvent se produire lors de l’ouverture d’un objet de **connexion** ou de l’exécution d’une [commande](../../../ado/reference/ado-api/command-object-ado.md) sur une **connexion**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Résumé du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Connection, objet (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
