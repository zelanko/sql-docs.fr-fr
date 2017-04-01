---
title: "Mises &#224; niveau de la version et de l&#39;&#233;dition prises en charge | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "composants [SQL Server], ajout aux installations existantes"
  - "versions [SQL Server], mise à niveau"
  - "mise à niveau de SQL Server, mises à niveau prises en charge"
  - "prise en charge multilingue"
ms.assetid: 702359c4-6ca9-42a8-860c-a95a802898a1
caps.latest.revision: 148
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 147
---
# Mises &#224; niveau de la version et de l&#39;&#233;dition prises en charge
  Vous pouvez effectuer une mise à niveau à partir de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]et [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. Cette rubrique répertorie les chemins de mise à niveau pris en charge à partir de ces versions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , et les mises à niveau d'édition prises en charge pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## Liste de contrôle préalable à la mise à niveau  
  
-   Avant de mettre à niveau une édition de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] vers une autre édition, vérifiez si les fonctionnalités que vous utilisez actuellement sont prises en charge dans l'édition vers laquelle vous vous déplacez.  
  
-   Avant de mettre à niveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], activez l'authentification Windows pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent et vérifiez la configuration par défaut : le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être membre du groupe sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Pour procéder à une mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous devez exécuter un système d'exploitation pris en charge. Pour plus d’informations, consultez [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md).  
  
-   La mise à niveau sera bloquée s'il existe un redémarrage en attente.  
  
-   La mise à niveau sera bloquée si le service Windows Installer ne s'exécute pas.  
  
## Scénarios non pris en charge  
  
-   Les instances inter-versions de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ne sont pas prises en charge. Les numéros de version des composants [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] doivent être identiques dans une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   SQL Server 2016 est uniquement disponible pour les plateformes 64 bits. La mise à niveau interplateforme n'est pas prise en charge. Vous ne pouvez pas mettre à niveau une instance 32 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers une instance native 64 bits à l'aide du programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez toutefois sauvegarder ou détacher des bases de données d'une instance 32 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis les restaurer ou les attacher sur une nouvelle instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (64 bits) si les bases de données ne sont pas publiées dans la réplication. Vous devez recréer toute connexion et tout autre objet utilisateur dans les bases de données système master, msdb et model.  
  
-   Vous ne pouvez pas ajouter de nouvelles fonctionnalités pendant la mise à niveau de votre instance existante de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Après avoir mis à niveau une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez ajouter des fonctionnalités via le programme d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour plus d’informations, consultez [Ajouter des fonctionnalités à une instance de SQL Server 2016 &#40;programme d’installation&#41;](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md).  
 
-   Les clusters de basculement ne sont pas pris en charge en mode WOW.  
  
-   La mise à niveau à partir d'une version d'évaluation précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas prise en charge.  
  
## Mises à niveau des versions antérieures vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 
SQL Server 2016 prend en charge la mise à niveau à partir des versions suivantes de SQL Server :
 
- SQL Server 2008 SP3 ou version ultérieure
- SQL Server 2008 R2 SP2 ou version ultérieure
- SQL Server 2012 SP2 ou version ultérieure
- SQL Server 2014 ou version ultérieure 
 

  
> [!NOTE]  
>  Pour mettre à niveau des bases de données sur [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], consultez [Prise en charge de 2005](#SupportFor2005).  
  
 Le tableau ci-dessous répertorie les scénarios de mise à niveau pris en charge depuis des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
|Mise à niveau à partir de|Chemin d'accès de mise à niveau pris en charge|  
|------------------|----------------------------|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Enterprise|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Developer|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Standard|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Small Business|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Workgroup|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Express |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Datacenter|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Enterprise|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Developer|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Small Business|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Standard|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Workgroup|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Express |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Enterprise|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Developer|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Développeur <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Standard|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Express |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express <br/> <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Business Intelligence|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Evaluation|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Développeur|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Evaluation|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Développeur|  
|[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] version Release Candidate (RC)* |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise |  
|[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] Développeur |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise | 

 \* La prise en charge Microsoft de la mise à niveau à partir de la version Release Candidate (RC) s’adresse particulièrement aux clients qui ont participé au programme TAP (Technology Adoption Program). 

   
###  <a name="SupportFor2005"></a> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Prise en charge pour [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
 Cette section aborde la prise en charge de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez effectuer les opérations suivantes :  
  
-   Attacher une base de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (fichiers mdf/ldf) à l'instance [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du moteur de base de données.  
  
-   Restaurer une base de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] vers l'instance [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du moteur de base de données à partir d'une sauvegarde.  
  
-   Sauvegarder un cube [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] et le restaurer sur [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Lorsqu'une base de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] est mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], le niveau de compatibilité de cette base de données passe de 90 à 100. (Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], les valeurs valides du niveau de compatibilité de la base de données sont 100, 110, 120 et 130.) [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md) explique comment la modification du niveau de compatibilité peut affecter les applications [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les scénarios non spécifiés dans la liste ci-dessus ne sont pas pris en charge, notamment :  
  
-   Installation de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur le même ordinateur (côte à côte).  
  
-   Utilisation d'une instance de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] comme membre de la topologie de réplication qui implique une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   Configuration de la mise en miroir de bases de données entre les instances [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
-   Sauvegarde du journal des transactions avec la copie des journaux de transaction entre les instances [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
-   Configuration des serveurs liés entre les instances [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
-   Gestion d'une instance de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] à partir de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Management Studio.  
  
-   Attachement d'un cube [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Management Studio.  
  
-   Connexion à [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] depuis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Management Studio.  
  
-   Gestion d'un service [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] à partir de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Management Studio.  
  
-   Prise en charge des composants personnalisés Integration Services tiers de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], par exemple, pour l'exécution et la mise à niveau.  
  
## [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Mise à niveau d’édition  
 Le tableau suivant répertorie les scénarios de mise à niveau d'édition prise en charge dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Pour obtenir des instructions détaillées sur la façon d’effectuer une mise à niveau d’édition, consultez [Mettre à niveau vers une autre édition de SQL Server 2016 &#40;programme d’installation&#41;](../../database-engine/install-windows/upgrade-to-a-different-edition-of-sql-server-2016-setup.md).  
  
|Mise à niveau à partir de|Mise à niveau vers|  
|------------------|----------------|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licence serveur+CAL et licence principale)**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise |  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation Enterprise**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licence serveur+CAL ou licence principale) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> La mise à niveau depuis une version d’évaluation (une édition gratuite) vers toutes les éditions payantes est prise en charge pour les installations autonomes, mais pas pour les installations en cluster.|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licence serveur+CAL ou licence principale)|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licence serveur+CAL ou licence principale) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licence serveur+CAL ou licence principale) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express*|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licence serveur+CAL ou licence principale) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Développeur <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
  
 En outre vous pouvez également effectuer une mise à niveau d'édition entre [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licence serveur+CAL) et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licence principale) :  
  
|Mise à niveau d'édition depuis|Mise à niveau d'édition vers|  
|--------------------------|------------------------|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licence serveur+CAL)**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licence principale)|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licence principale)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (licence serveur+CAL)|  
  
 \* S’applique également à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express with Tools et à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express with Advanced Services.  
  
 ** La modification de l’édition d’un cluster de basculement [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est limitée à certains scénarios. Les scénarios suivants ne sont pas pris en charge pour les clusters de basculement [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] :  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer, Standard ou Evaluation.  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard ou Evaluation.  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation.  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard.  
  
## Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)   
 [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)   
 [Mettre à niveau vers SQL Server 2016](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)  
  
  