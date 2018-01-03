---
title: "Nouveautés du système de plateforme Analytique – un entrepôt de données de la montée en puissance parallèle"
author: happynicolle
ms.author: nicw;barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "Voir quelles sont les nouveautés dans le système de plateforme Microsoft® Analytique, un dispositif de montée en puissance parallèle sur site qui héberge MPP SQL Server Parallel Data Warehouse."
ms.date: 11/28/2016
ms.topic: article
ms.openlocfilehash: eeeb41045527e72856edfb8bdb40becc462bde07
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="whats-new-in-analytics-platform-system-2016-a-scale-out-mpp-data-warehouse"></a>Nouveautés de l’Analytique plateforme System 2016, un entrepôt de données MPP montée en puissance parallèle
Voir quelles sont les nouveautés dans Microsoft® Analytique système de plateforme (APS) 2016, la dernière mise à jour du matériel pour un dispositif de montée en puissance parallèle sur site qui héberge MPP SQL Server Parallel Data Warehouse. 

## <a name="sql-server-2016"></a>SQL Server 2016

APS 2016 s’exécute sur la dernière version de SQL Server 2016 et utilise le niveau de compatibilité de base de données par défaut 130.  SQL Server 2016 permet de prendre en charge certaines des nouvelles fonctionnalités telles que les index secondaires pour l’index columnstore cluster et Kerberos pour PolyBase. 


## <a name="t-sql"></a>T-SQL
APS 2016 prend en charge ces améliorations de compatibilité de T-SQL.  Ces éléments de langage supplémentaires facilitent la migration à partir de SQL Server et d’autres sources de données. 

- [Les classements au niveau des colonnes SQL][] sont désormais pris en charge en plus des classements Windows.
- [Les index non cluster sur les index cluster columnstore][] améliorer les performances des requêtes qui recherchent des valeurs spécifiques dans l’index columnstore cluster. 
- [SÉLECTIONNEZ... DANS][] 
- [sp_spaceused()][] affiche l’espace disque utilisé ou réservé dans une table ou une base de données.
- [Les tableaux larges][] prise en charge est le même que SQL Server 2016. La limite précédente de 32 Ko pour la taille de ligne n’existe plus. 

### <a name="data-types"></a>Types de données

- [Varchar (max)][], [nvarchar (max)][] et [varbinary (max)][]. Ces types de données LOB ont une taille maximale de 2 Go. Pour charger ces objets utilisent [utilitaire bcp][]. Polybase et dwloader ne prennent pas actuellement en charge ces types de données. 
- [SYSNAME][]
- [UNIQUEIDENTIFIER][]
- [NUMÉRIQUE][] et types de données décimal.

### <a name="window-functions"></a>Fonctions de fenêtre

- [ROWS ou RANGE][] dans la clause OVER de l’instruction SELECT.
- [FIRST_VALUE][]
- [LAST_VALUE][]
- [CUME_DIST][]
- [PERCENT_RANK][]

### <a name="security-functions"></a>Fonctions de sécurité

- [CHECKSUM()][] et [BINARY_CHECKSUM()][]
- [HAS_PERMS_BY_NAME()][]

### <a name="additional-functions"></a>Fonctions supplémentaires

- [NEWID()][]
- [RAND()][]

## <a name="polybasehadoop-enhancements"></a>Améliorations de PolyBase/Hadoop

- Compatibilité avec Hortonworks HDP 2.4 et HDP 2.5
- Prise en charge Kerberos via les informations d’identification de la portée de la base de données
- Prise en charge des informations d’identification avec des objets BLOB de stockage Azure

## <a name="install-and-upgrade-enhancements"></a>Installer et des améliorations de la mise à niveau

### <a name="enterprise-architecture-updates"></a>Mises à jour Enterprise architecture
La mise à niveau de l’appliance existante vers APS 2016 installe le dernier microprogramme et les mises à jour du pilote, qui incluent les correctifs de sécurité. 

Un nouveau matériel à partir de HPE ou DELL inclut toutes les dernières mises à jour plus :

- Dernière génération la prise en charge (Broadwell)
- Mettre à jour vers DDR4 DIMM
- Débit DIMM améliorés

### <a name="integration"></a>Intégration

- Entièrement prise en charge du nom de domaine complet (FQDN) rend possible de configurer une approbation de domaine à l’appliance. 
- Pour utiliser le nom de domaine complet, vous devez effectuer une mise à niveau complète et de participer au cours de la mise à niveau. 

### <a name="reduced-downtime"></a>Temps mort réduit
L’installation ou la mise à niveau vers 2016 de points d’accès est plus rapide et nécessite moins de temps mort que les versions précédentes. Pour réduire les temps d’arrêt, l’installation ou la mise à niveau : 

 - Rationalise application des mises à jour WSUS à l’aide d’une image qui contient toutes les mises à jour juin 2016
 - Applique les mises à jour de sécurité avec les mises à jour de pilote et de microprogramme
 - Place les derniers correctifs logiciels et l’utilitaire de vérification de matériel (PAV) sur votre appareil afin qu’ils soient prêtes à être installées sans avoir à les télécharger.


<!--MSDN references-->
[database compatibility level 130]:https://msdn.microsoft.com/library/bb510680.aspx
[Les classements au niveau des colonnes SQL]:https://msdn.microsoft.com/library/ms143726.aspx
[Les index non cluster sur les index cluster columnstore]:https://msdn.microsoft.com/library/ms188783.aspx
[Varchar (max)]:https://msdn.microsoft.com/library/ms176089.aspx
[nvarchar (max)]:https://msdn.microsoft.com/library/ms186939.aspx
[varbinary (max)]:https://msdn.microsoft.com/library/ms188362.aspx
[SYSNAME]:https://msdn.microsoft.com/library/ms188021.aspx
[SÉLECTIONNEZ... DANS]:https://msdn.microsoft.com/library/ms188029.aspx
[sp_spaceused()]:https://msdn.microsoft.com/library/ms188776.aspx
[Les tableaux larges]:https://msdn.microsoft.com/library/ms143432.aspx
[BULK INSERT]:https://msdn.microsoft.com/library/ms188365.aspx
[utilitaire bcp]:https://msdn.microsoft.com/library/ms162802.aspx
[UNIQUEIDENTIFIER]:https://msdn.microsoft.com/library/ms187942.aspx
[NUMÉRIQUE]:https://msdn.microsoft.com/library/ms187746.aspx
[ROWS ou RANGE]:https://msdn.microsoft.com/library/ms189461.aspx
[FIRST_VALUE]:https://msdn.microsoft.com/library/hh213018.aspx
[LAST_VALUE]:https://msdn.microsoft.com/library/hh231517.aspx
[CUME_DIST]:https://msdn.microsoft.com//library/hh231078.aspx
[PERCENT_RANK]:https://msdn.microsoft.com/library/hh213573.aspx
[CHECKSUM()]:https://msdn.microsoft.com/library/ms189788.aspx
[BINARY_CHECKSUM()]:https://msdn.microsoft.com/library/ms173784.aspx
[HAS_PERMS_BY_NAME()]:https://msdn.microsoft.com/library/ms189802.aspx
[NEWID()]:https://msdn.microsoft.com/library/ms190348.aspx
[RAND()]:https://msdn.microsoft.com/library/ms177610.aspx


  

  


