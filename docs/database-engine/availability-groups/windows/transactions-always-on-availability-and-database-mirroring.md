---
title: "Transactions - Groupes de disponibilité Always On et mise en miroir de bases de données | Microsoft Docs"
ms.custom: 
ms.date: 07/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- cross-database transactions [SQL Server]
- transactions [database mirroring]
- Availability Groups [SQL Server], interoperability
- troubleshooting [SQL Server], cross-database transactions
ms.assetid: 9f7ed895-ad65-43e3-ba08-00d7bff1456d
caps.latest.revision: 33
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bc86ef8e495bacaaaebf2470306b25d38d5158e5
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="transactions---availability-groups-and-database-mirroring"></a>Transactions - Groupes de disponibilité Always On et mise en miroir de bases de données
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

Cette rubrique décrit la prise en charge des transactions entre bases de données et distribuées pour des groupes de disponibilité Always On et la mise en miroir de bases de données.  

## <a name="support-for-distributed-transactions"></a>Prise en charge des transactions distribuées

SQL Server 2017 prend en charge les transactions distribuées pour les bases de données des groupes de disponibilité. Cette prise en charge comprend les bases de données sur la même instance de SQL Server ou les bases de données sur différentes instances de SQL Server. Les transactions distribuées ne sont pas prises en charge pour les bases de données configurées pour la mise en miroir de bases de données.

