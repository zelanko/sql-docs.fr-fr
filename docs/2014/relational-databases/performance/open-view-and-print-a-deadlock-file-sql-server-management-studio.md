---
title: Ouvrir, afficher et imprimer un fichier d’interblocage (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a81f92fb80e094b0347baea38632bac41c7661c0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044705"
---
# <a name="open-view-and-print-a-deadlock-file-sql-server-management-studio"></a>Ouvrir, afficher et imprimer un fichier d'interblocage (SQL Server Management Studio)
  Lorsque le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] génère un interblocage, vous pouvez capturer et enregistrer les informations correspondantes dans un fichier. Une fois le fichier de blocage enregistré, vous pouvez l'ouvrir dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour le consulter ou l'imprimer.  
  
### <a name="to-open-and-view-a-deadlock-file"></a>Pour ouvrir et consulter un fichier de blocage  
  
1.  Dans le menu **Fichier** de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], pointez sur **Ouvrir**, puis cliquez sur **Fichier**.  
  
2.  Dans la boîte de dialogue **Ouvrir un fichier** , sélectionnez le type de fichier .xdl dans la zone **Fichiers de type** . Vous obtenez alors une liste filtrée comportant uniquement les fichiers de blocage.  
  
### <a name="to-print-a-deadlock-file"></a>Pour imprimer un fichier de blocage  
  
1.  Dans le menu **Fichier** de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], pointez sur **Ouvrir** , puis cliquez sur **Fichier**.  
  
2.  Dans la boîte de dialogue **Ouvrir un fichier** , sélectionnez le type de fichier .xdl dans la zone **Fichiers de type** . Vous obtenez alors une liste filtrée comportant uniquement les fichiers de blocage.  
  
3.  Sélectionnez le fichier de blocage à imprimer, puis cliquez sur **Ouvrir**.  
  
4.  Dans le menu **Fichier** , cliquez sur **Imprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer les événements Deadlock Graph &#40;Générateur de profils SQL Server&#41;](save-deadlock-graphs-sql-server-profiler.md)  
  
  