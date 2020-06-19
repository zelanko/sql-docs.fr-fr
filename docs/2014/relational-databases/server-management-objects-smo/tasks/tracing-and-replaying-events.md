---
title: Traçage et relecture des événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd75fdae7fc871101aa07785561c8277783a424f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063060"
---
# <a name="tracing-and-replaying-events"></a>Événements de traçage et de relecture
  Dans SMO, les objets `Trace` et `Replay` de l'espace de noms <xref:Microsoft.SqlServer.Management.Trace> fournissent l'accès par programme à la fonctionnalité [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)], qui est utilisée pour surveiller une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Vous pouvez capturer et enregistrer des données sur chaque événement dans un fichier ou dans une table en vue d'une analyse ultérieure. Par exemple, vous pouvez surveiller un environnement de production pour savoir quelles sont les procédures qui compromettent les performances en s'exécutant trop lentement.  
  
 Les objets `Trace` et `Replay` fournissent un jeu d'objets qui peuvent être utilisés pour créer des traces sur une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ces objets peuvent être utilisés au sein de vos propres applications pour créer manuellement des traces pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. En outre, les objets SMO `Trace` peuvent être utilisés pour lire des fichiers et des tables SQL Trace créés en surveillant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ou l'enregistrement DTS.  
  
 Les objets SMO `Trace` vous permettent de réaliser les fonctions suivantes :  
  
-   Créer une trace.  
  
-   Définir des filtres sur la trace.  
  
-   Définir les événements qui sont tracés.  
  
-   Arrêter ou démarrer une trace.  
  
-   Lire des fichiers ou des tables de trace.  
  
-   Obtenir des informations sur les événements d'une trace.  
  
-   Obtenir des informations sur les filtres d'une trace.  
  
-   Manipuler des données de trace par programme.  
  
-   Écrire des fichiers ou des tables de trace.  
  
-   Relire des fichiers ou des tables de trace.  
  
 Les données de trace des `Trace` `Replay` objets et peuvent être utilisées par l’application Smo, ou elles peuvent être examinées manuellement à l’aide de [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md). Les données de trace sont également compatibles avec les procédures stockées [SQL Trace](../../sql-trace/sql-trace.md) qui proposent également des fonctionnalités de suivi.  
  
 Les objets de trace SMO résident dans l'espace de noms <xref:Microsoft.SqlServer.Management.Trace>, qui requiert une référence au fichier Microsoft.SQLServer.ConnectionInfo.dll.  
  
 Les objets `Trace` et `Replay` requièrent un objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection><xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> pour établir une connexion à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. L'objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection> réside dans l'espace de noms <xref:Microsoft.SqlServer.Management.Common>, qui requiert une référence au fichier Microsoft.SQLServer.ConnectionInfo.dll.  
  
> [!NOTE]  
>  Les objets `Trace` et `Replay` ne sont pas pris en charge sur une plate-forme 64 bits.  
  
  
