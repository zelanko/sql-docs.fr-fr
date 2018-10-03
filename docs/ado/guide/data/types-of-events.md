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
ms.openlocfilehash: b324857816df774486716978425d1332a695952a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708467"
---
# <a name="types-of-events"></a>Types d’événements
Il existe deux types d’événements. « Événements will », appelés avant le début d’une opération, comportent généralement « Est » dans leurs noms, par exemple, **WillChangeRecordset** ou **WillConnect**. Les événements qui sont appelées après un événement a été effectué généralement incluent « Complète » dans leurs noms, par exemple, **RecordChangeComplete** ou **ConnectComplete**. Exceptions existent, tel que **InfoMessage** , mais elles se produisent une fois l’opération associée terminée.  
  
## <a name="will-events"></a>Sont des événements  
 Gestionnaires d’événements appelés avant le démarrage de l’opération vous offre la possibilité d’examiner ou modifier les paramètres d’opération, puis annuler l’opération ou lui permettre d’effectuer. Ces routines de gestionnaire d’événements ont généralement des noms au format **sera*événement ***.  
  
## <a name="complete-events"></a>Événements de fin  
 Gestionnaires d’événements appelés après qu’une opération se termine peuvent avertir votre application qu’une opération est terminée. Tel un gestionnaire d’événements est également averti quand un gestionnaire d’événements Will annule une opération en attente. Ces routines de gestionnaire d’événements ont généralement des noms au format ***événement * Terminer**.  
  
 Va et événements de fin sont généralement utilisées par paires.  
  
## <a name="other-events"></a>Autres événements  
 Les autres gestionnaires d’événements, autrement dit, les événements dont les noms ne sont pas sous la forme **sera * événement*** ou ***événement * terminé** — sont appelées uniquement après une opération se termine. Ces événements sont **déconnexion**, **EndOfRecordset**, et **InfoMessage**.  
  
## <a name="see-also"></a>Voir aussi  
 [Résumé du Gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Instanciation des événements ADO par langage](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Paramètres d’événement](../../../ado/guide/data/event-parameters.md)   
 [Fonctionnement conjoint des gestionnaires d’événements](../../../ado/guide/data/how-event-handlers-work-together.md)
