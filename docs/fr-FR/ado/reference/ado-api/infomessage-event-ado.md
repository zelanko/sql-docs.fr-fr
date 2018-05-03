---
title: L’événement InfoMessage (ADO) | Documents Microsoft
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
- Connection::InfoMessage
- InfoMessage
helpviewer_keywords:
- InfoMessage event [ADO]
ms.assetid: 468c87dd-e3bc-4084-9941-94d10743d4e9
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3216c9dfb31fdc7ac27051d409bbb6c658c2b091
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="infomessage-event-ado"></a>Événement InfoMessage (ADO)
Le **InfoMessage** événements sont appelé chaque fois qu’un avertissement se produit pendant une **ConnectionEvent** opération.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pError*  
 Un [erreur](../../../ado/reference/ado-api/error-object.md) objet. Ce paramètre contient toutes les erreurs qui sont retournées. Si plusieurs erreurs sont retournées, énumèrent les **erreurs** collection pour les retrouver.  
  
 *adStatus*  
 Un [il ne](../../../ado/reference/ado-api/eventstatusenum.md) valeur d’état. Si un avertissement se produit, *ne* a la valeur **adStatusOK** et *pError* contient l’avertissement.  
  
 Avant le retour de cet événement, définissez ce paramètre sur **adStatusUnwantedEvent** pour éviter toute notification.  
  
 *pConnection*  
 A [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet. La connexion pour laquelle l’avertissement s’est produite. Par exemple, des avertissements peuvent se produire lors de l’ouverture un **connexion** objet ou en exécutant un [commande](../../../ado/reference/ado-api/command-object-ado.md) sur un **connexion**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Résumé du Gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)
