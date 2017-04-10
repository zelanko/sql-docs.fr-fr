---
title: "Transactions entre bases de donn&#233;es et transactions distribu&#233;es pour des groupes de disponibilit&#233; Always On et la mise en miroir de bases de donn&#233;es (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mise en miroir de bases de données [SQL Server], interopérabilité"
  - "transactions entre bases de données [SQL Server]"
  - "transactions [mise en miroir de bases de données]"
  - "groupes de disponibilité [SQL Server], interopérabilité"
  - "résolution de problèmes [SQL Server], transactions entre bases de données"
ms.assetid: 9f7ed895-ad65-43e3-ba08-00d7bff1456d
caps.latest.revision: 33
ms.author: "mikeray"
manager: "jhubbard"
---
# Transactions entre bases de donn&#233;es et transactions distribu&#233;es pour des groupes de disponibilit&#233; Always On et la mise en miroir de bases de donn&#233;es (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Cette rubrique décrit la prise en charge des transactions entre bases de données et distribuées pour des groupes de disponibilité Always On et la mise en miroir de bases de données.  
  
## Prise en charge des transactions entre bases de données dans la même instance de SQL Server  
Les transactions entre bases de données dans une instance de SQL Server ne sont pas prises en charge pour les groupes de disponibilité Always On. Cela signifie que l’instance de SQL Server ne peut pas héberger les deux bases de données d’une telle transaction. Et ce, même si ces bases de données font partie du même groupe de disponibilité.  
  
En outre, les transactions de bases de données croisées ne sont non plus prises en charge pour la mise en miroir de bases de données.  
  
##  <a name="dtcsupport"></a> Prise en charge des transactions distribuées  
Les transactions distribuées sont prises en charge avec les groupes de disponibilité Always On. Cela s’applique aux transactions distribuées entre les bases de données hébergées par deux instances de SQL Server différentes. CeIa s’applique également aux transactions distribuées entre SQL Server et un autre serveur compatible DTC.  
 
MSDTC (Microsoft Distributed Transaction Coordinator ou DTC) est un service Windows qui fournit une infrastructure de transaction pour les systèmes distribués. MSDTC permet à des applications clientes d’inclure plusieurs sources de données dans une transaction qui est ensuite validée sur tous les serveurs inclus dans la transaction. Par exemple, vous pouvez utiliser MSDTC pour coordonner des transactions qui s’étendent sur plusieurs bases de données sur des serveurs différents.

SQL Server 2016 introduit la possibilité d’utiliser des transactions distribuées dans lesquelles une ou plusieurs bases de données de la transaction sont dans un groupe de disponibilité. Avant SQL Server 2016, les transactions distribuées n’étaient pas prises en charge pour les bases de données dans les groupes de disponibilité. SQL Server 2016 peut inscrire un gestionnaire de ressources par base de données. Cette nouvelle fonctionnalité permet aux transactions distribuées d’inclure des bases de données dans les groupes de disponibilité.

  
 Les conditions suivantes doivent être remplies :  
  
-   Les groupes de disponibilité doivent s’exécuter sur Windows Server 2016 ou Windows Server 2012 R2. Pour Windows Server 2012 R2, vous devez installer la mise à jour KB3090973 disponible à l’adresse [https://support.microsoft.com/en-us/kb/3090973](https://support.microsoft.com/en-us/kb/3090973).  
  
-   Les groupes de disponibilité doivent être créés avec la commande **CREATE AVAILABILITY GROUP** et la clause **WITH DTC_SUPPORT = PER_DB**. Actuellement, vous ne pouvez pas modifier un groupe de disponibilité.  

- Toutes les instances de SQL Server incluses dans le groupe de disponibilité doivent être équipées de SQL Server 2016 ou version ultérieure.
  
 
 ## Absence de prise en charge des transactions distribuées
 Les cas spécifiques où les transactions distribuées ne sont pas prises en charge sont notamment les suivants :
 
 -  Plusieurs bases de données impliquées dans la transaction figurent dans le même groupe de disponibilité.
 
 -  Au moins une base de données se trouve dans un groupe de disponibilité et une autre base de données se trouve sur la même instance de SQL Server. 
 
 -  Le groupe de disponibilité n’a pas été créé avec l’activation de la transaction distribuée.
 
 -  Mise en miroir de bases de données.
 
 ## Recommandation
 Dans les environnements de production, vous devez mettre en cluster le service DTC. Si vous ne mettez pas en cluster le service DTC, SQL Server utilise le service DTC local. Avec le service DTC local, la disponibilité globale de la solution est réduite. Quand le DTC est en cluster, les transactions en cours peuvent être récupérées si le nœud de cluster échoue.
 
 > [!IMPORTANT]
 > Déterminez le résultat par défaut approprié des transactions que DTC ne peut pas résoudre pour votre environnement.  Pour plus d’informations sur la façon de configurer le résultat par défaut, consultez [Résolution des transactions incertaines (option de configuration de serveur)](../../../database-engine/configure-windows/in-doubt-xact-resolution-server-configuration-option.md).
  
## Exemple de scénario de mise en miroir de bases de données  
 L'exemple de mise en miroir de bases de données suivant illustre la manière dont une incohérence logique pourrait se produire. Dans cet exemple, une application utilise une transaction entre bases de données pour insérer deux lignes de données : une ligne est insérée dans une table dans une base de données mise en miroir, A, et l'autre ligne est insérée dans une table dans une autre base de données, B. La base de données A est mise en miroir en mode haute sécurité avec basculement automatique. Pendant la validation de la transaction, la base de données A devient indisponible et la session de mise en miroir bascule automatiquement vers le miroir de la base de données A.  
  
 Après le basculement, il se peut que la transaction entre bases de données soit validée correctement dans la base de données B mais pas dans la base de données basculée. Cela pourrait se produire si le serveur principal d'origine de la base de données A n'avait pas envoyé le journal pour la transaction entre bases de données avant le basculement. Après le basculement, cette transaction n'existerait pas sur le nouveau serveur principal. Les bases de données A et B deviendraient incohérentes car les données insérées dans la base de donnes B demeureraient intactes, alors que celles insérées dans la base de données A auraient été perdues.  
  
 Un scénario semblable peut se présenter lors de l'utilisation d'une transaction MS DTC. Par exemple, après un basculement, le nouveau principal contacte MS DTC. Mais MS DTC n'a aucune connaissance du nouveau serveur principal et interrompt toute transaction en « préparation pour validation », considérée comme validée dans d'autres bases de données.  
  
> [!NOTE]  
>  L’utilisation de la mise en miroir de bases de données ou des groupes de disponibilité Always On avec DTC d’une manière non approuvée dans cette rubrique n’est pas prise en charge.  Cela ne signifie pas que certains aspects du produit sans rapport avec DTC ne sont pas pris en charge, mais qu’aucun problème résultant de l’utilisation incorrecte des transactions distribuées ne sera traité.  
  
## Voir aussi  
 [Groupes de disponibilité Always On : interopérabilité &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md)  
  
  