---
title: "R&#233;glage des performances des Services de SQL Server R | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf6f3b7d-f9f9-4e45-b0d1-07850b53e0c5
caps.latest.revision: 20
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 19
---
# R&#233;glage des performances des Services de SQL Server R
[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] fournit une plateforme pour le développement d’applications intelligentes ouvrent de nouvelles perspectives. Un spécialiste des données peut utiliser la puissance du langage R pour former et créer des modèles à l’aide des données stockées dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Une fois que le modèle est prêt pour la production, un spécialiste des données peut travailler avec les administrateurs de base de données et ingénieurs SQL pour déployer sa solution en production. Les informations contenues dans cette section fournissent des conseils de niveau élevé sur le réglage des performances à la fois lors de la création et l’apprentissage des modèles et lors du déploiement de modèles à la production.

Les informations contenues dans ce document part du principe que vous êtes familiarisé avec [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] concepts et la terminologie. Pour obtenir des informations générales sur les Services de R, consultez [SQL Server Services R](../../advanced-analytics/r-services/sql-server-r-services.md).

> [!NOTE]
> Alors que la plupart des informations de cette section est des instructions générales sur la configuration de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], certaines informations sont spécifiques aux fonctions analytiques RevoScaleR.

## Dans cette section

* [Configuration de SQL Server](../../advanced-analytics/r-services/sql-server-configuration-r-services.md): ce document fournit des conseils pour la configuration du matériel qui [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] est installé sur. Il est plus utile de __les administrateurs de base de données__.

* [R et l’optimisation de données](../../advanced-analytics/r-services/r-and-data-optimization-r-services.md): ce document fournit des conseils sur l’utilisation de scripts R avec les Services de R. Il est plus utile de __scientifiques__.

* [Étude de cas de performances](../../advanced-analytics/r-services/performance-case-study-r-services.md): ce document fournit des données de test et les scripts R qui peuvent être utilisés pour tester l’impact des instructions fournies dans les documents précédents.

## Références

Vous trouverez ci-dessous des liens vers des informations utilisées dans le développement de ce document.

* [Comment déterminer la taille de page appropriée pour les versions 64 bits de Windows](https://support.microsoft.com/kb/2860880)

* [Compression de données](../../relational-databases/data-compression/data-compression.md)

* [Activer la compression sur une table ou un index](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

* [Désactiver la compression sur une table ou un index](../../relational-databases/data-compression/disable-compression-on-a-table-or-index.md)

* [Outil de test de performances/générateur DISKSPD stockage charge](https://github.com/microsoft/diskspd)

* [Référence d’utilitaire FSUtil](https://technet.microsoft.com/library/cc753059.aspx)

* [Réorganiser et reconstruire des index](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)

* [R Services](../../advanced-analytics/r-services/r-services.md)

* [Options de réglage de performances pour rxDForest et rxDTree](https://support.microsoft.com/kb/3104235)

* [Surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)

* [Guide de l’utilisateur RevoScaleR](https://packages.revolutionanalytics.com/doc/7.0.0/win/RevoScaleR_Users_Guide.pdf)

* [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)

## Voir aussi

 
 [Configuration de SQL Server pour les Services de R](../../advanced-analytics/r-services/sql-server-configuration-r-services.md)
 
 [Étude de cas de performances](../../advanced-analytics/r-services/performance-case-study-r-services.md)
 
 [R et optimisation des données](../../advanced-analytics/r-services/r-and-data-optimization-r-services.md)