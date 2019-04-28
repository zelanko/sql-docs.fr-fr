---
title: Les Transactions entre bases de données non pris en charge pour AlwaysOn ou de mise en miroir de base de données des groupes de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- cross-database transactions [SQL Server]
- transactions [database mirroring]
- Availability Groups [SQL Server], interoperability
- troubleshooting [SQL Server], cross-database transactions
ms.assetid: 9f7ed895-ad65-43e3-ba08-00d7bff1456d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8c3616e40ff54c67d27902ddf9454084fb62e282
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813654"
---
# <a name="cross-database-transactions-not-supported-for-database-mirroring-or-alwayson-availability-groups-sql-server"></a>Transactions entre bases de données non prises en charge pour la mise en miroir de bases de données ou les groupes de disponibilité AlwaysOn (SQL Server)
  Les transactions entre bases de données et les transactions distribuées ne sont pas prises en charge par [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] et par la mise en miroir de bases de données. En effet, l'atomicité/intégrité des transactions ne peut pas être garantie pour les raisons suivantes :  
  
-   Pour les transactions entre bases de données : Chaque base de données est validée indépendamment. Par conséquent, même pour les bases de données dans un seul groupe de disponibilité, un basculement peut se produire après qu'une base de données a validé une transaction, mais avant que l'autre base de données ne le fasse. Pour la mise en miroir de bases de données, ce problème est aggravé car après un basculement, la base de données mise en miroir figure généralement sur une instance de serveur différente de l'autre base de données, et même si les deux bases de données sont mises en miroir entre les mêmes deux partenaires, il n'y a aucune garantie que les deux bases de données basculent au même moment.  
  
-   Pour les transactions distribuées : Après un basculement, le nouveau principal/réplica principal est incapable de se connecter au coordinateur de transaction distribuée sur le précédent principal/réplica principal. Par conséquent, le nouveau principal/réplica principal ne peut pas obtenir l'état de la transaction.  
  
 L'exemple de mise en miroir de bases de données suivant illustre la manière dont une incohérence logique pourrait se produire. Dans cet exemple, une application utilise une transaction entre bases de données pour insérer deux lignes de données : une ligne est insérée dans une table dans une base de données mise en miroir, A, et l'autre ligne est insérée dans une table dans une autre base de données, B. La base de données A est mise en miroir en mode haute sécurité avec basculement automatique. Pendant la validation de la transaction, la base de données A devient indisponible et la session de mise en miroir bascule automatiquement vers le miroir de la base de données A.  
  
 Après le basculement, il se peut que la transaction entre bases de données soit validée correctement dans la base de données B mais pas dans la base de données basculée. Cela pourrait se produire si le serveur principal d'origine de la base de données A n'avait pas envoyé le journal pour la transaction entre bases de données avant le basculement. Après le basculement, cette transaction n'existerait pas sur le nouveau serveur principal. Les bases de données A et B deviendraient incohérentes car les données insérées dans la base de donnes B demeureraient intactes, alors que celles insérées dans la base de données A auraient été perdues.  
  
 Un scénario semblable peut se présenter lors de l'utilisation d'une transaction MS DTC. Par exemple, après un basculement, le nouveau principal contacte MS DTC. Mais MS DTC n'a aucune connaissance du nouveau serveur principal et interrompt toute transaction en « préparation pour validation », considérée comme validée dans d'autres bases de données.  
  
> [!IMPORTANT]  
>  Le fait d'utiliser la mise en miroir de bases de données ou les groupes de disponibilité avec DTC n'entraîne pas une installation non prise en charge de SQL Server. Si, cependant, une base de données fait partie d'une session de mise en miroir de bases de données ou d'un groupe de disponibilité et DTC est également utilisé dans la base de données, les problèmes de prise en charge seront examinés par Microsoft uniquement s'ils ne sont pas associés à l'utilisation combinée de la mise en miroir de bases de données ou des groupes de disponibilité avec DTC.  
  
  
