---
title: Ouvrir, afficher et imprimer un fichier d’interblocage (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: b89c44ca71dcac588dea2c364f8fef7220331b3f
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39560769"
---
# <a name="open-view-and-print-a-deadlock-file-sql-server-management-studio"></a>Ouvrir, afficher et imprimer un fichier d’interblocage (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Lorsque le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] génère un interblocage, vous pouvez capturer et enregistrer les informations correspondantes dans un fichier. Une fois le fichier d’interblocage enregistré, vous pouvez l’ouvrir dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour le consulter ou l’imprimer.  
  
## <a name="open-and-view-a-deadlock-file"></a>Ouvrir et consulter un fichier d’interblocage  
  
1. Dans le menu **Fichier** de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], pointez sur **Ouvrir**, puis sélectionnez **Fichier**.  
  
2. Dans la boîte de dialogue **Ouvrir un fichier** , sélectionnez le type de fichier .xdl dans la zone **Fichiers de type** . Vous obtenez alors une liste filtrée comportant uniquement les fichiers d’interblocage.  
  
## <a name="print-a-deadlock-file"></a>Imprimer un fichier d’interblocage  
  
1. Dans le menu **Fichier** de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], pointez sur **Ouvrir**, puis sélectionnez **Fichier**.  
  
2. Dans la boîte de dialogue **Ouvrir un fichier** , sélectionnez le type de fichier .xdl dans la zone **Fichiers de type** . Vous obtenez alors une liste filtrée comportant uniquement les fichiers d’interblocage.  
  
3. Sélectionnez le fichier d’interblocage à imprimer, puis sélectionnez **Ouvrir**.  
  
4. Dans le menu **Fichier**, sélectionnez **Imprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer les événements Deadlock Graph &#40;SQL Server Profiler&#41;](../../relational-databases/performance/save-deadlock-graphs-sql-server-profiler.md)  
  
  
