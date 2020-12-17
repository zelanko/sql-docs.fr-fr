---
title: Déterminer la fréquence d’interrogation
description: Cet article explique comment déterminer la fréquence d’interrogation pour les alertes de l’appliance système Analytics Platform.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ee5c83fee1028b7e165db6dfb8015129c29e4eca
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97641476"
---
# <a name="determine-polling-frequency"></a>Déterminer la fréquence d’interrogation
Cet article explique comment déterminer la fréquence d’interrogation pour les alertes de l’appliance système Analytics Platform.  
  
## <a name="to-determine-the-polling-frequency"></a>Pour déterminer la fréquence d’interrogation  
Étant donné que PDW ne prend pas en charge les notifications proactives lorsque des alertes se produisent, la solution de surveillance doit interroger continuellement les dll de l’appliance.  En interne, PDW interroge les composants à des intervalles différents :  
  
-   Cluster-60 secondes  
  
-   Pulsation-60 secondes  
  
-   Tous les autres composants-cinq minutes  
  
-   Compteurs de performances-trois secondes  
  
L’intervalle courant d’interrogation des alertes, qui est également utilisé par System Center, est de **15 minutes**.  Évidemment, vous pouvez interroger plus ou moins fréquemment, mais il n’est pas recommandé de demander une interrogation inférieure à toutes les six heures.  
  
Une interrogation plus fréquente est acceptable, mais les interrogations trop fréquentes peuvent encombrer la DMV [sys.dm_pdw_nodes_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) .  Les interrogations trop fréquentes peuvent compliquer le diagnostic des problèmes de performances des requêtes lorsqu’ils sont rapidement déverrouillés.  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Système de plateforme d’analyse de &#40;Analytics de l’appliance&#41;](appliance-monitoring.md)  
