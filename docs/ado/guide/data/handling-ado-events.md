---
title: Gestion des événements ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO]
- ADO, events
- event handlers [ADO]
ms.assetid: e9003457-0762-48b3-942f-0820266b158f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 452259b6e4e406d7a406211a9e9b42ebbf60da53
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925222"
---
# <a name="handling-ado-events"></a>Gestion des événements ADO
Le modèle d’événements ADO prend en charge certaines opérations ADO synchrones et asynchrones qui émettent des *événements*, ou notifications, avant le démarrage de l’opération ou après son achèvement. Un événement est en fait un appel à une routine de gestionnaire d’événements que vous définissez dans votre application.  
  
 Si vous fournissez des fonctions de gestionnaire ou des procédures pour le groupe d’événements qui se produisent avant le démarrage de l’opération, vous pouvez examiner ou modifier les paramètres qui ont été passés à l’opération. Comme il n’a pas encore été exécuté, vous pouvez annuler l’opération ou l’autoriser à se terminer.  
  
 Les événements qui se produisent après la fin d’une opération sont particulièrement importants si vous utilisez ADO de manière asynchrone. Par exemple, une application qui démarre une opération asynchrone [Recordset. Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) est notifiée par un événement exécution terminée lorsque l’opération se termine.  
  
 L’utilisation du modèle d’événement ADO ajoute une surcharge à votre application, mais offre une plus grande souplesse que les autres méthodes de gestion des opérations asynchrones, telles que la surveillance de la propriété d' [État](../../../ado/reference/ado-api/state-property-ado.md) d’un objet avec une boucle.  
  
> [!NOTE]
>  Pour gérer les événements, ADO doit avoir une pompe de messages ou être utilisé dans un modèle STA (Single-Threaded Apartment). Les événements ADO sont gérés en interne par la création d’une fenêtre masquée. ADO publie des messages dans cette fenêtre lorsque des événements doivent être déclenchés. Cela permet de s’assurer que les événements sont envoyés au thread qui a appelé **IConnectionPoint :: Advise** sur le point de connexion. Cette architecture peut entraîner des problèmes lorsque le thread qui doit recevoir les notifications ne pompe pas les messages de fenêtre. Les problèmes potentiels incluent les événements ADO non remis au thread et les diffusions de fenêtre globale expirent et ralentissent éventuellement le système entier, car les fenêtres masquées ne traitent pas les messages. Les threads STA ont généralement une pompe de messages en cours d’exécution, ce problème ne se manifeste donc pas sur les threads STA. Toutefois, les threads MTA ne disposent généralement pas d’une pompe de messages, de sorte que le problème se manifeste généralement sur les threads MTA.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)  
  
-   [Types d’événements](../../../ado/guide/data/types-of-events.md)  
  
-   [Paramètres des événements](../../../ado/guide/data/event-parameters.md)  
  
-   [Fonctionnement conjoint des gestionnaires d’événements](../../../ado/guide/data/how-event-handlers-work-together.md)  
  
-   [Instanciation des événements ADO par langage](../../../ado/guide/data/ado-event-instantiation-by-language.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Résumé du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Instanciation des événements ADO par langage](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Événements ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Paramètres d’événement](../../../ado/guide/data/event-parameters.md)   
 [Types d’événements](../../../ado/guide/data/types-of-events.md)
