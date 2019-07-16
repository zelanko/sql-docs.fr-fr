---
title: Déterminer la fréquence d’interrogation - Analytique Platform System | Microsoft Docs
description: Cet article explique comment déterminer la fréquence d’interrogation pour les alertes de l’appliance Analytique Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2d305c766801ce27268e2d3bc873d9c361c034f0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961070"
---
# <a name="determine-polling-frequency"></a>Déterminer la fréquence d’interrogation
Cet article explique comment déterminer la fréquence d’interrogation pour les alertes de l’appliance Analytique Platform System.  
  
## <a name="to-determine-the-polling-frequency"></a>Pour déterminer la fréquence d’interrogation  
Dans la mesure où PDW ne prend pas en charge proactive notifications lorsque des alertes se produisent, la solution de surveillance doit interroger en permanence la DLL de l’appliance.  En interne, PDW interroge les composants à des intervalles différents :  
  
-   Cluster - 60 secondes  
  
-   Pulsation - 60 secondes  
  
-   Tous les autres composants - cinq minutes  
  
-   Compteurs de performances - trois secondes  
  
Un intervalle commun à interroger pour les alertes, qui est également utilisé par System Center, est **toutes les 15 minutes**.  Évidemment, vous pouvez interroger plus ou moins fréquemment, mais il n’est pas recommandé d’interroger moins de toutes les six heures.  
  
Interrogation plus fréquente est acceptable, mais interrogation trop fréquente peut encombrer le [sys.dm_pdw_nodes_exec_requests](https://msdn.microsoft.com/library/ms177648(v=sql11).aspx) DMV.  Interrogation trop fréquente peut rendre difficile pour les utilisateurs diagnostiquer les performances de requête des problèmes lorsque leurs se déroule rapidement hors de la vue.  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Surveillance de l’appliance &#40;Analytique Platform System&#41;](appliance-monitoring.md)  
  
