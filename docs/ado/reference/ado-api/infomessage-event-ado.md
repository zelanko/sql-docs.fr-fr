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
manager: craigg
ms.openlocfilehash: 516e6a95ba98f1b8d66ddf9f417460ef2a6b7dc0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028026"
---
# <a name="infomessage-event-ado"></a>InfoMessage, événement (ADO)
Le **InfoMessage** événement est appelé chaque fois qu’un avertissement se produit pendant une **ConnectionEvent** opération.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pError*  
 Un [erreur](../../../ado/reference/ado-api/error-object.md) objet. Ce paramètre contient les erreurs qui sont retournées. Si plusieurs erreurs sont retournées, énumérez les **erreurs** collection pour les rechercher.  
  
 *adStatus*  
 Un [il ne](../../../ado/reference/ado-api/eventstatusenum.md) valeur d’état. Si un avertissement se produit, *ne* a la valeur **adStatusOK** et *pError* contient l’avertissement.  
  
 Avant le retour de cet événement, définissez ce paramètre sur **adStatusUnwantedEvent** pour éviter toute notification.  
  
 *pConnection*  
 Un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet. La connexion pour laquelle l’avertissement se produit. Par exemple, des avertissements peuvent se produire lorsque vous ouvrez un **connexion** objet ou l’exécution un [commande](../../../ado/reference/ado-api/command-object-ado.md) sur un **connexion**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Résumé du Gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)
