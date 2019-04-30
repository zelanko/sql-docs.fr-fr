---
title: Types d’événements | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- EventComplete event [ADO]
- events [ADO], types
- Will events [ADO]
- complete events [ADO]
- WillEvent event [ADO]
ms.assetid: f3327ea0-635a-43d4-bd78-c1674f62f1a2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 78505f010706a39e5278d50219dd4504e33dd67c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63142938"
---
# <a name="types-of-events"></a>Types d’événements
Il existe deux types d’événements. « Événements will », appelés avant le début d’une opération, comportent généralement de « Est » dans leurs noms - par exemple, **WillChangeRecordset** ou **WillConnect**. Les événements qui sont appelées après un événement a été effectué généralement incluent par exemple, « Complète » dans leurs noms - **RecordChangeComplete** ou **ConnectComplete**. Exceptions existent - comme **InfoMessage** - mais elles se produisent une fois l’opération associée terminée.  
  
## <a name="will-events"></a>Sont des événements  
 Gestionnaires d’événements appelés avant le démarrage de l’opération vous offre la possibilité d’examiner ou modifier les paramètres d’opération, puis annuler l’opération ou lui permettre d’effectuer. Ces routines de gestionnaire d’événements ont généralement des noms au format <strong>sera*événement*</strong>.  
  
## <a name="complete-events"></a>Événements de fin  
 Gestionnaires d’événements appelés après qu’une opération se termine peuvent avertir votre application qu’une opération est terminée. Tel un gestionnaire d’événements est également averti quand un gestionnaire d’événements Will annule une opération en attente. Ces routines de gestionnaire d’événements ont généralement des noms au format  <strong>*événement*Terminer</strong>.  
  
 Va et événements de fin sont généralement utilisées par paires.  
  
## <a name="other-events"></a>Autres événements  
 Les autres gestionnaires d’événements - autrement dit, les événements dont les noms ne sont pas sous la forme <strong>sera*événement*</strong>  ou  <strong>*événement*Terminer</strong> -sont appelées uniquement après une opération se termine. Ces événements sont **déconnexion**, **EndOfRecordset**, et **InfoMessage**.  
  
## <a name="see-also"></a>Voir aussi  
 [Résumé du Gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Instanciation des événements ADO par langage](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Paramètres d’événement](../../../ado/guide/data/event-parameters.md)   
 [Fonctionnement conjoint des gestionnaires d’événements](../../../ado/guide/data/how-event-handlers-work-together.md)
