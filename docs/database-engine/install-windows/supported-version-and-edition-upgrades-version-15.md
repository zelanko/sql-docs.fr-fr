---
title: Mises à niveau de version et d’édition prises en charge (SQL Server 2019)
description: Décrit les mises à niveau de version et d’édition prises en charge pour SQL Server 2019.
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- components [SQL Server], adding to existing installations
- versions [SQL Server], upgrading
- upgrading SQL Server, upgrades supported
- cross-language support
ms.assetid: 702359c4-6ca9-42a8-860c-a95a802898a1
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions'
ms.openlocfilehash: 687f314e776dcc049f03cb4c8a164fb5fa84073e
ms.sourcegitcommit: 2f868a77903c1f1c4cecf4ea1c181deee12d5b15
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91670198"
---
# <a name="supported-version--edition-upgrades-sql-server-2019"></a>Mises à niveau de version et d’édition prises en charge (SQL Server 2019)

[!INCLUDE [SQL Server -Windows Only](../../includes/applies-to-version/sql-windows-only.md)]
  
  Vous pouvez effectuer une mise à niveau à partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], [!INCLUDE[sssql16-md](../../includes/sssql16-md.md)]et [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)]. Cet article répertorie les chemins de mise à niveau pris en charge à partir de ces versions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et les mises à niveau d’édition prises en charge pour [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)].  
  
## <a name="pre-upgrade-checklist"></a>Liste de contrôle préalable à la mise à niveau  

- Avant de mettre à niveau une édition de [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] vers une autre édition, vérifiez si les fonctionnalités que vous utilisez actuellement sont prises en charge dans l'édition vers laquelle vous vous déplacez.  
- Vérifiez [le matériel et les logiciels](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-ver15.md) pris en charge.
- Avant de mettre à niveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], activez l'authentification Windows pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent et vérifiez la configuration par défaut : le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être membre du groupe sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
- Pour procéder à une mise à niveau vers [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)], vous devez exécuter un système d'exploitation pris en charge. Pour plus d’informations, consultez [Configurations matérielle et logicielle requises pour l’installation de SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-ver15.md).  
- La mise à niveau sera bloquée s'il existe un redémarrage en attente.  
- La mise à niveau sera bloquée si le service Windows Installer ne s'exécute pas.

## <a name="unsupported-scenarios"></a>Scénarios non pris en charge

- Les instances inter-versions de [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] ne sont pas prises en charge. Les numéros de version des composants [!INCLUDE[ssDE](../../includes/ssde-md.md)] doivent être identiques dans une instance de [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)].  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] est disponible seulement pour les plateformes 64 bits. La mise à niveau interplateforme n'est pas prise en charge. Vous ne pouvez pas mettre à niveau une instance 32 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers une instance native 64 bits à l'aide du programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez toutefois sauvegarder ou détacher des bases de données d'une instance 32 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis les restaurer ou les attacher sur une nouvelle instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (64 bits) si les bases de données ne sont pas publiées dans la réplication. Vous devez recréer toute connexion et tout autre objet utilisateur dans les bases de données système master, msdb et model.  
  
- Vous ne pouvez pas ajouter de nouvelles fonctionnalités pendant la mise à niveau de votre instance existante de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Après avoir mis à niveau une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)], vous pouvez ajouter des fonctionnalités via le programme d'installation de [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)]. Pour plus d’informations, consultez [Ajouter des fonctionnalités à une instance de SQL Server &#40;Installation&#41;](./add-features-to-an-instance-of-sql-server-setup.md).  
 
## <a name="upgrades-from-earlier-versions-to-sssqlv15-md"></a>Mises à niveau des versions antérieures vers [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)]  
 
[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] prend en charge la mise à niveau à partir des versions suivantes de SQL Server :

- [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 ou ultérieur
- [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP3 ou ultérieur
- [!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] SP2 ou ultérieur
- [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]

Le tableau ci-dessous répertorie les scénarios de mise à niveau pris en charge depuis des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)].  
  
|Mise à niveau à partir de|Chemin d'accès de mise à niveau pris en charge|  
|:------|:------|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 Enterprise|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 Developer|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/>[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 Standard|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 Web|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 Express |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express <br/> <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 Business Intelligence|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4 version d’évaluation|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] version d’évaluation <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 Enterprise|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 Developer|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 Standard|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 Web|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 Express |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 Business Intelligence|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 Evaluation|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] version d’évaluation <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer|
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Enterprise|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Developer|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Standard|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Web|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Express |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer|  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Business Intelligence|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 version d’évaluation|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] version d’évaluation <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer|
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Enterprise|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Developer|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Standard|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Web|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Express |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer|  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Business Intelligence|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] version d’évaluation|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] version d’évaluation <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer|
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] version Release Candidate (RC)* |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise |  
|[!INCLUDE[sssqlv15_md](../../includes/sssqlv15-md.md)] Developer |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise | 

 \* La prise en charge Microsoft de la mise à niveau à partir de la version Release Candidate (RC) s’adresse spécifiquement aux clients qui ont participé au programme Utilisateur précoce.

