---
title: Déterminer la fréquence d’interrogation (système de plateforme Analytique)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 062c0e3d-f7d0-44f1-aeab-a9bd17dc6fdd
caps.latest.revision: 7
ms.openlocfilehash: e67ab38c12000f3d78a9179a177ce5f673b8eaa2
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="determine-polling-frequency"></a>Déterminer la fréquence d’interrogation
Cette rubrique explique comment déterminer la fréquence d’interrogation pour les alertes de SQL Server PDW appliance.  
  
## <a name="to-determine-the-polling-frequency"></a>Pour déterminer la fréquence d’interrogation  
PDW ne prend pas en charge les notifications proactive lorsque des alertes se produisent, la solution d’analyse doit interroger en permanence de l’application DLL.  En interne, PDW interroge les composants à des intervalles différents :  
  
-   Cluster : 60 secondes  
  
-   Pulsation – 60 secondes  
  
-   Tous les autres composants – 5 minutes  
  
-   Compteurs de performances – 3 secondes  
  
Un intervalle d’interrogation pour les alertes, commun, qui est également utilisé par System Center, est **toutes les 15 minutes**.  Évidemment, vous pouvez interroger plus ou moins fréquemment, mais il n’est pas recommandé d’interrogation inférieur à toutes les 6 heures.  
  
Interrogation plus fréquente est acceptable, mais d’interrogation trop fréquemment peut encombrer la [sys.dm_pdw_nodes_exec_requests](http://msdn.microsoft.com/en-us/library/ms177648(v=sql11).aspx) DMV.  Cela peut rendre difficiles à diagnostiquer les problèmes de performances de requête si il interroger rapidement restaure hors de l’affichage.  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Surveillance de l’appliance &#40;Analytique plate-forme système&#41;](appliance-monitoring.md)  
  
