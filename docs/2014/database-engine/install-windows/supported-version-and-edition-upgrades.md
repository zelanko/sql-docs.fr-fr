---
title: Mises à niveau de version et d’édition prises en charge | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 4a245aab71292e1482bd5a17bd32a27bded640ab
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018584"
---
# <a name="supported-version-and-edition-upgrades"></a>Mises à niveau de version et d’édition prises en charge
  Vous pouvez effectuer une mise à niveau depuis [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] et [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Cette rubrique répertorie les chemins de mise à niveau pris en charge à partir de ces versions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , et les mises à niveau d'édition prises en charge pour [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
## <a name="pre-upgrade-checklist"></a>Liste de contrôle préalable à la mise à niveau  
  
-   Avant de mettre à niveau une édition de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] vers une autre édition, vérifiez si les fonctionnalités que vous utilisez actuellement sont prises en charge dans l'édition vers laquelle vous vous déplacez.  
  
-   Avant de mettre à niveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], activez l'authentification Windows pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent et vérifiez la configuration par défaut : le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être membre du groupe sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Pour procéder à une mise à niveau vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], vous devez exécuter un système d'exploitation pris en charge. Pour plus d'informations, consultez [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   La mise à niveau sera bloquée s'il existe un redémarrage en attente.  
  
-   La mise à niveau sera bloquée si le service Windows Installer ne s'exécute pas.  
  
## <a name="unsupported-scenarios"></a>Scénarios non pris en charge  
  
-   Les instances inter-versions de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ne sont pas prises en charge. Les numéros de version des composants [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] doivent être identiques dans une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   La mise à niveau interplateforme n'est pas prise en charge. Vous ne pouvez pas mettre à niveau une instance 32 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers une instance native 64 bits à l'aide du programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez toutefois sauvegarder ou détacher des bases de données d'une instance 32 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis les restaurer ou les attacher sur une nouvelle instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (64 bits) si les bases de données ne sont pas publiées dans la réplication. Vous devez recréer toute connexion et tout autre objet utilisateur dans les bases de données système master, msdb et model.  
  
-   Vous ne pouvez pas ajouter de nouvelles fonctionnalités pendant la mise à niveau de votre instance existante de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Après avoir mis à niveau une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez ajouter des fonctionnalités via le programme d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour plus d’informations, consultez [ajouter des fonctionnalités à une Instance de SQL Server 2014 &#40;le programme d’installation&#41;](add-features-to-an-instance-of-sql-server-setup.md).  
  
-   Les clusters de basculement ne sont pas pris en charge en mode WOW.  
  
-   La mise à niveau à partir d'une version d'évaluation précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas prise en charge.  
  
## <a name="upgrades-from-earlier-versions-to-includesssql14includessssql14-mdmd"></a>Mises à niveau des versions antérieures vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
> [!NOTE]  
>  La prise en charge de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] est décrite plus en détail dans la section suivante, « Prise en charge[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] pour [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]».  
  
-   Les éditions 32 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent être mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dans le sous-système 32 bits (WOW64) d'un serveur 64 bits.  
  
-   Les versions 64 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent être mises à niveau uniquement vers un serveur 64 bits [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Lorsque vous effectuez la mise à niveau vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] d'une version antérieure de l'édition Enterprise de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , choisissez entre Enterprise Edition : contrat de licence selon le nombre de cœurs et Enterprise Edition. Ces éditions Enterprise se différencient uniquement par leur mode de licences et le nombre maximal de noyaux pris en charge. Pour plus d’informations, voir [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] prend en charge la mise à niveau à partir des versions suivantes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 ou version ultérieure  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 ou ultérieur  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 ou version ultérieure  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 ou version ultérieure  
  
 Le tableau ci-dessous répertorie les scénarios de mise à niveau pris en charge depuis des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
|Mise à niveau à partir de|Chemin d'accès de mise à niveau pris en charge|  
|------------------|----------------------------|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 Enterprise|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 Developer|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 Standard|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 Workgroup|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 Express,<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 Express with Tools, et<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 Express with Advanced Services|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Enterprise|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Developer|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Standard|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Small Business|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Web|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Workgroup|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Express,<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Express with Tools, et<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Express with Advanced Services|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Datacenter|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Enterprise|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Developer|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Small Business|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Standard|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Web|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Workgroup|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Express,<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Express with Tools, et<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Express with Advanced Services|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Enterprise|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Developer|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Standard|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Web|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Express,<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Express with Tools, et<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Express Management Studio, et<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Express with Advanced Services|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Business Intelligence|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
  