## <a name="migrate-to-sql-server-2019"></a>Migrer vers SQL Server 2019

Vous pouvez migrer des bases de données à partir de versions antérieures. Par exemple, vous pouvez migrer des bases de données à partir de [!INCLUDE [sskilimanjaro-md](../../includes/sskilimanjaro-md.md)] vers SQL Server 2019.

Pour plus d’informations, consultez le [guide de migration de base de données Azure](https://datamigration.microsoft.com/scenario/sql-to-sqlserver).

Les conseils et les outils suivants peuvent vous aider à planifier et à implémenter votre migration.

- Outils de migration : La migration est prise en charge par le biais de l’[Assistant Migration de données (DMA)](../../dma/dma-overview.md).
- Sauvegarde et restauration : Une sauvegarde effectuée sur SQL Server 2008 ou SQL Server 2008 R2 peut être restaurée sur SQL Server 2019.
- Copie des journaux de transaction : La copie des journaux de transaction est prise en charge si l’instance principale exécute SQL Server 2008 SP3 ou ultérieur, ou SQL Server 2008 R2 SP2 ou ultérieur, et si l’instance secondaire exécute SQL Server 2019. 

   > [!WARNING]
   > Si un basculement automatique ou manuel se produit et que SQL Server 2019 devient l’instance principale, SQL Server 2008 ou SQL Server 2008 R2 devient l’instance secondaire et ne peut pas recevoir de modifications de l’instance principale.

- Chargement en masse : Les tables peuvent être copiées en bloc à partir de SQL Server 2008 ou SQL Server 2008 R2 vers SQL Server 2019.

## <a name="sssqlv15-md-edition-upgrade"></a>[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Mise à niveau d’édition 

Le tableau suivant répertorie les scénarios de mise à niveau d'édition prise en charge dans [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)].  

Pour obtenir des instructions détaillées sur la façon d’effectuer une mise à niveau d’édition, consultez [Mettre à niveau vers une autre édition de SQL Server &#40;Installation&#41;](../../database-engine/install-windows/upgrade-to-a-different-edition-of-sql-server-setup.md).  
  
|Mise à niveau à partir de|Mise à niveau vers|  
|------------------|----------------|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (licence serveur+CAL et licence principale)**|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise |  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Evaluation Enterprise**|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (licence serveur+CAL ou licence principale) <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> La mise à niveau depuis une version d’évaluation (une édition gratuite) vers toutes les éditions payantes est prise en charge pour les installations autonomes, mais pas pour les installations en cluster. Cette limitation ne s’applique pas aux instances autonomes installées sur un cluster de basculement Windows qui est membre d’un groupe de disponibilité. |  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard**|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (licence serveur+CAL ou licence principale)|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer**|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (licence serveur+CAL ou licence principale) <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (licence serveur+CAL ou licence principale) <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express*|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (licence serveur+CAL ou licence principale) <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
  
 En outre vous pouvez également effectuer une mise à niveau d'édition entre [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (licence serveur+CAL) et [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (licence principale) :  
  
|Mise à niveau d'édition depuis|Mise à niveau d'édition vers|  
|--------------------------|------------------------|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (licence serveur+CAL)**|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (licence principale)|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (licence principale)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (licence serveur+CAL)|  
  
 \* S’applique également à [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express with Tools et à [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express with Advanced Services.  
  
 ** Le changement de l’édition d’une instance en cluster de [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] est limitée. Les scénarios suivants ne sont pas pris en charge pour les clusters de basculement [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] :  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise vers [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer, Standard ou Evaluation.  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer vers [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard ou Evaluation.  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard vers [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Evaluation.  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Evaluation vers [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard.  
  
## <a name="see-also"></a>Voir aussi  

 [Éditions et fonctionnalités prises en charge de [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)]](../../sql-server/editions-and-components-of-sql-server-version-15.md)

 [Configurations matérielle et logicielle requises pour l’installation de SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-ver15.md)

 [Mise à niveau vers SQL Server](../../database-engine/install-windows/upgrade-sql-server.md)