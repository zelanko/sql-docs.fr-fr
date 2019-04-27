---
title: Cible de compteur d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- synchronous event counter target [SQL Server extended events]
- targets [SQL Server extended events], synchronous event counter target
ms.assetid: 342e08d1-dcca-4a71-ae64-cb61b55b85bc
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8f701ff8a1648a3f90f7e04c71f159081ac7a3da
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62780903"
---
# <a name="event-counter-target"></a>Cible de compteur d'événements
  La cible de compteur d'événements compte tous les événements qui surviennent au cours d'une session Événements étendus. Elle vous permet d'obtenir des informations sur les caractéristiques de charge de travail sans ajouter la surcharge de la collecte d'événements complète. Cette cible n'a pas de paramètres personnalisables.  
  
## <a name="adding-the-target-to-a-session"></a>Ajout de la cible à une session  
 Pour ajouter la cible de compteur d'événements à une session Événements étendus, vous devez inclure l'instruction suivante lorsque vous créez ou modifiez une session d'événements :  
  
```  
ADD TARGET package0.event_counter  
```  
  
## <a name="reviewing-the-target-output"></a>Vérification de la sortie cible  
 Pour vérifier la sortie de la cible de compteur d’événements, vous pouvez utiliser la requête suivante, en remplaçant *session_name* par le nom de la session d’événements :  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 L'exemple suivant montre le format de sortie de la cible de compteur d'événements.  
  
```  
<CounterTarget truncated = "0">  
  <Packages>  
    <Package name = "[package name]">  
      <Event name = "[event name]" count = "[number]" />  
    </Package>  
  </Packages>  
</CounterTarget>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Cibles des Événements étendus SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)   
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
