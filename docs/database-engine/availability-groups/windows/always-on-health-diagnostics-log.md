---
title: Journaux de diagnostic d’intégrité de la DLL de ressource SQL Server pour les groupes de disponibilité
description: Décrit comment la DLL de ressource SQL Server supervise l’intégrité du groupe de disponibilité Always On.
ms.custom: ag-guide, seodec18
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: c1862d8a-5f82-4647-a280-3e588b82a6dc
author: rothja
ms.author: jroth
manager: jroth
ms.openlocfilehash: f9df88d021ffa6aebbc30f3a733ece3b395ac102
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66789587"
---
# <a name="sql-server-resource-dll-health-diagnostic-logs-for-availability-groups"></a>Journaux de diagnostic d’intégrité de la DLL de ressource SQL Server pour les groupes de disponibilité
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Pour monitorer l’intégrité du réplica de disponibilité principal, la DLL de ressource SQL Server exécutée par le cluster WSFC (clustering de basculement Windows Server) utilise une procédure stockée dans l’instance SQL Server appelée [sp_server_diagnostics](~/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md).  
  
 La DLL de ressource SQL Server garde une connexion ouverte dédiée à l’instance SQL Server, via laquelle l’instance SQL Server envoie régulièrement des diagnostics d’intégrité détaillés à la DLL de ressource SQL Server. Le cluster utilise les diagnostics d’intégrité, ainsi que la stratégie de basculement configurée dans la ressource du groupe de disponibilité du cluster (propriété FailoverConditionLevel), pour déterminer s’il faut redémarrer ou basculer la ressource du groupe de disponibilité. Cette procédure stockée constitue la « pulsation » entre l’instance SQL Server 2012 (et versions ultérieures) et le cluster WSFC. Elle est plus précise et plus fiable que dans SQL Server 2008 R2 (et versions antérieures), où une connexion périodique à l’instance est établie au moyen de la requête `SELECT @@SERVERNAME`. Vous pouvez ensuite contrôler les conditions qui déclenchent des basculements en définissant la propriété FailureConditonLevel du groupe de disponibilité.  
  
 **Utiliser les journaux de diagnostic du cluster de basculement SQL Server**
 
 Tous les diagnostics d’intégrité envoyés par sp_server_diagnostics à la DLL de ressource SQL Server sont automatiquement enregistrés dans le répertoire Log par défaut de l’instance SQL Server (%PROGRAMFILES%\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Log). Ces journaux, appelés « journaux SQLDIAG », sont enregistrés au format de fichier XEL (événements étendus). Les fichiers contenus dans le répertoire Log SQL Server sont au format suivant : \<NOMHÔTE>_\<NOMINSTANCE>_SQLDIAG_X_XXXXXXXXX.xel. L’examen des journaux SQLDIAG peut vous aider à déterminer la cause racine de l’événement d’échec ou de basculement de la ressource du groupe disponibilité.  
  
 Pour voir un journal SQLDIAG, faites glisser le fichier .xel dans SQL Server Management Studio.  
  
  
