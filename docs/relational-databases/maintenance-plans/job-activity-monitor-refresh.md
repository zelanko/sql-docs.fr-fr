---
title: Actualisation du moniteur d’activité des travaux | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6343929a2f893d020d992a7bd68ba70e178ed2c3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85666914"
---
# <a name="job-activity-monitor-refresh"></a>Actualisation du moniteur d'activité des travaux
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  La boîte de dialogue **Paramètres d'actualisation** vous permet de configurer la fréquence à laquelle le moniteur d'activité des travaux obtient de nouvelles informations sur l'activité du serveur. Le moniteur d'activité des travaux doit exécuter des requêtes sur le serveur surveillé pour obtenir des informations pour la grille du moniteur d'activité des travaux. Si la fréquence d’actualisation automatique est inférieure à 30 secondes, le temps nécessaire à l’exécution des requêtes peut affecter les performances du serveur.  
  
 Pour ouvrir cette boîte de dialogue, cliquez sur **Afficher les paramètres d'actualisation**dans la section **État** du moniteur d'activité des travaux.  
  
## <a name="options"></a>Options  
 **Actualiser automatiquement toutes les**  
 Activez pour initier l'actualisation automatique des informations du moniteur d'activité. Cette option est désactivée par défaut.  
  
 **secondes**  
 Nombre de secondes entre deux tentatives d'actualisation automatique. La valeur par défaut est de 60 secondes. L'actualisation s'effectue toutes les 5 secondes lorsque la valeur spécifiée est inférieure ou égale à 5.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller l'activité des travaux](../../ssms/agent/monitor-job-activity.md)  
  
  
