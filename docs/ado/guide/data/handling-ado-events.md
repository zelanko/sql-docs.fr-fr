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
manager: jroth
ms.openlocfilehash: 162cac52920b076e4388a74a251cd347137f49cd
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702018"
---
# <a name="handling-ado-events"></a>Gestion des événements ADO
Le modèle d’événement ADO prend en charge certaines opérations synchrones et asynchrones qui émettent *événements*, ou des notifications, avant le démarrage de l’opération ou une fois terminé. Un événement est en fait un appel à une routine de gestionnaire d’événements que vous définissez dans votre application.  
  
 Si vous fournissez des fonctions de gestionnaire ou les procédures pour le groupe d’événements qui se produisent avant le démarrage de l’opération, vous pouvez examiner ou modifier les paramètres qui ont été passés à l’opération. Car il n'a pas encore été exécutée, vous pouvez annuler l’opération ou lui permettre d’effectuer.  
  
 Les événements qui se produisent après qu’une opération se termine sont particulièrement importants si vous utilisez ADO de façon asynchrone. Par exemple, une application qui démarre asynchrone [Recordset.Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) opération est avertie par un événement de fin de l’exécution lorsque l’opération se termine.  
  
 À l’aide du modèle d’événement ADO ajoute une surcharge à votre application, mais fournit plus de souplesse que d’autres méthodes de traitement des opérations asynchrones, comme la surveillance du [état](../../../ado/reference/ado-api/state-property-ado.md) propriété d’un objet avec une boucle.  
  
> [!NOTE]
>  Pour gérer les événements, ADO doit avoir une pompe de messages ou être utilisée dans un modèle de thread unique cloisonné (STA). Événements ADO sont gérées en interne en créant une fenêtre masquée. ADO publie des messages dans cette fenêtre lorsque des événements doivent être des déclencheurs. Cela permet de vous assurer que les événements sont envoyés au thread qui a appelé **IConnectionPoint::Advise** sur le point de connexion. Cette architecture peut entraîner des problèmes lorsque le thread qui doit recevoir les notifications ne pompe pas les messages de fenêtre. Les problèmes potentiels incluent des événements ADO ne pas remises au thread et les diffusions de fenêtre global n’expire et éventuellement ralentir l’ensemble du système, car les fenêtres masquées ne pas traitent les messages. Threads STA ont généralement une pompe de messages en cours d’exécution pour ce problème ne se produit pas sur des threads STA. Threads MTA, toutefois, en général ont une pompe de messages et le problème est généralement se manifester sur des threads MTA.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)  
  
-   [Types d’événements](../../../ado/guide/data/types-of-events.md)  
  
-   [Paramètres des événements](../../../ado/guide/data/event-parameters.md)  
  
-   [Fonctionnement conjoint des gestionnaires d’événements](../../../ado/guide/data/how-event-handlers-work-together.md)  
  
-   [Instanciation des événements ADO par langage](../../../ado/guide/data/ado-event-instantiation-by-language.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Résumé du Gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Instanciation des événements ADO par langage](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Événements ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Paramètres d’événement](../../../ado/guide/data/event-parameters.md)   
 [Types d’événements](../../../ado/guide/data/types-of-events.md)
