---
title: Obtenir des informations sur les déclencheurs DDL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [SQL Server], triggers
- status information [SQL Server], DDL triggers
- DDL triggers, metadata
ms.assetid: 462becea-292a-4b9e-bb98-533e89733911
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 35fdba2dff5f4b68040007c8c5d21c127bd1548c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113769"
---
# <a name="get-information-about-ddl-triggers"></a>Obtenir des informations sur les déclencheurs DDL
  Les affichages catalogue répertoriés dans cette section permettent d'obtenir des informations sur les déclencheurs DDL.  
  
 **Pour obtenir des informations sur les événements ou groupes d'événements sur lesquels un déclencheur DDL peut être activé.**  
  
-   [sys.trigger_event_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-event-types-transact-sql)  
  
 **Pour afficher les dépendances d'un déclencheur**  
  
-   [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
-   [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
-   [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
## <a name="database-scoped-ddl-triggers"></a>Déclencheurs DDL d'étendue de base de données  
 **Pour obtenir des informations sur les déclencheurs d'étendue de base de données**  
  
-   [sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql)  
  
 **Pour obtenir des informations sur les événements de base de données qui exécutent des déclencheurs**  
  
-   [sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql)  
  
 **Pour afficher la définition d'un déclencheur d'étendue de base de données**  
  
-   [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
 **Pour obtenir des informations sur les déclencheurs CLR d'étendue de base de données**  
  
-   [sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
## <a name="server-scoped-ddl-triggers"></a>Déclencheurs DDL d'étendue de serveur  
 **Pour obtenir des informations sur les déclencheurs d'étendue de serveur**  
  
-   [sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)  
  
 **Pour obtenir des informations sur les événements de serveur qui exécutent des déclencheurs**  
  
-   [sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql)  
  
 **Pour afficher la définition d'un déclencheur d'étendue de serveur**  
  
-   [sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql)  
  
 **Pour obtenir des informations sur les déclencheurs CLR d'étendue de serveur**  
  
-   [sys.server_assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
## <a name="see-also"></a>Voir aussi  
 [Déclencheurs DDL](../triggers/ddl-triggers.md)  
  
  
