---
title: "Interop&#233;rabilit&#233; de R dans les Services SQL Server R | Microsoft Docs"
ms.custom: ""
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0506b950-34b3-4f11-8e2f-d067a58015bd
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# Interop&#233;rabilit&#233; de R dans les Services SQL Server R

Cette rubrique se concentre sur le mécanisme d’exécution pour R dans [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], et décrit les différences entre Microsoft R et open source R. Pour plus d’informations sur les composants supplémentaires, consultez la page [de nouveaux composants de SQL Server](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md).

### Composants Open Source de R

[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] inclut une distribution complète des outils et des packages R base. Pour plus d’informations sur ce qui est inclus avec la distribution de base, consultez la documentation installée lors de l’installation à l’emplacement par défaut suivant :
`C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES\doc\manual`

Dans le cadre de l’installation de [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], vous devez accepter les termes du contrat de la licence publique GNU. Par la suite, vous pouvez exécuter des packages R standards sans modification supplémentaire comme vous le feriez dans n’importe quelle autre distribution open source de R.

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ne modifie pas l’exécution de R en aucune façon. Le runtime R est exécuté en dehors de la [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] traiter et peut être exécuté indépendamment de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Toutefois, nous recommandons fortement que vous n’exécutez pas ces outils pendant [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] est à l’aide de R, afin d’éviter les conflits de ressources.

La distribution du package de base R qui est associée à son propre [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] instance se trouve dans le dossier associé à l’instance. Par exemple, si vous avez installé les Services de R sur l’instance par défaut, les bibliothèques R se trouvent dans `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`.

De même, les outils R associés à l’instance par défaut se trouvent dans `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin`,

Pour plus d’informations sur la distribution de base, consultez [Packages installés avec Microsoft R Open](https://mran.revolutionanalytics.com/rro/installed/)

### Packages R supplémentaires

Outre la distribution R de base, [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] inclut certains packages R propriétaires, ainsi que d’une infrastructure pour l’exécution parallèle de R et de bibliothèques qui prennent en charge l’exécution de R dans les contextes de calcul à distance. 

Ce jeu combiné de fonctionnalités R - la distribution de base R ainsi que les fonctionnalités améliorées de R et les packages - est appelé **Microsoft R**. Si vous installez Microsoft R serveur (autonome), vous obtenez exactement le même ensemble de packages qui sont installés avec SQL Server Services R (de base de données), mais dans un dossier différent. 

Microsoft R inclut une distribution de la bibliothèque Intel mathématiques du noyau, qui est utilisée chaque fois que possible pour un traitement plus rapide mathématique. Par exemple, la bibliothèque de base algèbre linéaire (BLAS) est utilisée pour la plupart des packages de module complémentaire ainsi que pour R lui-même. Pour plus d’informations, consultez les articles suivants :

+ [Comment le noyau de mathématiques Intel accélère R](http://blog.revolutionanalytics.com/2014/10/revolution-r-open-mkl.html)
+ [Avantages de la liaison R pour les bibliothèques de calcul multithread](http://blog.revolutionanalytics.com/2010/06/performance-benefits-of-multithreaded-r.html)

Parmi les ajouts les plus importantes à Microsoft R la **RevoScaleR** et **RevoPemaR** packages. Il s’agit de packages R qui ont été écrits en grande partie en C ou C++ pour optimiser les performances.

+ **RevoScaleR.** Inclut une variété d’API de manipulation de données et d’analyse. Les API ont été optimisées pour analyser les jeux de données qui sont trop volumineuses pour tenir en mémoire et pour effectuer des calculs réparties sur plusieurs cœurs ou processeurs.

   Les APIs RevoScaleR prennent également en charge l’utilisation des sous-ensembles de données pour une plus grande évolutivité. En d’autres termes, la plupart des fonctions RevoScaleR peut fonctionner sur des segments de données et l’utilisation de mise à jour des algorithmes pour agréger les résultats. Par conséquent solutions R basées sur les fonctions RevoScaleR peuvent fonctionner avec des jeux de données très volumineux et ne sont pas liées à la mémoire locale.

  Le package RevoScaleR prend également en charge les. Format de fichier XDF de mouvement plus rapide et le stockage des données utilisées pour l’analyse. Le format XDF utilise le stockage en colonnes est portable et permettre être utilisé pour charger et manipulez ensuite les données à partir de diverses sources, y compris une connexion ODBC, SPS ou texte. Un exemple montrant comment utiliser le format XDF est fourni dans ce didacticiel : [approfondie de science des données](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)


+ **RevoPemaR.** Algorithme de mémoire externe parallèle signifie ZGEP. Le **RevoPemaR** package fournit des API que vous pouvez utiliser pour développer vos propres algorithmes parallèles. Pour plus d’informations, consultez [RevoPemaR Getting Started Guide](https://msdn.microsoft.com/microsoft-r/rserver/rserver-pemar-getting-started).

## Voir aussi
[Vue d'ensemble de l'architecture](../../advanced-analytics/r-services/architecture-overview-sql-server-r-services.md)

[De nouveaux composants de SQL Server pour prendre en charge les Services de R](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md)

[Vue d'ensemble de la sécurité](../../advanced-analytics/r-services/security-overview-sql-server-r-services.md)