>[!NOTE]
>[! INCLUDE [SQL Server 2016]](../../../includes/sssql15-md.md)] SQL Server 2016 offrait une prise en charge limitée des transactions distribuées pour les bases de données d’un groupe de disponibilité. Les transactions distribuées utilisant des bases de données dans un groupe de disponibilité étaient prises en charge pour autant qu’aucune autre base de données de la transaction ne se trouvait dans la même instance de SQL Server. Pour plus d’informations, consultez [Prise en charge de SQL Server 2016 DTC dans les groupes de disponibilité](http://blogs.technet.microsoft.com/dataplatform/2016/01/25/sql-server-2016-dtc-support-in-availability-gr)

Pour configurer un groupe de disponibilité pour les transactions distribuées, consultez [Configurer de groupe de disponibilité pour les transactions distribuées](configure-availability-group-for-distributed-transactions.md).

Pour plus d’informations, consultez :

- [Guide d’Administration de DTC](http://msdn.microsoft.com/library/ms681291.aspx)
- [Guide du développeur de DTC](http://msdn.microsoft.com/library/ms679938.aspx)
- [Informations de référence pour les programmeurs de DTC](http://msdn.microsoft.com/library/ms686108.aspx)

## <a name="sql-server-2016-and-before-support-for-cross-database-transactions-within-the-same-sql-server-instance"></a>SQL Server 2016 et versions antérieures : prise en charge des transactions entre bases de données dans la même instance de SQL Server  

Dans SQL Server 2016 et les versions antérieures, les transactions entre bases de données dans la même instance de SQL Server ne sont pas prises en charge pour les groupes de disponibilité. Cela signifie que l’instance de SQL Server ne peut pas héberger les deux bases de données d’une telle transaction. Et ce, même si ces bases de données font partie du même groupe de disponibilité.  
  
En outre, les transactions de bases de données croisées ne sont non plus prises en charge pour la mise en miroir de bases de données.  
  
##  <a name="dtcsupport"></a> SQL Server 2016 : prise en charge des transactions distribuées  
Les transactions distribuées sont prises en charge avec les groupes de disponibilité. Cela s’applique aux transactions distribuées entre les bases de données hébergées par deux instances de SQL Server différentes. CeIa s’applique également aux transactions distribuées entre SQL Server et un autre serveur compatible DTC.  
 
MSDTC (Microsoft Distributed Transaction Coordinator ou DTC) est un service Windows qui fournit une infrastructure de transaction pour les systèmes distribués. MSDTC permet à des applications clientes d’inclure plusieurs sources de données dans une transaction qui est ensuite validée sur tous les serveurs inclus dans la transaction. Par exemple, vous pouvez utiliser MSDTC pour coordonner des transactions qui s’étendent sur plusieurs bases de données sur des serveurs différents.

SQL Server 2016 introduit la possibilité d’utiliser des transactions distribuées dans lesquelles une ou plusieurs bases de données de la transaction sont dans un groupe de disponibilité. Avant SQL Server 2016, les transactions distribuées n’étaient pas prises en charge pour les bases de données dans les groupes de disponibilité. SQL Server 2016 peut inscrire un gestionnaire de ressources par base de données. Cette nouvelle fonctionnalité permet aux transactions distribuées d’inclure des bases de données dans les groupes de disponibilité.
  
 Les conditions suivantes doivent être remplies :  
  
-   Les groupes de disponibilité doivent s’exécuter sur Windows Server 2016 ou Windows Server 2012 R2. Pour Windows Server 2012 R2, vous devez installer la mise à jour KB3090973 disponible à l’adresse [https://support.microsoft.com/en-us/kb/3090973](https://support.microsoft.com/en-us/kb/3090973).  
  
-   Availability groups must be created with the **CREATE AVAILABILITY GROUP** et la clause **WITH DTC_SUPPORT = PER_DB** . Actuellement, vous ne pouvez pas modifier un groupe de disponibilité.  

- Toutes les instances de SQL Server incluses dans le groupe de disponibilité doivent être équipées de SQL Server 2016 ou version ultérieure.
 
 ## <a name="non-support-for-distributed-transactions"></a>Absence de prise en charge des transactions distribuées
 Les cas spécifiques où les transactions distribuées ne sont pas prises en charge sont notamment les suivants :
 
 - Dans SQL Server 2016 et les versions antérieures, quand plusieurs bases de données impliquées dans la transaction se trouvent dans le même groupe de disponibilité.
 
 - Dans SQL Server 2016 et les versions antérieures, quand au moins une base de données se trouve dans un groupe de disponibilité et qu’une autre se trouve sur la même instance de SQL Server. 
 
 - Le groupe de disponibilité n’a pas été créé avec l’activation de la transaction distribuée.
 
 - Mise en miroir de bases de données.
 
 > [!IMPORTANT]
 > Déterminez le résultat par défaut approprié des transactions que DTC ne peut pas résoudre pour votre environnement.  Pour plus d’informations sur la façon de configurer le résultat par défaut, consultez [ (option de configuration de serveur)](../../../database-engine/configure-windows/in-doubt-xact-resolution-server-configuration-option.md).
  
## <a name="example-scenario-with-database-mirroring"></a>Exemple de scénario de mise en miroir de bases de données  
 L'exemple de mise en miroir de bases de données suivant illustre la manière dont une incohérence logique pourrait se produire. Dans cet exemple, une application utilise une transaction entre bases de données pour insérer deux lignes de données : une ligne est insérée dans une table dans une base de données mise en miroir, A, et l'autre ligne est insérée dans une table dans une autre base de données, B. La base de données A est mise en miroir en mode haute sécurité avec basculement automatique. Pendant la validation de la transaction, la base de données A devient indisponible et la session de mise en miroir bascule automatiquement vers le miroir de la base de données A.  
  
 Après le basculement, il se peut que la transaction entre bases de données soit validée correctement dans la base de données B mais pas dans la base de données basculée. Cela pourrait se produire si le serveur principal d'origine de la base de données A n'avait pas envoyé le journal pour la transaction entre bases de données avant le basculement. Après le basculement, cette transaction n'existerait pas sur le nouveau serveur principal. Les bases de données A et B deviendraient incohérentes car les données insérées dans la base de donnes B demeureraient intactes, alors que celles insérées dans la base de données A auraient été perdues.  
  
 Un scénario semblable peut se présenter lors de l'utilisation d'une transaction MS DTC. Par exemple, après un basculement, le nouveau principal contacte MS DTC. Mais MS DTC n'a aucune connaissance du nouveau serveur principal et interrompt toute transaction en « préparation pour validation », considérée comme validée dans d'autres bases de données.  
  
> [!NOTE]  
>  L’utilisation de la mise en miroir de bases de données ou de groupes de disponibilité avec DTC d’une façon non approuvée dans cette rubrique n’est pas prise en charge.  Cela ne signifie pas que certains aspects du produit sans rapport avec DTC ne sont pas pris en charge, mais qu’aucun problème résultant de l’utilisation incorrecte des transactions distribuées ne sera traité.  
  
## <a name="see-also"></a>Voir aussi  
 [Groupes de disponibilité Always On : interopérabilité &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md)  
  
  

