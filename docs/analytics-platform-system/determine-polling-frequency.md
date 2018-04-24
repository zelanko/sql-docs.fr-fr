---
title: Déterminer la fréquence d’interrogation - système de plateforme Analytique | Documents Microsoft
description: Cet article explique comment déterminer la fréquence d’interrogation pour les alertes de matériel de système de plateforme Analytique.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e8e2a1ccf469e6c587870c0d5921014d797f87d1
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="determine-polling-frequency"></a>Déterminer la fréquence d’interrogation
Cet article explique comment déterminer la fréquence d’interrogation pour les alertes de matériel de système de plateforme Analytique.  
  
## <a name="to-determine-the-polling-frequency"></a>Pour déterminer la fréquence d’interrogation  
PDW ne prend pas en charge les notifications proactive lorsque des alertes se produisent, la solution d’analyse doit interroger en permanence de l’application DLL.  En interne, PDW interroge les composants à des intervalles différents :  
  
-   Cluster : 60 secondes  
  
-   Pulsation – 60 secondes  
  
-   Tous les autres composants – 5 minutes  
  
-   Compteurs de performances – trois secondes  
  
Un intervalle d’interrogation pour les alertes, commun, qui est également utilisé par System Center, est **toutes les 15 minutes**.  Évidemment, vous pouvez interroger plus ou moins fréquemment, mais il n’est pas recommandé d’interrogation inférieur à toutes les six heures.  
  
Interrogation plus fréquente est acceptable, mais d’interrogation trop fréquemment peut encombrer la [sys.dm_pdw_nodes_exec_requests](http://msdn.microsoft.com/en-us/library/ms177648(v=sql11).aspx) DMV.  Interrogation trop fréquente peut rendre difficile pour les utilisateurs diagnostiquer les performances des requêtes les problèmes lorsque leurs restaure rapidement hors de l’affichage.  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Surveillance de l’appliance &#40;Analytique plate-forme système&#41;](appliance-monitoring.md)  
  
