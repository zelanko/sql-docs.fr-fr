---
title: "Effectuez-vous une mise &#224; niveau &#224; partir de SQL Server&#160;2005&#160;? | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad40e66f-71fe-4ee6-9ce3-17127e7b1d7a
caps.latest.revision: 21
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 21
---
# Effectuez-vous une mise &#224; niveau &#224; partir de SQL Server&#160;2005&#160;?
  La fin du support étendu pour SQL Server 2005 est une bonne raison d’effectuer une mise à niveau vers une version plus récente de SQL Server et vers Azure SQL Database. La mise à niveau vous permet de maintenir la sécurité et la conformité, d’atteindre des performances élevées et d’optimiser l’infrastructure de votre plateforme de données.  
  
 Pour plus d’informations, et pour obtenir les documents et les outils nécessaires pour planifier et automatiser la mise à niveau ou la migration, consultez [Fin du support de SQL Server 2005](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/).  
  
## Pourquoi effectuer une mise à niveau ?  
  
> [!IMPORTANT]  
>  Le support étendu pour SQL Server 2005 prendra fin le 12 avril 2016. Si vous utilisez encore SQL Server 2005 après le 12 avril 2016, vous ne recevrez plus de mises à jour de sécurité.  
  
 Pour obtenir une feuille de données au format PDF expliquant les avantages d’une mise à niveau de SQL Server 2005, [cliquez ici](https://info.microsoft.com/rs/157-GQE-382/images/EN-CNTNT-Infographic-UpgradeSQL2005Datasheet.pdf) (et non sur l’image miniature ci-dessous).  
  
 ![Data sheet about upgrading from SQL Server 2005](../../database-engine/install-windows/media/sqlserver2005eos.png "Data sheet about upgrading from SQL Server 2005")  
  
## Choisir votre option de mise à niveau  
 Si vous mettez à niveau des bases de données relationnelles à partir de SQL Server 2005, voici les options de stockage relationnel à votre disposition sur la plateforme Microsoft.  
  
 Pour une analyse plus complète de ces options, [cliquez ici](http://sql05upgrade.azurewebsites.net/).  
  
|Option de stockage relationnel|Avantages|Autres facteurs à prendre en compte|  
|-------------------------------|--------------|-------------------------------|  
|**SQL Server local**<br /><br /> Envisagez cette option pour tous les types d’applications de base de données, des systèmes transactionnels aux entrepôts de données.|Dans la mesure où vous gérez le matériel et les logiciels, vous bénéficiez d’un contrôle optimal sur les fonctionnalités et l’évolutivité.<br /><br /> Si vous procédez à la mise à niveau à partir de SQL Server 2005, il s’agit de l’environnement le plus similaire.|L’investissement initial et les efforts de gestion continue sont les plus importants, car vous devez acheter, maintenir et gérer votre matériel et vos logiciels.<br /><br /> Pour plus d’informations, consultez la page [SQL Server 2016](https://www.microsoft.com/EN-US/server-cloud/products/sql-server-2016/).|  
|**SQL Server hébergé sur Azure Virtual Machines**<br /><br /> Envisagez cette option si vous souhaitez :<br /><br /> profiter des avantages de la migration dans un environnement hébergé ;<br /><br /> contrôler l’environnement d’exploitation ;<br /><br /> bénéficier de toutes les fonctionnalités de SQL Server qui vous sont familières.|Vous pouvez effectuer rapidement le déploiement à partir d’une bibliothèque d’images de machine virtuelle.<br /><br /> Vous obtenez l’ensemble complet des fonctionnalités de SQL Server.<br /><br /> Vous économisez les coûts liés au matériel et au logiciel serveur. Votre consommation est facturée à l’heure.|Vous devez configurer et gérer SQL Server et le système d’exploitation.<br /><br /> <br /><br /> Pour plus d’informations, consultez [Vue d’ensemble de SQL Server sur les machines virtuelles Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/).<br /><br /> Pour plus d’informations sur la migration, consultez [Migration d’une base de données vers SQL Server sur une machine virtuelle Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-migrate-onpremises-database/).|  
|**Service de base de données hébergé par Azure SQL Database**<br /><br /> Envisagez cette option si vous souhaitez une solution économique nécessitant moins d’efforts de maintenance.<br /><br /> Cette option convient particulièrement aux applications qui ne nécessitent pas une capacité constante ou qui doivent fournir un accès externe.|Déploiement rapide et mise à l’échelle simplifiée.<br /><br /> Votre consommation est facturée à l’heure.<br /><br /> Le coût du service inclut non seulement le stockage, mais aussi des sauvegardes automatisées à haute disponibilité.|Azure SQL Database ne propose pas certaines fonctionnalités de SQL Server qui ne sont pas applicables à un environnement hébergé dans le cloud. Pour plus d’informations, consultez [Informations sur le langage Transact-SQL d’Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-transact-sql-information/).<br /><br /> Azure SQL Database limite également la taille des bases de données à 500 Go, contre 524 Po pour SQL Server.<br /><br /> Pour plus d’informations, consultez la page [Base de données SQL](https://azure.microsoft.com/services/sql-database/).<br /><br /> Pour plus d’informations sur la migration, consultez [Migration d’une base de données SQL Server vers une base de données SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-cloud-migrate/).|  
  
 Vous pouvez également envisager d’utiliser une solution non relationnelle ou NoSQL pour certaines applications et données.  
  
|Solution non relationnelle|Avantages|  
|------------------------------|--------------|  
|**Azure DocumentDB**<br /><br /> Envisagez cette option pour vos applications web récentes, évolutives et mobiles qui utilisent des données JSON et qui nécessitent à la fois des capacités robustes d’exécution de requêtes et de traitement des données transactionnelles.<br /><br /> Pour plus d’informations, consultez [DocumentDB](https://azure.microsoft.com/en-us/services/documentdb/).<br /><br /> Pour plus d’informations sur l’importation de données, consultez [Importation de données vers DocumentDB avec l’outil de migration de base de données](https://azure.microsoft.com/documentation/articles/documentdb-import-data/).|Vos documents sont indexés, et vous pouvez exécuter des requêtes sur ceux-ci en utilisant la syntaxe SQL que vous connaissez.<br /><br /> La base de données ne contient pas de schéma.<br /><br /> Vous pouvez ajouter des propriétés à des documents sans avoir à reconstruire les index.<br /><br /> Le moteur de base de données prend directement en charge JSON et JavaScript.<br /><br /> Vous bénéficiez de la prise en charge native des données géospatiales et de l’intégration à d’autres services Azure, comme Azure Search, HDInsight et Data Factory.<br /><br /> Vous obtenez un stockage offrant des performances élevées et une latence faible avec des niveaux de débit réservés.|  
|**Stockage de tables Azure**<br /><br /> Envisagez cette option pour stocker plusieurs pétaoctets de données semi-structurées dans une solution rentable.<br /><br /> Pour plus d’informations, consultez [Stockage de table](https://azure.microsoft.com/services/storage/tables/).|Vous pouvez faire évoluer vos applications et votre schéma de table sans mettre les données hors connexion.<br /><br /> Vous pouvez procéder à une montée en puissance sans partitionner votre jeu de données.<br /><br /> Vous obtenez un stockage géo-redondant qui réplique les données dans plusieurs régions.|  
  
 Pour télécharger le rapport « Migration à partir de SQL Server 2005 » (par Directions on Microsoft), [cliquez ici](https://info.microsoft.com/CO-SQL-CNTNT-FY16-09Sep-14-ModernizationDirOnMFST-Register.html) (pas sur l’image miniature ci-dessous).  
  
 ![Report about migrating from SQL Server 2005](../../database-engine/install-windows/media/sqlserver2005migratingdoc.png "Report about migrating from SQL Server 2005")  
  
## Planifier votre mise à niveau  
  
-   Découvrez comment planifier votre mise à niveau en lisant les séries de billets de blog suivantes de l’équipe SQL Server.  
  
    -   [Planification d’une mise à niveau efficace de SQL Server 2005 : étape 1 sur 3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/10/planning-an-efficient-upgrade-from-sql-server-2005-step-1-of-3.aspx)  
  
    -   [Planification d’une mise à niveau efficace de SQL Server 2005 : étape 2 sur 3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/15/planning-an-efficient-upgrade-from-sql-server-2005-step-2-of-3.aspx)  
  
    -   [Planification d’une mise à niveau efficace de SQL Server 2005 : étape 3 sur 3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/17/planning-an-efficient-upgrade-from-sql-server-2005-step-3-of-3.aspx)  
  
-   Passez en revue les exigences et éléments à prendre en compte spécifiés dans la page [Planning a SQL Server Installation](../../sql-server/install/planning-a-sql-server-installation.md), y compris les [Hardware and Software Requirements for Installing SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md).  
  
-   Découvrez comment effectuer la mise à niveau.  
  
    -   Passez en revue les méthodes de mise à niveau disponibles et découvrez comment planifier et tester dans la rubrique [Upgrade Database Engine](../../database-engine/install-windows/upgrade-database-engine.md).  
  
        > [!IMPORTANT]  
        >  Vous ne pouvez pas effectuer une mise à niveau sur place d’un serveur SQL Server 2005 vers un serveur SQL Server 2016. Vous devez installer SQL Server 2016, puis migrer vos bases de données SQL Server 2005 vers la nouvelle installation. Pour plus d’informations, consultez la section « New Installation Upgrade » (Mise à niveau d’une nouvelle installation) de la rubrique [Choose a Database Engine Upgrade Method](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md).  
  
    -   Pour obtenir une version plus détaillée du « guide technique sur la mise à niveau » au format PDF, [cliquez ici](http://download.microsoft.com/download/7/1/5/715BDFA7-51B6-4D7B-AF17-61E78C7E538F/SQL_Server_2014_Upgrade_technical_guide.pdf).  
  
        > [!NOTE]  
        >  Il s’agit actuellement de la version SQL Server 2014 du « Guide de mise à niveau technique ». La version SQL Server 2016 de ce guide n’est pas encore disponible.  
  
-   Pour plus d’informations, et pour obtenir les documents et les outils nécessaires pour planifier et automatiser la mise à niveau ou la migration, consultez [Fin du support de SQL Server 2005](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/).  
  
## Obtenir SQL Server 2016  
 Pour télécharger une copie d’évaluation de SQL Server 2016, [cliquez ici](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016/?wt.mc_id=upgrade2005).  
  
## Voir aussi  
 [SQL Server 2016](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2016/default.aspx)   
 [Fin du support de SQL Server 2005](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/)   
 [Mise à niveau de SQL Server 2005 vers SQL Server 2014](https://msdn.microsoft.com/en-us/library/mt170591\(v=sql.120\).aspx)  
  
  