---
title: "Déterminer la fréquence d’interrogation (système de plateforme Analytique)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 062c0e3d-f7d0-44f1-aeab-a9bd17dc6fdd
caps.latest.revision: "7"
ms.openlocfilehash: fb32abc38a90cd7450dc310a9f73eb7a5d72b5fb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
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
[Surveillance de l’appliance &#40; Système de plateforme Analytique &#41;](appliance-monitoring.md)  
  
