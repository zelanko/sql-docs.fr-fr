---
title: Configurations matérielle et logicielle requises pour l’installation de SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 07/10/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Setup [SQL Server], software
- software [SQL Server]
- installing SQL Server, software
- operating systems [SQL Server], SQL Server requirements
- Setup [SQL Server], cross-language support
- operating systems [SQL Server], cross-language support
- network connections [SQL Server], requirements
- disk space [SQL Server], SQL Server installations
- WOW [SQL Server]
- Setup [SQL Server], hardware
- dependencies [SQL Server], SQL Server installations
- cluster hardware requirements [SQL Server]
- endpoints [SQL Server], SQL Server installations
- Internet [SQL Server], SQL Server installations
- hardware [SQL Server]
- Windows on Windows [SQL Server]
- installing SQL Server, hardware
- Setup Configuration Checker
- SCC [SQL Server]
- operating systems [SQL Server]
- space [SQL Server], SQL Server installations
- system configuration checker
- installing SQL Server, cross-language support
- Internet [SQL Server]
- space [SQL Server]
- extended system support [SQL Server]
- 64-bit edition [SQL Server]
- failover clustering [SQL Server]
- failover clustering [SQL Server], hardware requirements
- 32-bit edition [SQL Server]
- locales [SQL Server], SQL Server installations
- cross-language support
- disk space [SQL Server]
- localized SQL Server versions
ms.assetid: 09bcf20b-0a40-4131-907f-b61479d5e4d8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ce6cef69abe7c2461552229363c8334ca56555b4
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75245655"
---
# <a name="hardware-and-software-requirements-for-installing-sql-server-2014"></a>Configurations matérielle et logicielle requises pour l'installation de SQL Server 2014

 > - Essayez SQL Server 2016 en installant ** [gratuitement Developer Edition](https://my.visualstudio.com/Downloads?q=SQL%20Server%20Developer)!**  
  
## <a name="considerations"></a>Considérations 
  
-   Nous vous recommandons [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] d’exécuter sur des ordinateurs avec le format de fichier NTFS. Le système de fichiers FAT32 est pris en charge mais n’est pas recommandé, car il est moins sécurisé que le système de fichiers NTFS.  
  
-   Vous ne pouvez pas installer sur des lecteurs en lecture seule, mappés ou compressés.  
  
-   Pour permettre l’installation correcte du composant Visual Studio, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous devez installer une mise à jour. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Le programme d’installation vérifie la présence de cette mise à jour, puis vous demande de télécharger et d’installer cette mise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à jour avant de pouvoir poursuivre l’installation. Pour éviter l’interruption pendant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’installation, téléchargez et installez la mise à jour **avant d’exécuter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation** comme décrit ci-dessous (ou installez toutes les mises à jour de .net 3,5 SP1 disponibles sur Windows Update) :  
  
    -   Pour [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] SP2, récupérez la mise à jour requise [ici](https://go.microsoft.com/fwlink/?LinkId=198093).  
  
    -   Pour tout autre système d’exploitation pris en charge, cette mise à jour est incluse.  
  
-   L'exécution de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par Terminal Services Client n'est pas prise en charge. L’installation échoue si vous lancez le programme d’installation par le biais du client des services Terminal Server.   
  
-   Le programme d'installation de[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installe les composants logiciels suivants requis par le produit :  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Fichiers de support du programme d’installation  
  
-   Pour connaître la configuration minimale requise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour [!INCLUDE[win8srv](../../includes/win8srv-md.md)] installer [!INCLUDE[win8](../../includes/win8-md.md)]sur ou, consultez [installation de SQL Server sur Windows Server 2012 ou Windows 8](https://support.microsoft.com/kb/2681562) (https://support.microsoft.com/kb/2681562).  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Configuration matérielle et logicielle requise](hardware-and-software-requirements-for-installing-sql-server.md#hwswr)  
  
-   [Processeur, mémoire et système d’exploitation requis](hardware-and-software-requirements-for-installing-sql-server.md#pmosr)  
  
-   [Prise en charge de plusieurs langues](hardware-and-software-requirements-for-installing-sql-server.md#CrossLanguageSupport)  
  
-   [Prise en charge des systèmes étendus](hardware-and-software-requirements-for-installing-sql-server.md#ess)  
  
-   [Espace disque nécessaire (32 et 64 bits)](hardware-and-software-requirements-for-installing-sql-server.md#HardDiskSpace)  
  
-   [Types de stockage pour les fichiers de données](hardware-and-software-requirements-for-installing-sql-server.md#StorageTypes)  
  
-   [Installation d’SQL Server sur un contrôleur de domaine](hardware-and-software-requirements-for-installing-sql-server.md#DC_support)  
  
##  <a name="hwswr"></a>Configuration matérielle et logicielle requise  
 La configuration requise suivante s'applique à toutes les installations de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] :  
  
|Composant|Prérequis|  
|---------------|-----------------|  
|.NET Framework|Le .NET 3.5 SP1 est requis pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] lorsque vous sélectionnez [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)], Réplication ou [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], et qu'il n'est plus installé par le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . <br />-Si vous exécutez le programme d’installation et que vous n’avez pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .net 3,5 SP1, le programme d’installation vous demande de télécharger et d’installer .NET [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 3,5 SP1 avant de poursuivre l’installation. (Installez .NET 3,5 SP1 à partir de [Microsoft .NET Framework 3,5 Service Pack 1](https://www.microsoft.com/download/details.aspx?id=22).) Le message d’erreur contient un lien vers le centre de téléchargement ou vous pouvez télécharger .NET 3,5 SP1 à partir de Windows Update. Pour éviter toute interruption pendant l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous pouvez télécharger et installer .NET 3.5 SP1 avant d'exécuter le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br />-Si vous exécutez le programme d’installation sur [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] un ordinateur [!INCLUDE[win8](../../includes/win8-md.md)]disposant de SP1 ou, vous devez activer .NET Framework [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]3,5 SP1 avant d’installer.<br />-S’il n’y a pas d’accès à Internet, vous devez télécharger et installer .NET Framework 3,5 SP1 avant d’exécuter le programme d’installation pour installer l’un des composants mentionnés ci-dessus. Pour plus d’informations sur les recommandations et des conseils sur l’obtention et l’activation de [!INCLUDE[win8](../../includes/win8-md.md)] .NET Framework [!INCLUDE[win8srv](../../includes/win8srv-md.md)]3,5 sur et, consultez Considérations sur lehttps://msdn.microsoft.com/library/windows/hardware/hh975396) [déploiement de Microsoft .NET Framework 3,5](https://msdn.microsoft.com/library/windows/hardware/hh975396) (.<br /><br /> .NET 4.0 est une condition requise pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installe le .NET 4.0 lors de l'étape d'installation des fonctionnalités.<br />-Si vous installez les [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] éditions, assurez-vous qu’une connexion Internet est disponible sur l’ordinateur. Le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] télécharge et installe le .NET 4 car il n'est pas inclus dans les médias [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].<br />-[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]n’installe pas .NET 4,0 sur le mode Server Core [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] de SP1 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]ou. Vous devez installer le .NET 4.0 avant d'installer [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] sur une installation Server Core de [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 ou [!INCLUDE[win8srv](../../includes/win8srv-md.md)].|  
|Windows PowerShell|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]n’installe pas ou n’active pas Windows PowerShell 2,0 ; Toutefois, Windows PowerShell 2,0 est un composant requis pour [!INCLUDE[ssDE](../../includes/ssde-md.md)] l’installation [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]des composants et. Si le programme d'installation signale que Windows PowerShell 2.0 n'est pas présent, vous pouvez l'installer ou l'activer en suivant les instructions de la page [Structure de gestion Windows](https://go.microsoft.com/fwlink/?LinkId=186214) .|  
|Logiciel réseau|Les systèmes d'exploitation pris en charge pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] possèdent un logiciel réseau intégré. Les instances par défaut et les instances nommées d'une installation autonome prennent en charge les protocoles réseau suivants : protocoles de mémoire partagée, TCP/IP, Canaux nommés et VIA.<br /><br /> Remarque : Le protocole VIA n’est pas pris en charge sur les clusters de basculement. Les clients ou les applications exécutés sur le même nœud du cluster de basculement en tant que l’instance SQL Server peuvent utiliser le protocole de mémoire partagée pour se connecter à SQL Server à l’aide de leur adresse de canal local. Toutefois, ce type de connexion n’est pas adaptée aux clusters et échoue après un basculement de l’instance. Il n’est donc pas recommandé et ne doit être utilisé que dans des scénarios très spécifiques. Le protocole VIA est déconseillé. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<br /><br /> Pour plus d'informations sur les protocoles et les bibliothèques réseau, consultez [Network Protocols and Network Libraries](network-protocols-and-network-libraries.md).|  
|Virtualisation|
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est pris en charge dans les environnements d'ordinateur virtuel qui s'exécutent sur le rôle Hyper-V dans les éditions :<br />-<br />                    Standard, Enterprise et Datacenter de [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2<br />-[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 éditions standard, Enterprise et Datacenter.<br />-<br />                    [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Éditions datacenter et standard.<br /><br /> En plus des ressources requises par la partition parente, chaque ordinateur virtuel (partition enfant) doit être fourni avec des ressources processeur, mémoire et disque suffisantes pour son instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Les configurations requises sont répertoriées ultérieurement dans cette rubrique.\*<br /><br /> Dans le rôle Hyper-V sur [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 ou [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1, un maximum de 4 (quatre) processeurs virtuels peuvent être alloués aux ordinateurs virtuels qui exécutent les éditions [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 32 bits/64 bits, ou [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] et [!INCLUDE[win8srv](../../includes/win8srv-md.md)] 64 bits.<br /><br /> Dans le rôle Hyper-V sur [!INCLUDE[win8srv](../../includes/win8srv-md.md)]:<br />Un maximum de 8 (huit) processeurs virtuels peut être alloué aux ordinateurs virtuels qui exécutent les éditions [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 32 bits/64 bits.<br />Un maximum de 64 (soixante-quatre) processeurs virtuels peuvent être alloués aux ordinateurs virtuels qui exécutent les éditions [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 64-bits ou [!INCLUDE[win8srv](../../includes/win8srv-md.md)] 64-bits.<br /><br /> Pour plus d'informations sur les limites de capacité de calcul pour différentes éditions de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et sur la façon dont ils diffèrent dans les environnements physiques et virtualisés avec les processeurs hyperthreaded, consultez [Compute Capacity Limits by Edition of SQL Server](../compute-capacity-limits-by-edition-of-sql-server.md). Pour plus d'informations sur le rôle Hyper-V, consultez le [site Web de Windows Server 2008](https://go.microsoft.com/fwlink/?LinkId=182820).<br /><br /> ** \* Important \* \* ** Le clustering de basculement invité [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]est pris en charge dans. Pour plus d'informations sur les versions prises en charge de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les systèmes d'exploitation pour le clustering de basculement d'invité, ainsi que sur la prise en charge de la virtualisation, consultez la [Politique de prise en charge pour les produits Microsoft SQL Server exécutés dans un environnement matériel virtuel](https://go.microsoft.com/fwlink/?LinkId=151676).|  
|Disque dur|
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] requiert un minimum de 6 GO d'espace disque disponible.<br /><br /> L'espace disque nécessaire varie selon les composants [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] que vous installez. Pour plus d'informations, consultez [Hard Disk Space Requirements (32-Bit and 64 Bit)](hardware-and-software-requirements-for-installing-sql-server.md#HardDiskSpace) , plus loin dans cette rubrique. Pour plus d'informations sur les types de stockage pris en charge pour les fichiers de données, consultez [Storage Types for Data Files](hardware-and-software-requirements-for-installing-sql-server.md#StorageTypes).|  
|Lecteur|Un lecteur de DVD, selon le cas, est requis pour l'installation à partir d'un disque.|  
|Surveiller|
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] requiert un moniteur avec une résolution Super-VGA (800 x 600) ou supérieure.|  
|Internet|Les fonctionnalités Internet requièrent un accès à Internet (des frais peuvent s'appliquer).|  
  
 * L' [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] exécution sur un ordinateur virtuel sera plus lente que l’exécution en mode natif en raison de la surcharge de la virtualisation.  
  
##  <a name="pmosr"></a>Processeur, mémoire et système d’exploitation requis  
 Les spécifications de mémoire et de processeur suivantes s'appliquent à toutes les éditions de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
|Composant|Prérequis|  
|---------------|-----------------|  
|Mémoire<sup>[1]</sup>|**Minimale**<br /><br /> Éditions Express : 512 MO<br /><br /> Toutes les autres éditions : 1 GO<br /><br /> **Recommandations**<br /><br /> Éditions Express : 1 GO<br /><br /> Toutes les autres éditions : au moins 4 GO, qui doivent être augmentés au fur et à mesure de l'augmentation de la taille de la base de données pour garantir des performances optimales.|  
|Vitesse du processeur|**Minimale**<br /><br /> Processeur x86 : 1,0 GHz<br /><br /> Processeur x64 : 1,4 GHz<br /><br /> **Recommandé :** 2,0 GHz ou plus rapide|  
|Type de processeur|Processeur x64 : AMD Opteron, AMD Athlon 64, Intel Xeon avec prise en charge Intel EM64T Intel Pentium IV avec prise en charge EM64T<br /><br /> Processeur x86 : compatible Pentium III ou supérieur|  
  
 <sup>[1]</sup> La mémoire minimale requise pour installer le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] composant dans [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) est de 2 Go de RAM, ce qui diffère de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] la mémoire minimale requise. Pour obtenir des informations sur l'installation de DQS, consultez [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
 **Prise en charge WOW64 :**  
  
 WOW64 (Windows 32 bits sur Windows 64 bits) est une fonctionnalité des éditions 64 bits de Windows qui permet aux applications 32 bits de s'exécuter de façon native en mode 32 bits. Les applications fonctionnent en mode 32 bits, même si le système d'exploitation sous-jacent est un système 64 bits.  
  
-   Sur un système d'exploitation 64 bits pris en charge, les éditions 32 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent être installées sur le sous-système 32 bits de Windows on Windows (WOW64) d'un serveur 64 bits. WOW64 est pris en charge uniquement pour les instances autonomes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il n'est pas pris en charge pour les installations du cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Pour les installations de l'édition 64 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur les systèmes d'exploitation 64 bits pris en charge, les outils d'administration sont pris en charge dans WOW64. Pour plus d'informations sur les systèmes d'exploitation pris en charge, sélectionnez une édition de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dans les sections ci-dessous.  
  
 **Prise en charge de Server Core :**  

 
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est maintenant pris en charge sur une installation Server Core de Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2, Windows Server 2016 et Windows Server 2019. 

L’installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur le mode Server Core est prise en charge par les éditions suivantes de Windows Server :

|                              |                                |
| :------------------------    | :------------------------------|
| Windows Server 2019 Standard | Windows Server 2019 Datacenter |
| Windows Server 2016 Standard | Windows Server 2016 Datacenter |
| Windows Server 2012 R2 Standard | Windows Server 2012 R2 Datacenter|
| Windows Server 2012 Standard | Windows Server 2012 Datacenter |
| Windows Server 2008 R2 SP1 Standard | Windows Server 2008 R2 SP1 Datacenter |
| Windows Server 2008 R2 SP1 Enterprise | Windows Server 2008 R2 SP1 Web|
   | &nbsp; | &nbsp; |
  
 Pour plus d’informations sur [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] l’installation de sur Server Core, consultez [installer SQL Server 2014 sur Server Core](../../database-engine/install-windows/install-sql-server-on-server-core.md).  
  
   >[!NOTE]
   > Les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont prises en charge sur [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 64 bits x64 édition Standard sont également prises en charge sur [!INCLUDE[sbs_2](../../includes/sbs-2-md.md)] 64 bits x64.  
  
 **Prise en charge du système d’exploitation :**  
  
 Les éditions de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sont classées comme suit :  
  
-   [Principales éditions de SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md#TOP_Principal)  
  
-   [Éditions spécialisées de SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md#TOP_SP)  
  
-   [Éditions transversales de SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md#TOP_Breadth)  
  
###  <a name="TOP_Principal"></a>Conditions requises pour les systèmes d’exploitation des éditions principales  
 Le tableau suivant décrit la configuration requise du système d'exploitation pour les principales éditions de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Édition|32 bits|64 bits|  
|---------------------------------------|-------------|-------------|  
|[!INCLUDE[ssEnterprise](../../includes/ssenterprise-md.md)]|[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Standard 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 standard 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 32 bits<br /><br /> [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]SP2 standard 32 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 32 bits|[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Standard 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 standard 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Business Intelligence|[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Standard 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 standard 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 32 bits<br /><br /> [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]SP2 standard 32 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 32 bits|[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Standard 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 standard 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits|  
|[!INCLUDE[ssStandard](../../includes/ssstandard-md.md)]|Windows 10 Famille 64 bits<br /><br /> Windows 10 Professionnel 64 bits<br /><br /> Windows 10 Entreprise 64 bits<br /><br /> Windows 10 Famille 32 bits<br /><br /> Windows 10 Professionnel 32 bits<br /><br /> Windows 10 Entreprise 32 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Standard 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 standard 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]32 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]32 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]32 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Ultimate 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professionnel 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Ultimate 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Entreprise 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professionnel 32 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 32 bits<br /><br /> [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]SP2 standard 32 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 32 bits|Windows 10 Famille 64 bits<br /><br /> Windows 10 Professionnel 64 bits<br /><br /> Windows 10 Entreprise 64 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Standard 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 standard 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Ultimate 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professionnel 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits| 
  
###  <a name="TOP_SP"></a>Conditions requises pour le système d’exploitation des éditions spécialisées  
 Le tableau suivant décrit la configuration requise du système d'exploitation pour les éditions spécialisées de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Édition|32 bits|64 bits|  
|---------------------------------------|-------------|-------------|  
|[!INCLUDE[ssWeb](../../includes/ssweb-md.md)]|Windows 10 Famille 64 bits<br /><br /> Windows 10 Professionnel 64 bits<br /><br /> Windows 10 Entreprise 64 bits<br /><br /> Windows 10 Famille 32 bits<br /><br /> Windows 10 Professionnel 32 bits<br /><br /> Windows 10 Entreprise 32 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Standard 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 standard 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 32 bits<br /><br /> [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]SP2 standard 32 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 32 bits|Windows 10 Famille 64 bits<br /><br /> Windows 10 Professionnel 64 bits<br /><br /> Windows 10 Entreprise 64 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br />
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Standard 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 standard 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits| 
  
###  <a name="TOP_Breadth"></a>Éditions de largeur configuration requise du système d’exploitation
 Le tableau suivant décrit la configuration requise du système d'exploitation pour les éditions transversales de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Édition|32 bits|64 bits|  
|---------------------------------------|-------------|-------------|  
|[!INCLUDE[ssDeveloper](../../includes/ssdeveloper-md.md)]|Windows 10 Famille 64 bits<br /><br /> Windows 10 Professionnel 64 bits<br /><br /> Windows 10 Entreprise 64 bits<br /><br /> Windows 10 Famille 32 bits<br /><br /> Windows 10 Professionnel 32 bits<br /><br /> Windows 10 Entreprise 32 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br />
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Standard 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 standard 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]32 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]32 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]32 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Ultimate 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professionnel 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Familiale Premium 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Familiale Basique 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Ultimate 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Entreprise 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professionnel 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Familiale Premium 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Familiale Basique 32 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 32 bits<br /><br /> [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]SP2 standard 32 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 32 bits|Windows 10 Famille 64 bits<br /><br /> Windows 10 Professionnel 64 bits<br /><br /> Windows 10 Entreprise 64 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br />
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Standard 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 standard 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Ultimate 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professionnel 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Familiale Premium 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Familiale Basique 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits|  
|[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]|Windows 10 Famille 64 bits<br /><br /> Windows 10 Professionnel 64 bits<br /><br /> Windows 10 Entreprise 64 bits<br /><br /> Windows 10 Famille 32 bits<br /><br /> Windows 10 Professionnel 32 bits<br /><br /> Windows 10 Entreprise 32 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Standard 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 standard 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]32 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]32 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]32 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Ultimate 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professionnel 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Familiale Premium 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Familiale Basique 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Ultimate 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Entreprise 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professionnel 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Familiale Premium 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Familiale Basique 32 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 32 bits<br /><br /> [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]SP2 standard 32 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 32 bits|Windows 10 Famille 64 bits<br /><br /> Windows 10 Professionnel 64 bits<br /><br /> Windows 10 Entreprise 64 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Standard 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 standard 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Ultimate 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professionnel 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Familiale Premium 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Édition Familiale Basique 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits|  
  
## <a name="minimum-sql-server-version-requirements-for-windows-10"></a>Configuration requise d’un ordinateur Windows 10 en fonction de la version de SQL Server  
 Avant d’installer SQL Server sur un ordinateur Windows 10, vous devez veiller à ce que la configuration suivante soit en place :  
  
-   Pour SQL Server 2014, vous devez appliquer SQL Server 2014 Service Pack 1 ou une mise à jour ultérieure. Pour plus d’informations, consultez [Comment obtenir le dernier Service Pack pour SQL Server 2014](https://support.microsoft.com/kb/2958069).  
  
-   Pour SQL Server 2012, vous devez appliquer SQL Server 2012 Service Pack 2 ou une mise à jour ultérieure. Pour plus d’informations, consultez [Comment obtenir le dernier Service Pack pour SQL Server 2012](https://support.microsoft.com/kb/2755533).  
  
-   SQL Server 2008 R2  
    et SQL Server 2008 ne sont pas pris en charge sur Windows 10.  
  
##  <a name="CrossLanguageSupport"></a>Prise en charge de plusieurs langues  
 Pour plus d’informations sur la prise en charge de plusieurs langues et sur les considérations relatives à l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans les langues localisées, consultez [Versions linguistiques locales dans SQL Server](local-language-versions-in-sql-server.md)  
  
##  <a name="ess"></a>Prise en charge étendue du système  
 Les versions 64 bits de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] intègrent la prise en charge des systèmes étendus, également appelée Windows 32-bit sur Windows 64-bit (WOW64). WOW64 est une fonctionnalité des éditions 64 bits de Windows qui permet aux applications 32 bits de s'exécuter de façon native en mode 32 bits. Les applications fonctionnent en mode 32 bits, même si le système d'exploitation sous-jacent est un système 64 bits.  
  
##  <a name="HardDiskSpace"></a>Espace disque requis (32 bits et 64 bits)  
 Pendant l’installation Windows Installer crée des fichiers temporaires sur le lecteur système. Avant d’exécuter le programme d’installation ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de mise à niveau, vérifiez que vous disposez d’au moins **6,0 Go** d’espace disque disponible sur le lecteur système pour ces fichiers. Cette condition s’applique même si vous installez des composants sur un lecteur autre que celui par défaut.  
  
 L'espace disque nécessaire peut varier selon la configuration du système et les fonctionnalités installées. Pour obtenir la liste des fonctionnalités prises en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]les éditions de, consultez [fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). Le tableau suivant présente l'espace disque nécessaire pour les composants [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
|**Fonctionnalité**|**Espace disque requis**|  
|-----------------|--------------------------------|  
|
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] et fichiers de données, réplication, recherche en texte intégral et Data Quality Services|811 Mo|  
|
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et fichiers de données|345 Mo|  
|
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et Gestionnaire de rapports|304 Mo|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|591 Mo|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|243 Mo|  
|Composants clients (autres que la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les outils Integration Services)|1823 Mo|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Composants de la documentation en ligne pour afficher et gérer le contenu d’aide<sup>1</sup>|375 Ko|  
  
 <sup>1</sup> L’espace disque requis pour le contenu de la documentation en ligne téléchargé est de 200 Mo.  
  
##  <a name="StorageTypes"></a>Types de stockage pour les fichiers de données  
 Les types de stockage pris en charge pour les fichiers de données sont :  
  
-   Disque local  
  
-   Stockage partagé  
  
-   Partage de fichiers SMB  
  
    > **Remarque :**  Le stockage SMB n’est pas [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pris en charge pour les fichiers de données des installations autonomes ou en cluster. Utilisez le stockage attaché direct ou un réseau de stockage à la place.  
  
    > **IMPORTANT !** Le stockage SMB peut être hébergé par un serveur de fichiers Windows ou un dispositif de stockage SMB tiers. Si vous utilisez un serveur de fichiers Windows, il doit s'agir de la version 2008 ou ultérieure. Pour plus d'informations sur l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le partage de fichiers SMB comme option de stockage, consultez [Install SQL Server with SMB Fileshare as a Storage Option](../../database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option.md).  
  
    > **!!!! D’avertissement**  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge uniquement le disque local pour l'installation des fichiers tempdb. Assurez-vous que le chemin d’accès spécifié pour les fichiers journaux et de données tempdb est valide sur **tous** les nœuds du cluster. Pendant le basculement, si les répertoires tempdb ne sont pas disponibles sur le nœud de basculement cible, la ressource [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sera pas en ligne.  
  
##  <a name="DC_support"></a>Installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un contrôleur de domaine-limitations  
 Pour des raisons de sécurité, nous recommandons de ne pas installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur un contrôleur de domaine. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne bloquera pas l'installation sur un ordinateur qui est contrôleur de domaine, mais les limitations suivantes s'appliquent :  
  
-   Vous ne pouvez pas exécuter les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un contrôleur de domaine sous un compte de service local.  
  
-   Après avoir installé sur un ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous ne pouvez pas modifier l'ordinateur d'un membre de domaine en un contrôleur de domaine. Vous devez désinstaller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant de modifier l'ordinateur hôte en un contrôleur de domaine.  
  
-   Après avoir installé sur un ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous ne pouvez pas modifier l'ordinateur d'un contrôleur de domaine en un membre de domaine. Vous devez désinstaller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant de modifier l'ordinateur hôte en un membre de domaine.  
  
-   Les instances de cluster de basculement[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sont pas prises en charge quand les nœuds du cluster sont des contrôleurs de domaine.  
  
-   Le programme d'installation de[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas créer de groupes de sécurité ni configurer de comptes de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un contrôleur de domaine en lecture seule. Dans ce scénario, le programme d'installation échoue.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification d’une installation de SQL Server](planning-a-sql-server-installation.md)   
 [Considérations sur la sécurité pour une installation SQL Server](security-considerations-for-a-sql-server-installation.md)   
 [Spécifications de produit pour SQL Server 2014](../../getting-started/sql-server-2014-product-specifications.md)  
