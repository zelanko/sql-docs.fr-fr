---
title: "Actualisation du moniteur d’activité des travaux | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 85e2fd2b5ca1e3c0c1a01af8dd386ac2240cecdc
ms.lasthandoff: 04/11/2017

---
# <a name="job-activity-monitor-refresh"></a>Actualisation du moniteur d'activité des travaux
  La boîte de dialogue **Paramètres d'actualisation** vous permet de configurer la fréquence à laquelle le moniteur d'activité des travaux obtient de nouvelles informations sur l'activité du serveur. Le moniteur d'activité des travaux doit exécuter des requêtes sur le serveur surveillé pour obtenir des informations pour la grille du moniteur d'activité des travaux. Si la fréquence d’actualisation automatique est inférieure à 30 secondes, le temps nécessaire à l’exécution des requêtes peut affecter les performances du serveur.  
  
 Pour ouvrir cette boîte de dialogue, cliquez sur **Afficher les paramètres d'actualisation**dans la section **État** du moniteur d'activité des travaux.  
  
## <a name="options"></a>Options  
 **Actualiser automatiquement toutes les**  
 Activez pour initier l'actualisation automatique des informations du moniteur d'activité. Cette option est désactivée par défaut.  
  
 **secondes**  
 Nombre de secondes entre deux tentatives d'actualisation automatique. La valeur par défaut est de 60 secondes. L'actualisation s'effectue toutes les 5 secondes lorsque la valeur spécifiée est inférieure ou égale à 5.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller l'activité des travaux](http://msdn.microsoft.com/library/71cb432b-631d-4b8b-9965-e731b3d8266d)  
  
  
