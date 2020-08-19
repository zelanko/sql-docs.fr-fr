---
description: Actualisation du moniteur d'activité des travaux
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
ms.openlocfilehash: 78141d10b6244308f075e420f1d1ea3501830286
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424041"
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
  
  
