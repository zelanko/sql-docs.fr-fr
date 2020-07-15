---
title: blocked process threshold (option de configuration de serveur) | Microsoft Docs
description: Découvrez comment utiliser l’option blocked process threshold pour spécifier l’intervalle auquel SQL Server génère des rapports de processus bloqués et des alertes de problèmes.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- thresholds [SQL Server]
- blocked process threshold option
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bdd5f7d01e7271609562fb7d42126746d6163de4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725240"
---
# <a name="blocked-process-threshold-server-configuration-option"></a>blocked process threshold (option de configuration de serveur)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

 L'option **blocked process threshold** permet de spécifier le seuil, en secondes, à partir duquel des rapports de processus bloqués sont générés. Le seuil peut être compris entre 5 et 86 400.  Le moniteur de verrou se réveille uniquement toutes les 5 secondes pour détecter les conditions de blocage (il recherche également d’autres conditions, telles que les blocages). Par conséquent, si vous affectez la valeur 1 à une valeur « blocked process threshold », il ne détecte pas un processus qui a été bloqué pendant 1 seconde. La durée minimale qui lui permet de détecter un processus bloqué est de 5 secondes.
 
 Par défaut, aucun rapport de processus bloqué n'est généré. Cet événement n'est pas généré pour les tâches système ou les tâches en attente de ressources qui ne génèrent pas de blocages détectables.  
  
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
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Blocked Process Report, classe d’événements](../../relational-databases/event-classes/blocked-process-report-event-class.md)  
  
  
