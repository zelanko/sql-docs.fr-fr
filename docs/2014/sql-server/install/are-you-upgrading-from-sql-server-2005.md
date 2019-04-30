---
title: Effectuez-vous une mise à niveau à partir de SQL Server 2005 ? | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 3d50a66a-1845-4116-8b3a-7b5a2eeb78e6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e3f76346bf77e782eb47999a7acc36369fbec104
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63214915"
---
# <a name="are-you-upgrading-from-sql-server-2005"></a>Effectuez-vous une mise à niveau à partir de SQL Server 2005 ?
  La fin du support étendu pour SQL Server 2005 est une bonne raison d’effectuer une mise à niveau vers une version plus récente de SQL Server et vers Azure SQL Database. La mise à niveau vous permet de maintenir la sécurité et la conformité, d’atteindre des performances élevées et d’optimiser l’infrastructure de votre plateforme de données.  
  
 Pour plus d’informations, et pour obtenir les documents et les outils nécessaires pour planifier et automatiser la mise à niveau ou la migration, consultez [Fin du support de SQL Server 2005](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/).  
  
## <a name="why-upgrade"></a>Pourquoi effectuer une mise à niveau ?  
  
> [!IMPORTANT]  
>  Le support étendu pour SQL Server 2005 prendra fin le 12 avril 2016. Si vous utilisez encore SQL Server 2005 après le 12 avril 2016, vous ne recevrez plus de mises à jour de sécurité.  
  
 Pour obtenir la feuille de données au format PDF sur la mise à niveau à partir de SQL Server 2005, [cliquez ici](https://info.microsoft.com/rs/157-GQE-382/images/EN-CNTNT-Infographic-UpgradeSQL2005Datasheet.pdf) (et non sur l’image miniature ci-dessous).  
  
 ![Feuille de données sur la mise à niveau à partir de SQL Server 2005](../../../2014/sql-server/install/media/sqlserver2005eos.png "feuille de données sur la mise à niveau à partir de SQL Server 2005")  
  
## <a name="choose-your-upgrade-option"></a>Choisir votre option de mise à niveau  
 Si vous mettez à niveau des bases de données relationnelles à partir de SQL Server 2005, voici les options pour le stockage relationnel sur la plate-forme Microsoft.  
  
 Pour une analyse plus complète de ces options, [cliquez ici](http://sql05upgrade.azurewebsites.net/).  
  
|Option de stockage relationnel|Avantages|Autres facteurs à prendre en compte|  
|-------------------------------|--------------|-------------------------------|  
|**SQL Server local**<br /><br /> Envisagez cette option pour tous les types d’applications de base de données, des systèmes transactionnels aux entrepôts de données.<br /><br /> Pour plus d’informations, consultez [SQL Server 2014](https://www.microsoft.com/EN-US/server-cloud/products/sql-server/).|Dans la mesure où vous gérez le matériel et les logiciels, vous bénéficiez d’un contrôle optimal sur les fonctionnalités et l’évolutivité.<br /><br /> Si vous mettez à niveau à partir de SQL Server 2005, il s’agit de l’environnement plus similaire.|L’investissement initial et les efforts de gestion continue sont les plus importants, car vous devez acheter, maintenir et gérer votre matériel et vos logiciels.|  
|**SQL Server hébergé sur Azure Virtual Machines**<br /><br /> Envisagez cette option si vous souhaitez que les opérations suivantes.<br />-Avantages de la migration vers un environnement hébergé.<br />-Contrôler l’environnement d’exploitation.<br />-Ensemble de fonctionnalités familier de SQL Server.<br /><br /> Pour plus d’informations, consultez [SQL Server sur une vue d’ensemble de Machines virtuelles](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/).<br /><br /> Pour plus d’informations sur la migration, consultez [Migration d’une base de données vers SQL Server sur une machine virtuelle Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-migrate-onpremises-database/).|Vous pouvez effectuer rapidement le déploiement à partir d’une bibliothèque d’images de machine virtuelle.<br /><br /> Vous obtenez l’ensemble complet des fonctionnalités de SQL Server.<br /><br /> Vous économisez les coûts liés au matériel et au logiciel serveur. Votre consommation est facturée à l’heure.|Vous devez configurer et gérer SQL Server et le système d’exploitation.|  
|**Service de base de données hébergé par Azure SQL Database**<br /><br /> Envisagez cette option si vous souhaitez une solution économique nécessitant moins d’efforts de maintenance.<br /><br /> Cette option convient particulièrement aux applications qui ne nécessitent pas une capacité constante ou qui doivent fournir un accès externe.<br /><br /> Pour plus d’informations, consultez [base de données SQL](https://azure.microsoft.com/services/sql-database/).<br /><br /> Pour plus d’informations sur la migration, consultez [migration d’une base de données SQL Server vers Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-cloud-migrate/).|Déploiement rapide et mise à l’échelle simplifiée.<br /><br /> Votre consommation est facturée à l’heure.<br /><br /> Le coût du service inclut non seulement le stockage, mais aussi des sauvegardes automatisées à haute disponibilité.|Azure SQL Database ne propose pas certaines fonctionnalités de SQL Server qui ne sont pas applicables à un environnement hébergé dans le cloud. Pour plus d’informations, consultez [Informations sur le langage Transact-SQL d’Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-transact-sql-information/).<br /><br /> Azure SQL Database limite également la taille des bases de données à 500 Go, contre 524 Po pour SQL Server.|  
  
 Vous pouvez également envisager d’utiliser une solution non relationnelle ou NoSQL pour certaines applications et données.  
  
|Solution non relationnelle|Avantages|  
|------------------------------|--------------|  
|**Azure DocumentDB**<br /><br /> Envisagez cette option pour vos applications web récentes, évolutives et mobiles qui utilisent des données JSON et qui nécessitent à la fois des capacités robustes d’exécution de requêtes et de traitement des données transactionnelles.<br /><br /> Pour plus d’informations, consultez [DocumentDB](https://azure.microsoft.com/en-us/services/documentdb/).|Vos documents sont indexés, et vous pouvez exécuter des requêtes sur ceux-ci en utilisant la syntaxe SQL que vous connaissez.<br /><br /> La base de données ne contient pas de schéma.<br /><br /> Vous pouvez ajouter des propriétés à des documents sans avoir à reconstruire les index.<br /><br /> Le moteur de base de données prend directement en charge JSON et JavaScript.<br /><br /> Vous bénéficiez de la prise en charge native des données géospatiales et de l’intégration à d’autres services Azure, comme Azure Search, HDInsight et Data Factory.<br /><br /> Vous obtenez un stockage offrant des performances élevées et une latence faible avec des niveaux de débit réservés.|  
|**Stockage de tables Azure**<br /><br /> Envisagez cette option pour stocker plusieurs pétaoctets de données semi-structurées dans une solution rentable.<br /><br /> Pour plus d’informations, consultez [Stockage de table](https://azure.microsoft.com/services/storage/tables/).|Vous pouvez faire évoluer vos applications et votre schéma de table sans mettre les données hors connexion.<br /><br /> Vous pouvez procéder à une montée en puissance sans partitionner votre jeu de données.<br /><br /> Vous obtenez un stockage géo-redondant qui réplique les données dans plusieurs régions.|  
  
 Pour télécharger le rapport « Migration à partir de SQL Server 2005 » (par Directions on Microsoft), [cliquez ici](https://info.microsoft.com/CO-SQL-CNTNT-FY16-09Sep-14-ModernizationDirOnMFST-Register.html) (pas sur l’image miniature ci-dessous).  
  
 ![Rapport sur la migration à partir de SQL Server 2005](../../../2014/sql-server/install/media/sqlserver2005migratingdoc.png "rapport sur la migration à partir de SQL Server 2005")  
  
## <a name="plan-your-upgrade"></a>Planifier votre mise à niveau  
  
-   Découvrez comment planifier votre mise à niveau en lisant les séries de billets de blog suivantes de l’équipe SQL Server.  
  
    -   [Planification d’une mise à niveau efficace de SQL Server 2005 : Étape 1 sur 3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/10/planning-an-efficient-upgrade-from-sql-server-2005-step-1-of-3.aspx)  
  
    -   [Planification d’une mise à niveau efficace de SQL Server 2005 : Étape 2 sur 3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/15/planning-an-efficient-upgrade-from-sql-server-2005-step-2-of-3.aspx)  
  
    -   [Planification d’une mise à niveau efficace de SQL Server 2005 : Étape 3 sur 3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/17/planning-an-efficient-upgrade-from-sql-server-2005-step-3-of-3.aspx)  
  
-   Passez en revue les exigences et considérations sous [planification d’une Installation SQL Server](../../../2014/sql-server/install/planning-a-sql-server-installation.md), y compris le [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Découvrez comment effectuer la mise à niveau.  
  
    -   Passez en revue les méthodes de mise à niveau disponibles et découvrez comment planifier et tester dans la rubrique [Upgrade Database Engine](../../database-engine/install-windows/upgrade-database-engine.md).  
  
        > [!IMPORTANT]  
        >  Vous ne pouvez pas effectuer une mise à niveau sur place d’un serveur SQL Server 2005 vers un serveur SQL Server 2014. Vous devez installer SQL Server 2014, puis migrer vos bases de données SQL Server 2005 vers la nouvelle installation.  
  
    -   Pour obtenir une version plus détaillée du « guide technique sur la mise à niveau » au format PDF, [cliquez ici](https://download.microsoft.com/download/7/1/5/715BDFA7-51B6-4D7B-AF17-61E78C7E538F/SQL_Server_2014_Upgrade_technical_guide.pdf).  
  
-   Pour plus d’informations, et pour obtenir les documents et les outils nécessaires pour planifier et automatiser la mise à niveau ou la migration, consultez [Fin du support de SQL Server 2005](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/).  
  
## <a name="get-sql-server-2014"></a>Obtenir SQL Server 2014  
 Pour télécharger une copie d’évaluation de SQL Server 2014, [cliquez ici](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2014).  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server 2014](https://www.microsoft.com/en-us/server-cloud/products/sql-server/default.aspx)   
 [Fin du support de SQL Server 2005](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/)   
 [Mise à niveau à partir de SQL Server 2005 vers SQL Server 2016](https://msdn.microsoft.com/library/mt168847.aspx)  
  
  
