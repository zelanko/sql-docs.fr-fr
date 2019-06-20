---
title: Cible d’histogramme | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- bucketing target [SQL Server extended events]
- event bucketing target
- targets [SQL Server extended events], bucketing
ms.assetid: 2ea39141-7eb0-4c74-abf8-114c2c106a19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4a584311061a24d674eed114f37d9cbbbda43909
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66064698"
---
# <a name="histogram-target"></a>Cible d'histogramme
  Une cible d'histogramme regroupe les occurrences d'un type d'événement spécifique en fonction de données d'événement. Les regroupements d'événements sont comptabilisés en fonction d'une colonne d'événement ou d'une action spécifiée. Vous pouvez utiliser la cible d'histogramme pour résoudre les problèmes de performance. En identifiant les événements qui se produisent le plus souvent, vous pouvez trouver des « zones réactives » qui indiquent la cause probable d'un problème de performance.  
  
 Le tableau suivant décrit les options pouvant être utilisées pour configurer la cible d'histogramme.  
  
|Option|Valeurs autorisées|Description|  
|------------|--------------------|-----------------|  
|slots|Toute valeur entière. Cette valeur est facultative.|Valeur spécifiée par l'utilisateur qui indique le nombre maximal de regroupements à conserver. Lorsque cette valeur est atteinte, les nouveaux événements qui n'appartiennent pas aux groupes existants sont ignorés.<br /><br /> Notez que pour améliorer les performances, le numéro d'emplacement est arrondi à la puissance suivante de 2.|  
|filtering_event_name|Tout événement présent dans la session Événements étendus. Cette valeur est facultative.|Une valeur spécifiée par l'utilisateur qui permet d'identifier une classe d'événements. Seules les instances de l'événement spécifié sont placées dans un compartiment. Tous les autres événements sont ignorés.<br /><br /> Si vous spécifiez cette valeur, vous devez utiliser le format *nom_package*.*nom_événement*, par exemple `'sqlserver.checkpoint_end'`. Vous pouvez identifier le nom du package à l'aide de la requête suivante :<br /><br /> Sélectionnez p.name, se.event_name<br />À partir de la deuxième édition sys.dm_xe_session_events<br />JOINDRE sys.dm_xe_packages p<br />ON se_event_package_guid = p.guid<br />ORDER BY p.name, se.event_name<br /><br /> <br /><br /> Si vous ne spécifiez pas la valeur filtering_event_name, source_type doit avoir la valeur 1 (valeur par défaut).|  
|source_type|Type d'objet sur lequel le compartiment est basé. Cette valeur est facultative et a la valeur par défaut 1 si elle n'est pas spécifiée.|Peut avoir l'une des valeurs suivantes :<br /><br /> 0 pour un événement<br /><br /> 1 pour une action|  
|source|Colonne d'événement ou nom d'action.|La colonne d'événement ou le nom d'action utilisé(e) comme source de données.<br /><br /> Lorsque vous spécifiez une colonne d'événement pour la source, vous devez spécifier une colonne à partir de l'événement qui est utilisé pour la valeur filtering_event_name. Vous pouvez identifier les colonnes possibles à l'aide de la requête suivante :<br /><br /> Nom de sélection FROM sys.dm_xe_object_columns<br />WHERE object_name = '\<nom_événement >'<br />AND column_type != 'readonly'<br /><br /> Lorsque vous spécifiez une colonne d'événement pour la source, il n'est pas nécessaire d'inclure le nom du package dans la valeur de la source.<br /><br /> Lorsque vous spécifiez un nom d'action pour la source, vous devez utiliser l'une des actions configurées pour la collection dans la session d'événements pour laquelle cette cible est utilisée. Pour trouver les valeurs possibles pour le nom d'action, vous pouvez interroger la colonne action_name de la vue sys.dm_xe_sesssion_event_actions.<br /><br /> Si vous utilisez un nom d’action comme source de données, vous devez spécifier la valeur de la source en utilisant le format *nom_package*.*nom_action*.|  
  
 L'exemple suivant montre globalement comment la cible d'histogramme collecte les données. Dans cet exemple, vous utilisez la cible d'histogramme pour comptabiliser le nombre d'attentes de chaque type d'attente. Pour ce faire, spécifiez les options suivantes lorsque vous définissez la cible d'histogramme :  
  
-   filtering_event_name = 'wait_info'  
  
-   source = 'wait_type'  
  
-   source_type = 0 (car wait_type est une colonne d'événement)  
  
 Dans ce scénario d'exemple, les données suivantes sont enregistrées pour la source wait_type.  
  
|Nom de l'événement de filtrage|Valeur de la colonne source|  
|--------------------------|-------------------------|  
|wait_info|file_io|  
|wait_info|file_io|  
|wait_info|réseau|  
|wait_info|réseau|  
|wait_info|veille|  
  
 Les valeurs de type d'attente doivent être catégorisées dans trois emplacements, avec les valeurs et nombres d'emplacements suivants :  
  
|Value|Nombre d'emplacements|  
|-----------|----------------|  
|file_io|2|  
|réseau|2|  
|veille|1|  
  
 La cible d'histogramme conserve seulement les données d'événement pour la source spécifiée. Dans certains cas, les données d'événement peuvent être trop volumineuses pour être conservées complètement, auxquels cas les données sont tronquées. Lorsque des données d'événement sont tronquées, le nombre d'octets est enregistré et affiché comme sortie XML.  
  
## <a name="adding-the-target-to-a-session"></a>Ajout de la cible à une session  
 Pour ajouter la cible d'histogramme à une session Événements étendus lorsque vous créez ou modifiez une session d'événements, vous devez inclure l'une des instructions suivantes, selon le type de cible désiré :  
  
```  
ADD TARGET package0.histogram  
```  
  
 Vous pouvez utiliser l'instruction SET pour définir les différentes options. L’exemple suivant montre l’ajout de la cible d’histogramme, dans laquelle les données de l’événement sqlserver.checkpoint_end sont recueillies.  
  
```  
ADD TARGET package0.histogram  
(SET slots = 32, filtering_event_name = 'sqlserver.checkpoint_end', source_type = 0, source = 'database_id')  
```  
  
 Pour plus d’informations, consultez [Trouver les objets comportant le plus de verrous](../relational-databases/extended-events/find-the-objects-that-have-the-most-locks-taken-on-them.md)et [Surveiller l’activité système à l’aide d’événements étendus](../relational-databases/extended-events/monitor-system-activity-using-extended-events.md).  
  
## <a name="reviewing-the-target-output"></a>Vérification de la sortie cible  
 La cible d'histogramme applique en série les données à une procédure ou un programme appelant au format XML. La sortie cible n'est conforme à aucun schéma.  
  
 Pour vérifier la sortie de la cible d’histogramme, vous pouvez utiliser la requête suivante, en remplaçant *nom_session* par le nom de la session d’événements.  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 L'exemple suivant illustre le format de sortie de la cible d'histogramme.  
  
```  
<Slots truncated = "0" buckets=[count]>  
    <Slot count=[count] trunc=[truncated bytes]>  
        <value>  
        </value>  
    </Slot>  
</Slots>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Cibles des Événements étendus SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)   
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
