---
title: "Utiliser plusieurs versions et instances de SQL&#160;Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installations simultanées [SQL Server]"
  - "versions [SQL Server], multiples"
  - "installations côte à côte [SQL Server]"
  - "plusieurs versions de composants SQL Server"
  - "installation de SQL Server, installations côte à côte"
  - "installation [SQL Server], installations côte à côte"
  - "édition 64 bits [SQL Server]"
  - "édition 32 bits [SQL Server]"
  - "éditions [SQL Server], installations côte à côte"
ms.assetid: 93acefa8-bb41-4ccc-b763-7801f51134e0
caps.latest.revision: 67
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 67
---
# Utiliser plusieurs versions et instances de SQL&#160;Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge plusieurs instances du [!INCLUDE[ssDE](../../includes/ssde-md.md)], d’[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur le même ordinateur. Vous pouvez également mettre à niveau des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou installer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur où des versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont déjà installées. Pour connaître les scénarios de mise à niveau pris en charge, consultez [Mises à niveau de la version et de l’édition prises en charge](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
## Composants et numérotation de version  
 Les concepts suivants sont utiles pour comprendre le comportement de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les instances côte à côte de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le format de version de produit standard pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est MM.nn.bbbb.rr, où chaque segment est défini comme suit :  
  
 MM - Version principale  
  
 nn - Version secondaire  
  
 bbbb - Numéro de build  
  
 rr - Numéro de révision de build  
  
 Dans chaque version finale principale ou secondaire de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le numéro de version est incrémenté afin de la différencier des versions antérieures. Cette modification de la version est utilisée à de nombreuses fins. Cela comprend l'affichage des informations sur la version dans l'interface utilisateur, le contrôle de la manière dont les fichiers sont remplacés pendant la mise à niveau, l'application des Service Packs, et cela joue également le rôle de mécanisme pour la différentiation fonctionnelle entre les versions consécutives.  
  
### Composants partagés par toutes les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Certains composants sont partagés par toutes les instances de toutes les versions installées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Lorsque vous installez des versions différentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] côte à côte sur le même ordinateur, ces composants sont mis à niveau automatiquement vers la version la plus récente. Ces composants sont habituellement désinstallés automatiquement lorsque la dernière instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est désinstallée.  
  
 Exemples : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser et Enregistreur Microsoft VSS [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### Composants partagés par toutes les instances de la même version principale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les versions qui ont le même numéro de version principale partagent certains composants d’une instance à l’autre. Si les composants partagés sont sélectionnés pendant la mise à niveau, les composants existants sont mis à niveau vers la version la plus récente.  
  
 Exemples : [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] et documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### Composants partagés par les versions secondaires  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les versions qui ont le même numéro de version principale.secondaire partagent des composants.  
  
 Exemple : fichiers de support d'installation.  
  
### Composants spécifiques à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Certains composants ou services de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont spécifiques à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ils sont également définis comme étant dépendants de l'instance. Ils partagent la même version que l'instance qui les héberge et sont utilisés exclusivement pour cette instance.  
  
 Exemples : [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
### Composants qui sont indépendants des versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Certains composants sont installés pendant l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais sont indépendant des versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ils peuvent être partagés par les versions principales ou par toutes les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Exemples : Microsoft Sync Framework, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 Pour plus d’informations sur l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, consultez [Installer SQL Server 2016 avec l’Assistant Installation &#40;programme d’installation&#41;](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md). Pour plus d’informations sur la désinstallation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, consultez [Désinstaller une instance existante de SQL Server &#40;programme d’installation&#41;](../../sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md).  
  
## Utilisation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] côte à côte avec les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Vous pouvez installer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur exécutant déjà les instances d'une version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si une instance par défaut existe sur l'ordinateur, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être installé comme instance nommée.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep ne prend pas en charge une installation côte à côte d’instances préparées de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] avec des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le même ordinateur. Par exemple, vous ne pouvez pas préparer d'instance [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] côte à côte avec une instance préparée de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Toutefois, vous pouvez installer plusieurs instances préparées de la même version principale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] côte à côte sur le même ordinateur. Pour plus d'informations, consultez [Considerations for Installing SQL Server Using SysPrep](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md).  
>   
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ne peut pas être installé côte à côte avec des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur qui exécute Windows Server 2008 R2 Server Core SP1. Pour plus d’informations sur les installations Server Core, consultez [Installer SQL Server 2016 sur Server Core](../../database-engine/install-windows/install-sql-server-2016-on-server-core.md).  
  
 Le tableau suivant répertorie la prise en charge côte à côte de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] :  
  
|Instance existante de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|Prise en charge côte à côte|  
|--------------------------------------------------|----------------------------|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (64 bits) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (32 bits)<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (64 bits) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (32 bits)<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (64 bits) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] (32 bits)<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] (64 bits) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (32 bits)<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (64 bits) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (32 bits)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (64 bits) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]|  
  
## Éviter les conflits d'adresse IP  
 Lorsqu'une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installée côte à côte avec une instance autonome de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], prenez soin d'éviter les conflits de numéro de port TCP sur les adresses IP. Les conflits se produisent généralement lorsque deux instances de [!INCLUDE[ssDE](../../includes/ssde-md.md)] sont configurées pour utiliser le port TCP par défaut (1433). Pour éviter des conflits, configurez une instance pour utiliser un port fixe non défini par défaut. La configuration d'un port fixe est généralement plus simple sur l'instance autonome. La configuration de [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour utiliser des ports différents empêche un conflit inattendu adresse IP/port TCP qui bloque un démarrage de l'instance lorsqu'une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] échoue au nœud en attente  
  
## Voir aussi  
 [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)   
 [Installer SQL Server 2016 avec l’Assistant Installation &#40;programme d’installation&#41;](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md)   
 [Mises à niveau de la version et de l'édition prises en charge](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Mettre à niveau vers SQL Server 2016](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)   
 [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)   
 [Compatibilité descendante_supprimé](../Topic/Backward%20Compatibility_deleted.md)  
  
  