---
title: Interrompre une trace
titleSuffix: SQL Server Profiler
description: Découvrez comment suspendre une trace afin que SQL Server Profiler arrête la capture des données d’événement et détermine les propriétés que vous pouvez modifier pendant la suspension de la trace.
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 432b9b0c-b5e7-47f3-a71b-310fb3bf2445
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 9a30e6d06137eddf2f8a9796c69cfe20fb9ab976
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774773"
---
# <a name="pause-a-trace-sql-server-profiler"></a>Suspendre une trace (SQL Server Profiler)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
Le fait de marquer une pause dans une trace empêche la capture de nouvelles données d’événement jusqu'au redémarrage de la trace.  
  
 Lorsque vous suspendez une trace, vous empêchez  la capture des données d’événements jusqu'à ce que vous redémarriez la trace. Le redémarrage d'une trace permet de reprendre les opérations de trace. Aucune donnée de trace précédente n'est perdue après le redémarrage. Lors du redémarrage de la trace, la capture des données reprend à partir du point où elle s'était arrêtée. Lorsqu'une trace est suspendue, vous pouvez modifier le nom, les événements, les colonnes et les filtres. Toutefois, vous ne pouvez pas modifier les destinations des données de la trace, ni la connexion au serveur.  
  
### <a name="to-pause-a-trace"></a>Pour interrompre une trace  
  
1.  Sélectionnez une fenêtre contenant une trace en cours d'exécution.  
  
2.  Dans le menu **Fichier** , cliquez sur **Suspendre la trace**.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
