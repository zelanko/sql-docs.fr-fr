---
title: Traçage et relecture des événements | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d83b716d9919bf322097b8ded8409950982d961c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "70148359"
---
# <a name="tracing-and-replaying-events"></a>Événements de traçage et de relecture
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Dans SMO, les objets de **trace** et de **relecture** <xref:Microsoft.SqlServer.Management.Trace> de l’espace de noms fournissent [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] un accès par programme à la fonctionnalité, qui est [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilisée [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]pour surveiller une instance de ou. Vous pouvez capturer et enregistrer des données sur chaque événement dans un fichier ou dans une table en vue d'une analyse ultérieure. Par exemple, vous pouvez surveiller un environnement de production pour savoir quelles sont les procédures qui compromettent les performances en s'exécutant trop lentement.  
  
 Les objets **Trace** et **Replay** fournissent un jeu d'objets qui peuvent être utilisés pour créer des traces sur une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ces objets peuvent être utilisés au sein de vos propres applications pour créer manuellement des traces pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. En outre, les objets Smo **trace** peuvent être utilisés pour lire les fichiers de trace SQL et les tables qui [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ont [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]été créées par l’analyse, ou la journalisation Dts.  
  
 Les objets SMO **Trace** vous permettent de réaliser les fonctions suivantes :  
  
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
  
 Les données de trace des objets **Trace** et **Replay** peuvent être utilisées par l'application SMO ou être examinées manuellement en utilisant [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md). Les données de trace sont également compatibles avec les procédures stockées [SQL Trace](../../../relational-databases/sql-trace/sql-trace.md) qui proposent également des fonctionnalités de suivi.  
  
 Les objets de trace SMO résident dans l'espace de noms <xref:Microsoft.SqlServer.Management.Trace>, qui requiert une référence au fichier Microsoft.SQLServer.ConnectionInfo.dll.  
  
 Les objets **trace** et **Replay** requièrent un objet [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) <xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> pour établir une connexion avec l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. L’objet [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) réside dans l’espace de noms [Microsoft. SqlServer. Management. Common](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common) , qui requiert une référence au fichier Microsoft. SqlServer. ConnectionInfo. dll.  
  
> [!NOTE]  
>  Les objets **Trace** et **Replay** ne sont pas pris en charge sur une plate-forme 64 bits.  
  
  
