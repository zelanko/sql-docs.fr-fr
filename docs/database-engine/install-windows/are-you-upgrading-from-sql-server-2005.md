---
title: Effectuez-vous une mise à niveau à partir de SQL Server 2005, 2008 ou 2008R2 ? | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ad40e66f-71fe-4ee6-9ce3-17127e7b1d7a
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 27e7285fe95307c6ce6308dc27e0076146e86223
ms.sourcegitcommit: 706f3a89fdb98e84569973f35a3032f324a92771
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58657763"
---
# <a name="are-you-upgrading-from-sql-server-2005-2008-or-2008r2"></a>Effectuez-vous une mise à niveau à partir de SQL Server 2005, 2008 ou 2008R2 ?

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
 La fin du support étendu de SQL Server est une bonne raison d’effectuer une mise à niveau vers une version plus récente de SQL Server et vers Azure SQL Database. La mise à niveau vous permet de maintenir la sécurité et la conformité, d’atteindre des performances élevées et d’optimiser l’infrastructure de votre plateforme de données.  
  
 Pour plus d’informations et pour obtenir les documents et les outils nécessaires afin de planifier et d’automatiser la mise à niveau ou la migration, consultez [Fin du support de SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005) et [Fin du support de SQL Server 2008](https://www.microsoft.com/cloud-platform/windows-sql-server-2008).  
  
## <a name="why-upgrade"></a>Pourquoi effectuer une mise à niveau ?  
  
> [!IMPORTANT]  
>  Le support étendu pour SQL Server 2005 a pris fin le 12 avril 2016. Si vous utilisez encore SQL Server 2005 après le 12 avril 2016, vous ne recevez plus de mises à jour de sécurité.  

> [!IMPORTANT]  
>  Le support étendu de SQL Server 2008 et 2008R2 prend fin le 9 juillet 2019. Si vous utilisez encore SQL Server 2008 ou 2008R2 après le 9 juillet 2019, vous ne recevrez plus de mises à jour de sécurité. Vous trouverez plus d’informations sur le blog [Announcing new options for SQL Server 2008](https://azure.microsoft.com/blog/announcing-new-options-for-sql-server-2008-and-windows-server-2008-end-of-support/).  
  
## <a name="choose-your-upgrade-option"></a>Choisir votre option de mise à niveau  
Si vous mettez à niveau des bases de données relationnelles à partir d’une version antérieure de SQL Server, voici les options de stockage relationnel à votre disposition sur la plateforme Microsoft.  
  
Pour une analyse plus complète de ces options, [cliquez ici](https://sql05upgrade.azurewebsites.net/).  
  
|Option de stockage relationnel|Avantages|Autres facteurs à prendre en compte|  
|-------------------------------|--------------|-------------------------------|  
|**SQL Server local**<br /><br /> Envisagez cette option pour tous les types d’applications de base de données, des systèmes transactionnels aux entrepôts de données.|Dans la mesure où vous gérez le matériel et les logiciels, vous bénéficiez d’un contrôle optimal sur les fonctionnalités et l’évolutivité.<br /><br /> Si vous procédez à la mise à niveau à partir d’une version antérieure de SQL Server, il s’agit de l’environnement le plus similaire.|L’investissement initial et les efforts de gestion continue sont les plus importants, car vous devez acheter, maintenir et gérer votre matériel et vos logiciels.<br /><br /> Pour plus d’informations, consultez la page [SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2017-rtm).|  
|**SQL Server hébergé sur Azure Virtual Machines**<br /><br /> Envisagez cette option si vous souhaitez :<br /><br /> profiter des avantages de la migration dans un environnement hébergé ;<br /><br /> contrôler l’environnement d’exploitation ;<br /><br /> bénéficier de toutes les fonctionnalités de SQL Server qui vous sont familières.|Vous pouvez effectuer rapidement le déploiement à partir d’une bibliothèque d’images de machine virtuelle.<br /><br /> Vous obtenez l’ensemble complet des fonctionnalités de SQL Server.<br /><br /> Vous économisez les coûts liés au matériel et au logiciel serveur. Votre consommation est facturée à l’heure.|Vous devez configurer et gérer SQL Server et le système d’exploitation.<br /><br /> <br /><br /> Pour plus d’informations, consultez [Vue d’ensemble de SQL Server sur les machines virtuelles Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/).<br /><br /> Pour plus d’informations sur la migration, consultez [Migration d’une base de données vers SQL Server sur une machine virtuelle Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-migrate-onpremises-database/).|  
|**Service de base de données hébergé par Azure SQL Database**<br /><br /> Envisagez cette option si vous souhaitez une solution économique nécessitant moins d’efforts de maintenance.<br /><br /> Cette option convient particulièrement aux applications qui ne nécessitent pas une capacité constante ou qui doivent fournir un accès externe.|Déploiement rapide et mise à l’échelle simplifiée.<br /><br /> Votre consommation est facturée à l’heure.<br /><br /> Le coût du service inclut non seulement le stockage, mais aussi des sauvegardes automatisées à haute disponibilité.|Azure SQL Database ne propose pas certaines fonctionnalités de SQL Server qui ne sont pas applicables à un environnement hébergé dans le cloud. Pour plus d’informations, consultez [Informations sur le langage Transact-SQL d’Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-transact-sql-information/).<br /><br /> Azure SQL Database limite également la taille des bases de données à 4 To, contre 524 Po pour SQL Server. Pour plus d’informations, consultez [Limites de ressources pour une base de données unique](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-single-databases)<br /><br /> Pour plus d’informations sur SQL Database, consultez [Vue d’ensemble d’Azure SQL Database](https://azure.microsoft.com/services/sql-database/) et [Documentation Azure SQL Database](https://docs.microsoft.com/azure/sql-database/).<br /><br /> Pour plus d’informations sur la migration, consultez [Migration d’une base de données SQL Server vers une base de données SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-cloud-migrate/).|  
  
 Vous pouvez également envisager d’utiliser une solution non relationnelle ou NoSQL pour certaines applications et données.  
  
|Solution non relationnelle|Avantages|  
|------------------------------|--------------|  
|**Azure Cosmos DB**<br /><br /> Envisagez cette option pour vos applications web récentes, scalables et mobiles qui utilisent des données JSON et qui nécessitent à la fois des capacités robustes d’exécution de requêtes et de traitement des données transactionnelles.<br /><br /> Pour plus d’informations, consultez [Cosmos DB](https://azure.microsoft.com/services/cosmos-db/).<br /><br /> Pour plus d’informations sur l’importation de données, consultez [Importer des données dans Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/import-data/).|Vos documents sont indexés, et vous pouvez exécuter des requêtes sur ceux-ci en utilisant la syntaxe SQL que vous connaissez.<br /><br /> La base de données ne contient pas de schéma.<br /><br /> Vous pouvez ajouter des propriétés à des documents sans avoir à reconstruire les index.<br /><br /> Le moteur de base de données prend directement en charge JSON et JavaScript.<br /><br /> Vous bénéficiez de la prise en charge native des données géospatiales et de l’intégration à d’autres services Azure, comme Azure Search, HDInsight et Data Factory.<br /><br /> Vous obtenez un stockage offrant des performances élevées et une latence faible avec des niveaux de débit réservés.|  
|**Stockage de tables Azure**<br /><br /> Envisagez cette option pour stocker plusieurs pétaoctets de données semi-structurées dans une solution rentable.<br /><br /> Pour plus d’informations, consultez [Stockage de table](https://azure.microsoft.com/services/storage/tables/).|Vous pouvez faire évoluer vos applications et votre schéma de table sans mettre les données hors connexion.<br /><br /> Vous pouvez procéder à une montée en puissance sans partitionner votre jeu de données.<br /><br /> Vous obtenez un stockage géo-redondant qui réplique les données dans plusieurs régions.|  
  
## <a name="plan-your-upgrade"></a>Planifier votre mise à niveau  
  
-   Découvrez comment planifier la mise à niveau de votre instance de SDL Server 2005 en lisant les séries de billets de blog suivantes de l’équipe SQL Server. 
    - Planification d’une mise à niveau efficace de SQL Server 2005 : [étape 1 sur 3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/10/planning-an-efficient-upgrade-from-sql-server-2005-step-1-of-3.aspx), [étape 2 sur 3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/15/planning-an-efficient-upgrade-from-sql-server-2005-step-2-of-3.aspx), [étape 3 sur 3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/17/planning-an-efficient-upgrade-from-sql-server-2005-step-3-of-3.aspx)
- Préparez-vous à la [Fin du support de SQL Server 2008](https://www.microsoft.com/sql-server/sql-server-2008).
  
-   Passez en revue les exigences et éléments à prendre en compte spécifiés dans la page [Planification d’une installation SQL Server](../../sql-server/install/planning-a-sql-server-installation.md), y compris les [Configurations matérielle et logicielle requises pour l’installation de SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Découvrez comment effectuer la mise à niveau.  
  
    -   Passez en revue les méthodes de mise à niveau disponibles et découvrez comment planifier et tester dans l’article [Mettre à niveau le moteur de base de données](../../database-engine/install-windows/upgrade-database-engine.md).  
  
        > [!IMPORTANT]  
        >- Vous ne pouvez pas effectuer une mise à niveau sur place d’une instance de SQL Server 2005 vers un serveur SQL Server 2017. Vous devez installer une instance de SQL Server 2017, puis migrer vos bases de données SQL Server 2005 vers la nouvelle installation. Pour plus d’informations, consultez la section « Mise à niveau d’une nouvelle installation » de l’article [Choisir une méthode de mise à niveau du moteur de base de données](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md).  
        >- Il est possible d’effectuer une mise à niveau sur place de SQL 2008 et SQL 2008R2 vers SQL 2017. Pour plus d’informations, consultez [Mises à niveau de la version et de l’édition prises en charge](supported-version-and-edition-upgrades-2017.md). 


-    Pour plus d’informations et pour obtenir les documents et les outils nécessaires afin de planifier et d’automatiser la mise à niveau ou la migration, consultez [Fin du support de SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005) et [Fin du support de SQL Server 2008](https://www.microsoft.com/cloud-platform/windows-sql-server-2008).  
  
## <a name="get-sql-server"></a>Obtenir SQL Server  
 Pour télécharger une copie d’évaluation de SQL Server, consultez [Téléchargements SQL Server](https://www.microsoft.com/sql-server/sql-server-downloads).  
  
## <a name="next-steps"></a>Next Steps  
 [SQL Server 2017](https://www.microsoft.com/sql-server/sql-server-2017)   
 [Fin du support de SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005)   
 [Fin du support de SQL Server 2008](https://www.microsoft.com/cloud-platform/windows-sql-server-2008)
  
  
