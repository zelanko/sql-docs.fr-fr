---
title: Activation du suivi d’événements dans SqlClient
description: Explique comment activer le suivi d’événements dans SqlClient en implémentant un détecteur d’événements et comment accéder aux données des événements.
ms.date: 06/15/2020
dev_langs:
- csharp
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: johnnypham
ms.author: v-jopha
ms.reviewer: ''
ms.openlocfilehash: 4eac1ab519549ccace092cfc175c735dd4537269
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725740"
---
# <a name="enabling-event-tracing-in-sqlclient"></a>Activation du suivi d’événements dans SqlClient

[!INCLUDE [appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE [Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Le [Suivi d’événements pour Windows (ETW)](/windows/win32/etw/event-tracing-portal) est une fonctionnalité de traçage efficace au niveau du noyau qui permet de consigner les événements définis par le pilote à des fins de débogage et de test. SqlClient prend en charge la capture des événements ETW à différents niveaux d’information. Pour capturer le suivi d’événements, les applications clientes doivent détecter les événements dans l’implémentation EventSource de SqlClient :

```
Microsoft.Data.SqlClient.EventSource
```

L’implémentation actuelle prend en charge les mots clés d’événements suivants :

| Nom du mot clé | Valeur | Description |
| ------------ | ----- | ----------- |
| ExecutionTrace | 1 | Active la capture des événements de démarrage/arrêt avant et après l’exécution de la commande. |
| Trace | 2 | Active la capture des événements de suivi de flux d’application de base. |
| Étendue | 4 | Active la capture des événements d’entrée et de sortie. |
| NotificationTrace | 8 | Active la capture des événements de suivi `SqlNotification`. |
| NotificationScope | 16 | Active la capture des événements d’entrée et de sortie de portée `SqlNotification`. |
| PoolerTrace | 32 | Active la capture des événements de suivi de flux de regroupement de connexions. |
| PoolerScope | 64 | Active la capture des événements de suivi de portée de regroupement de connexions. |
| AdvancedTrace | 128 | Active la capture des événements de suivi de flux avancés. |
| AdvancedTraceBin  | 256 | Active la capture des événements de suivi de flux avancés avec des informations supplémentaires. |
| CorrelationTrace | 512 | Active la capture des événements de suivi de flux de corrélation. |
| StateDump | 1 024 | Active la capture du vidage de l’état complet de `SqlConnection`. |
| SNITrace | 2 048 | Active la capture des événements de suivi de flux à partir de l’implémentation réseau gérée (s’applique uniquement à .NET Core). |
| SNIScope | 4096 | Active la capture des événements de portée à partir de l’implémentation réseau gérée (s’applique uniquement à .NET Core). |
|||

## <a name="example"></a>Exemple
L’exemple suivant active le suivi d’événements pour une opération de données sur l’exemple de base de données **AdventureWorks** et affiche les événements dans la fenêtre de console.

[!code-csharp [SqlClientEventSource#1](~/../sqlclient/doc/samples/SqlClientEventSource.cs#1)]

## <a name="external-resources"></a>Ressources externes  
Pour plus d'informations, consultez les ressources ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[EventSource Class](/dotnet/api/system.diagnostics.tracing.eventsource)|Offre la possibilité de créer des événements ETW.| 
|[Classe EventListener](/dotnet/api/system.diagnostics.tracing.eventlistener)|Fournit des méthodes permettant d’activer et de désactiver des événements à partir des sources d’événements.|