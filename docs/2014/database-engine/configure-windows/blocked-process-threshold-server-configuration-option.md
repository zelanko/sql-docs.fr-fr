---
title: blocked process threshold (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- thresholds [SQL Server]
- blocked process threshold option
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
caps.latest.revision: 19
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4c8208b51bd017aff5c2b4bf0092625926852af2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200159"
---
# <a name="blocked-process-threshold-server-configuration-option"></a>blocked process threshold (option de configuration de serveur)
  L'option **blocked process threshold** permet de spécifier le seuil, en secondes, à partir duquel des rapports de processus bloqués sont générés. Le seuil peut être compris entre 0 et 86 400. Par défaut, aucun rapport de processus bloqué n'est généré. Cet événement n'est pas généré pour les tâches système ou les tâches en attente de ressources qui ne génèrent pas de blocages détectables.  
  
 Vous pouvez définir une [alerte](../../ssms/agent/alerts.md) à exécuter dès lorsque cet événement est généré. Ainsi, par exemple, vous pouvez choisir de contacter l'administrateur par récepteur de radiomessagerie afin de l'inviter à gérer la situation de blocage de manière appropriée.  
  
 L'option « blocked process threshold » utilise le thread d'arrière-plan Moniteur de blocage pour parcourir la liste des tâches en attente depuis une durée supérieure ou multiple du seuil configuré. L'événement est généré une fois par intervalle de génération de rapports pour chaque tâche bloquée.  
  
 Les rapports de processus bloqués sont générés le plus tôt possible. Toutefois, rien ne garantit qu'ils seront générés en temps réel ou quasiment en temps réel.  
  
 Le paramètre prend effet immédiatement, sans arrêt et redémarrage du serveur.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, l'option `blocked process threshold` est définie à `20` secondes, générant ainsi un rapport de processus bloqué pour chaque tâche bloquée.  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 20 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Blocked Process Report, classe d’événements](../../relational-databases/event-classes/blocked-process-report-event-class.md)  
  
  
