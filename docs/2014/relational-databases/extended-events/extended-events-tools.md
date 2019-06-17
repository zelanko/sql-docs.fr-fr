---
title: Outils associés aux événements étendus | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], using
- extended events [SQL Server], options for using
ms.assetid: d312a9ff-50ba-4721-baef-50bfd3169d38
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e26bc62f0e6b81b7b4ac8e1361d0a1ac31513ef6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63137048"
---
# <a name="extended-events-tools"></a>Outils associés aux événements étendus
  Vous pouvez utiliser les outils suivants pour créer et gérer des sessions d’événements étendus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   Instructions DDL (Data Definition Language). Celles-ci vous permettent de créer et de modifier une session d'événements étendus.  
  
-   Vues de gestion dynamique, affichages catalogue et tables système. Ceux-ci vous permettent d’obtenir des données et des métadonnées de session à l’aide des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] . Les tables système vous aident à déterminer les équivalents Événements étendus existants pour les classes d'événements Trace SQL et les colonnes.  
  
-   Nœud **Événements étendus** de l’Explorateur d’objets. Il vous permet de démarrer, d'arrêter ou de supprimer une session, ou d'importer et d'exporter des modèles de session.  
  
-   Fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell. Il s’agit d’un outil puissant que vous pouvez utiliser pour créer, modifier et gérer des sessions d’événements étendus. Pour plus d’informations, consultez [Utiliser le fournisseur PowerShell pour les événements étendus](use-the-powershell-provider-for-extended-events.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Cela vous permet de créer et d'exécuter les exemples de code fournis dans les rubriques Événements étendus. Pour plus d’informations, consultez [Explorateur d’objets](../../ssms/object/object-explorer.md).  
  
 En plus des sessions que vous créez, une session de l'intégrité du système par défaut existe sur le serveur. Elle recueille des données système qui peuvent vous aider à résoudre des problèmes de performances. Pour plus d’informations, consultez [Utiliser la session system_health](use-the-ssms-xe-profiler.md).  
  
## <a name="ddl-statements"></a>Instructions DDL  
 Utilisez les instructions DDL suivantes pour créer, modifier et supprimer une session d'événements étendus.  
  
|Nom|Description|  
|----------|-----------------|  
|[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)|Crée un objet de session Événements étendus qui identifie la source des événements, les cibles de la session d'événements et les paramètres de la session d'événements.|  
|[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)|Démarre ou arrête une session d'événements, ou modifie la configuration d'une session d'événements.|  
|[DROP EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-event-session-transact-sql)|Supprime une session d'événements.|  
  
## <a name="catalog-views"></a>Affichages catalogue  
 Utilisez les affichages catalogue ci-dessous pour obtenir les métadonnées créées lorsque vous créez une session d'événements.  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|[sys.server_event_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql)|Répertorie toutes les définitions de la session d'événements.|  
|[sys.server_event_session_actions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-session-actions-transact-sql)|Retourne une ligne pour chaque action d'un événement d'une session d'événements.|  
|[sys.server_event_session_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-session-events-transact-sql)|Retourne une ligne pour chaque événement d'une session d'événements.|  
|[sys.server_event_session_fields &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-session-fields-transact-sql)|Retourne une ligne pour chaque colonne personnalisable définie explicitement sur les événements et les cibles.|  
|[sys.server_event_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-session-targets-transact-sql)|Retourne une ligne pour chaque cible d'événement d'une session d'événements.|  
  
## <a name="dynamic-management-views"></a>Vues de gestion dynamique  
 Utilisez les vues de gestion dynamique ci-dessous pour obtenir des métadonnées de session et des données de session. Les métadonnées sont obtenues à partir des affichages catalogue et les données de session sont créées lorsque vous démarrez et exécutez une session d'événements.  
  
> [!NOTE]  
>  Ces vues ne contiennent pas de données de session tant qu'une session n'a pas démarré.  
  
|Nom|Description|  
|----------|-----------------|  
|[sys.dm_os_dispatcher_pools &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-dispatcher-pools-transact-sql)|Retourne des informations sur les pools de répartiteurs de la session.|  
|[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)|Retourne une ligne pour chaque objet exposé par un package d'événement.|  
|[sys.dm_xe_object_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-object-columns-transact-sql)|Retourne les informations de schéma pour tous les objets.|  
|[sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)|Répertorie tous les packages inscrits avec le moteur d'événements étendus.|  
|[sys.dm_xe_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql)|Retourne des informations sur une session d'événements étendus active.|  
|[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)|Retourne des informations sur les cibles de la session.|  
|[sys.dm_xe_session_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-events-transact-sql)|Retourne des informations sur les événements de la session.|  
|[sys.dm_xe_session_event_actions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-event-actions-transact-sql)|Retourne des informations sur les actions de la session d'événements.|  
|[sys.dm_xe_map_values &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-map-values-transact-sql)|Fournit un mappage des clés numériques internes sur du texte explicite.|  
|[sys.dm_xe_session_object_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-object-columns-transact-sql)|Indique les valeurs de configuration d'objets liés à une session.|  
  
## <a name="system-tables"></a>Tables système  
 Utilisez les tables système suivantes pour obtenir les informations à propos des équivalents Événements étendus pour les classes d'événements Trace SQL et les colonnes.  
  
|Nom|Description|  
|----------|-----------------|  
|[trace_xe_event_map &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/extended-events-tables-trace-xe-event-map)|Contient une ligne pour chaque événement Événements étendus mappé à une classe d'événements Trace SQL.|  
|[trace_xe_action_map &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/extended-events-tables-trace-xe-action-map)|Contient une ligne pour chaque action Événements étendus mappée à un ID de colonne Trace SQL.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](../views/views.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)   
 [Tables des événements étendus SQL Server &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/system-tables-transact-sql)   
 [Utiliser la session system_health](use-the-ssms-xe-profiler.md)   
 [Utiliser le fournisseur PowerShell pour les événements étendus](use-the-powershell-provider-for-extended-events.md)  
  
  