### <a name="includesssql14includessssql14-mdmd-support-for-includessversion2005includesssversion2005-mdmd"></a>[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Prise en charge pour [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
 Cette section aborde la prise en charge de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] pour [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Dans [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], vous pouvez effectuer les opérations suivantes :  
  
-   Mettre à niveau une instance [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] du moteur de base de données [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] en exécutant le programme d'installation de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] avec l'assistant d'installation ou à partir de l'invite de commandes.  
  
-   Attacher une base de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (fichiers mdf/ldf) à l'instance [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] du moteur de base de données.  
  
-   Restaurer une base de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] vers l'instance [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] du moteur de base de données à partir d'une sauvegarde.  
  
-   Mettre à niveau un package [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. Exécuter des packages avec mise à niveau automatique sur place.  
  
-   Mettre à niveau un [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] en exécutant le programme d'installation de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
-   Sauvegarder un cube [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] et le restaurer sur [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
-   Mettre à niveau [!INCLUDE[ssRSversion2005](../../includes/ssrsversion2005-md.md)] vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] en exécutant le programme d'installation de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] .  
  
-   Se connecter à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]à l'aide de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 2014.  
  
 Lorsqu'une base de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] est mise à niveau vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], le niveau de compatibilité de cette base de données passe de 90 à 100. (Dans [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], les valeurs valides du niveau de compatibilité de la base de données sont 100, 110 et 120.) [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) explique comment la modification du niveau de compatibilité peut affecter les applications [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les scénarios non spécifiés dans la liste ci-dessus ne sont pas pris en charge, notamment :  
  
-   Installation de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] sur le même ordinateur (côte à côte).  
  
-   Utilisation d'une instance de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] comme membre de la topologie de réplication qui implique une instance de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
-   Configuration de la mise en miroir de bases de données entre les instances [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
-   Sauvegarde du journal des transactions avec la copie des journaux de transaction entre les instances [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
-   Configuration des serveurs liés entre les instances [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
-   Gestion d'une instance de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] à partir de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Management Studio.  
  
-   Attachement d'un cube [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] dans [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Management Studio.  
  
-   Connexion à [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] depuis [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Management Studio.  
  
-   Gestion d'un service [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] à partir de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Management Studio.  
  
-   Prise en charge des composants personnalisés Integration Services tiers de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , par exemple, pour l'exécution et la mise à niveau.  
  
## <a name="includesssql14includessssql14-mdmd-edition-upgrade"></a>[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Mise à niveau d’édition  
 Le tableau suivant répertorie les scénarios de mise à niveau d'édition prise en charge dans [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
 Pour obtenir des instructions détaillées sur la façon d’effectuer une mise à niveau d’édition, consultez [mise à niveau vers une édition différente de SQL Server 2014 &#40;le programme d’installation&#41;](upgrade-to-a-different-edition-of-sql-server-setup.md).  
  
|Mise à niveau à partir de|Mise à niveau vers|  
|------------------|----------------|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (licence serveur + CAL et licence principale) <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (licence serveur+CAL ou licence principale)|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Evaluation Enterprise <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (licence serveur+CAL ou licence principale)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> La mise à niveau depuis Evaluation Enterprise (une édition gratuite) vers toutes les éditions payantes est prise en charge pour les installations autonomes, mais pas pour les installations en cluster.|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (licence serveur+CAL ou licence principale)|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Développeur <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (licence serveur+CAL ou licence principale)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (licence serveur+CAL ou licence principale)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express <sup>1</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (licence serveur+CAL ou licence principale)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|  
  
 En outre vous pouvez également effectuer une mise à niveau d'édition entre [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (licence serveur+CAL) et [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (licence principale) :  
  
|Mise à niveau d'édition depuis|Mise à niveau d'édition vers|  
|--------------------------|------------------------|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (licence serveur + CAL) <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (licence principale)|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (licence principale)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (licence serveur+CAL)|  
  
 <sup>1</sup> s’applique également aux [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express with Tools et [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express with Advanced Services.  
  
 <sup>2</sup> modification de l’édition d’un [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] cluster de basculement est limité. Les scénarios suivants ne sont pas pris en charge pour les clusters de basculement [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] :  
  
-   SQL Server 2014 Enterprise vers SQL Server 2014 Developer, Standard ou Enterprise Evaluation.  
  
-   SQL Server 2014 Developer vers SQL Server 2014 Standard ou Enterprise Evaluation.  
  
-   SQL Server 2014 Standard vers SQL Server 2014 Enterprise Evaluation.  
  
-   SQL Server 2014 Enterprise Evaluation vers SQL Server 2014 Standard.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Matérielle et logicielle requise pour l’installation de SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)   
 [Mise à niveau vers SQL Server 2014](upgrade-sql-server.md)   
 [Utiliser le Conseiller de mise à niveau pour la préparation des mises à niveau](../../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
  
