---
title: Cible de mémoire tampon en anneau des | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events], ring buffer target
- ring buffer target [SQL Server extended events]
ms.assetid: 54494e11-b56b-43b7-aa5e-c8724e56b251
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d52dc4ba85ec3b65ddf3e1c703befd0ee32d78a0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48182539"
---
# <a name="ring-buffer-target"></a>Cible de mémoire tampon en anneau
  La cible de mémoire tampon en anneau maintient brièvement les données d'événements en mémoire. Cette cible peut gérer des événements dans deux modes différents.  
  
-   Le premier mode est le mode FIFO strict (premier entré, premier sorti), où l'événement le plus ancien est supprimé lorsque toute la mémoire allouée à la cible est utilisée. Dans ce mode (par défaut), l'option occurrence_number a la valeur 0.  
  
-   Le deuxième mode est le mode FIFO par événement, où un nombre spécifié d'événements de chaque type est conservé. Dans ce mode, les événements les plus anciens de chaque type sont supprimés lorsque toute la mémoire allouée à la cible est utilisée. Vous pouvez configurer l'option occurrence_number pour spécifier le nombre d'événements de chaque type à conserver.  
  
 Le tableau suivant décrit les options disponibles pour configurer la cible de mémoire tampon en anneau.  
  
|Option|Valeurs autorisées|Description|  
|------------|--------------------|-----------------|  
|max_memory|Tout entier de 32 bits. Cette valeur est facultative.|Quantité de mémoire maximale, en kilo-octet (Ko), à utiliser. Des événements existants sont supprimés en fonction de la limite qui est atteinte en premier : max_event_limit ou max_memory.|  
|max_event_limit|Tout entier de 32 bits. Cette valeur est facultative.|Nombre maximal d'événements conservés dans le tampon ring_buffer. Des événements existants sont supprimés en fonction de la limite qui est atteinte en premier : max_event_limit ou max_memory. Par défaut = 1000.|  
|occurrence_number|Une des valeurs suivantes :<br /><br /> 0 (par défaut) = l'événement le plus ancien est supprimé lorsque toute la mémoire allouée à la cible est utilisée.<br /><br /> entier 32 bits = le nombre d'événements de chaque type à conserver avant d'être supprimés en fonction du mode FIFO par événement.<br /><br /> <br /><br /> Cette valeur est facultative.|Le mode FIFO à utiliser et, s'il est supérieur à 0, le nombre d'événements préférés de chaque type à conserver dans la mémoire tampon.|
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="adding-the-target-to-a-session"></a>Ajout de la cible à une session  
 Pour ajouter la cible de mémoire tampon en anneau à une session Événements étendus lorsque vous créez ou modifiez une session d'événements, vous devez inclure l'instruction suivante :  
  
```sql
ADD TARGET package0.ring_buffer  
```  
  
## <a name="reviewing-the-target-output"></a>Vérification de la sortie cible  
 Pour vérifier la sortie de la cible de mémoire tampon en anneau, vous pouvez utiliser la requête suivante, en remplaçant *session_name* par le nom de la session d’événements.  
  
```sql
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 L'exemple suivant montre le format de sortie de la cible de mémoire tampon en anneau.  
  
```  
<RingBufferTarget eventsPerSec="" processingTime="" totalEventsProcessed="" eventCount="" droppedCount="" memoryUsed="">  
 <event name="" package="" id="" version="" timestamp="">  
    <data name="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </data>  
    <action name="" package="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </action>  
  </event>  
</RingBufferTarget>  
```


## <a name="see-also"></a>Voir aussi

- [Cibles des Événements étendus SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)
- [sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql?view=sql-server-2016)
- [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql?view=sql-server-2016)
- [ALTER EVENT SESSION &#40;Transact-SQL&#41;](https://docs.microsoft.com/sql/t-sql/statements/alter-event-session-transact-sql?view=sql-server-2016)

