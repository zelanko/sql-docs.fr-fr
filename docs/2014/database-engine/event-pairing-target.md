---
title: Événement cible d’appariement | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- pairing target [SQL Server extended events]
- event pairing target
- targets [SQL Server extended events], pairing target
ms.assetid: 3c87dcfb-543a-4bd8-a73d-1390bdf4ffa3
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7907ec8b5fa2e450a1a9e3e73c82bf8511da64ca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62780410"
---
# <a name="event-pairing-target"></a>Cible d'appariement d'événements
  La cible d'appariement d'événements correspond à deux événements qui utilisent une ou plusieurs colonnes de données qui sont présentes dans chaque événement. De nombreux événements se présentent sous forme de paires, tels que les acquisitions et les libérations de verrous. Une fois qu'une séquence d'événement a été couplée, les deux événements sont ignorés. Ignorer des jeux correspondants permet de détecter facilement les acquisitions de verrous qui n'ont pas été libérées.  
  
 Grâce aux filtres au niveau des événements, la cible d'appariement peut être utilisée pour capturer uniquement les événements qui ne correspondent pas aux critères prédéfinis.  
  
 Lorsque vous utilisez la cible d'appariement d'événements, vous pouvez choisir deux événements à associer, ainsi qu'une séquence de colonnes sur lesquelles s'effectuera la correspondance. Toutes les colonnes dans cette séquence doivent être du même type.  
  
 Le tableau suivant décrit les options disponibles pour configurer l'appariement d'événements.  
  
|Option|Valeurs autorisées|Description|  
|------------|--------------------|-----------------|  
|begin_event|Tout nom d'événement qui est présent dans la session active.|Le nom d'événement qui spécifie l'événement de début dans une séquence couplée.|  
|end_event|Tout nom d'événement qui est présent dans la session active.|Le nom d'événement qui spécifie l'événement de fin dans une séquence couplée.|  
|begin_matching_columns|Une liste ordonnée de noms de colonnes séparés par des virgules.|Les colonnes sur lesquelles effectuer la correspondance.|  
|end_matching_columns|Une liste ordonnée de noms de colonnes séparés par des virgules.|Les colonnes sur lesquelles effectuer la correspondance.|  
|begin_matching_actions|Liste ordonnée d'actions séparées par des virgules.|Actions sur lesquelles effectuer la correspondance.|  
|end_matching_actions|Liste ordonnée d'actions séparées par des virgules.|Actions sur lesquelles effectuer la correspondance.|  
|respond_to_memory_pressure|Une des valeurs suivantes :<br /><br /> 0 = ne pas répondre.<br /><br /> 1 = arrêter d'ajouter de nouveaux orphelins à la liste en cas de sollicitation de la mémoire.|La réponse cible aux événements de mémoire. Si la valeur spécifiée est 1 et que la mémoire du serveur est insuffisante, les informations non couplées qui sont conservées sont supprimées.|  
|max_orphans||Spécifie le nombre total d'événements non couplés qui seront collectés dans la cible. Une fois la limite atteinte, les événements non couplés sont supprimés selon le principe FIFO (premier entré/premier sorti). Par défaut = 10,000.|  
  
 Toutes les données associées à un événement sont capturées et stockées pour un appariement futur. De plus, les données ajoutées par les actions sont également collectées. Les données d'événement collectées sont stockées en mémoire et ont donc une limite finie. Cette limite est basée sur la capacité et l'activité du système. Plutôt que prendre la quantité maximale de mémoire à utiliser comme paramètre, la quantité de mémoire utilisée sera basée sur les ressources système disponibles. Lorsque celles-ci ne sont pas disponibles, les événements non couplés qui ont été conservés seront supprimés. Si un événement n'a pas été couplé et est supprimé, l'événement correspondant apparaîtra comme un événement non couplé.  
  
 La cible d'appariement applique en série des événements non couplés à un format XML. Ce format n'est conforme à aucun schéma. Le format contient uniquement deux types d'éléments. Le  **\<non appariés >** élément est la racine, suivi d’une unité. **\<événement >** élément pour chaque événement non couplé qui est actuellement en cours de suivi. Le  **\<événement >** élément contient un attribut qui contient le nom de l’événement non couplé.  
  
## <a name="adding-the-target-to-a-session"></a>Ajout de la cible à une session  
 Pour ajouter la paire cible correspondante à une session Événements étendus lorsque vous créez ou modifiez une session d'événements, vous devez inclure l'instruction suivante :  
  
```  
ADD TARGET package0.pair_matching   
```  
  
 Vous la ferez suivre d'une instruction SET pour définir les événements de début et de fin, ainsi que les actions ou les colonnes correspondantes. Voici un exemple de syntaxe pour l’appariement des événements sqlserver.lock_acquired et sqlserver.lock_released.  
  
```  
   ( SET begin_event = 'sqlserver.lock_acquired',  
      begin_matching_columns = 'database_id, resource_0, resource_1, resource_2, transaction_id, mode',  
      end_event = 'sqlserver.lock_released',  
      end_matching_columns = 'database_id, resource_0, resource_1, resource_2, transaction_id, mode',  
   respond_to_memory_pressure = 1)  
```  
  
 Pour plus d’informations, consultez [Déterminer quelles requêtes détiennent des verrous](../relational-databases/extended-events/determine-which-queries-are-holding-locks.md).  
  
## <a name="reviewing-the-target-output"></a>Vérification de la sortie cible  
 Pour vérifier la sortie de la cible d’appariement, vous pouvez utiliser la requête suivante, en remplaçant *nom_session* par le nom de la session d’événements.  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 L'exemple suivant montre le format de sortie de la cible d'appariement.  
  
```  
<unpaired truncated = "0" matchedCount = "[matched count]" memoryPressureDroppedCount = " [lost count]">  
    <event name  = "[event name]" package = "[package]" id= "[event ID value]" version = "[event version]">  
    <data name = "[column name]">   
    <type name = "[column type]" package = "[type package]" />   
    <value>[column value]</value>  
    <text value>[text value]</text>>  
        </data>  
    </event>  
</unpaired>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Cibles des Événements étendus SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)   
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
