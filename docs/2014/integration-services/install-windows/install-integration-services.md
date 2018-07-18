---
title: Installer Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, installing
- SSIS, installing
- installing Integration Services, about installing Integration Services
- SQL Server Integration Services, installing
- Setup [Integration Services], about installing Integration Services
- installing Integration Services
- Setup [Integration Services]
ms.assetid: bd20fd3a-414b-4581-959d-ebba4ddf5a55
caps.latest.revision: 100
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cd10fc638ed7a1d9c42b926190eebc0df5dd37b8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37156527"
---
# <a name="install-integration-services"></a>Installer Integration Services
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit un programme d'installation unique pour installer tout ou une partie de ses composants, y compris [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Le programme d'installation vous permet d'installer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] avec ou sans d'autres composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur unique.  
  
 Cette rubrique met l'accent sur quelques facteurs importants qu'il convient de prendre en compte avant d'installer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Les informations dans cette rubrique vous aideront à évaluer les options d'installation afin que vous puissiez effectuer des sélections garantissant la réussite de l'installation.  
  
 Cette rubrique ne contient pas d'instructions relatives au démarrage du programme d'installation, à l'utilisation de l'Assistant Installation ou à l'exécution du programme d'installation à partir de la ligne de commande. Pour obtenir des instructions détaillées sur la façon de démarrer le programme d’installation et sélectionnez les composants à installer, consultez [Installation de démarrage rapide de SQL Server 2014](../../getting-started/quick-start-installation-of-sql-server-2014.md). Pour plus d’informations sur les options de ligne de commande pour l’installation [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [installer SQL Server 2014 à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
## <a name="preparing-to-install-integration-services"></a>Préparation à l'installation d'Integration Services  
 Avant d'installer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vérifiez les éléments requis suivants :  
  
-   [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [Paramètres de l’outil d’analyse de configuration système](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)  
  
-   [Considérations sur la sécurité pour une installation SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
## <a name="selecting-an-integration-services-configuration"></a>Sélection d'une configuration Integration Services  
 Vous pouvez installer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans les configurations suivantes :  
  
-   Vous pouvez installer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur un ordinateur dépourvu d’instances antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Vous pouvez installer [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] côte à côte avec une instance existante de [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] et de [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)].  
  
     Lorsque vous mettez à niveau vers [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] sur un ordinateur sur lequel une de ces versions antérieures d' [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est déjà installée, [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] est installé côte à côte avec une version antérieure.  
  
     Pour plus d’informations sur la mise à niveau de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Mettre à niveau des packages Integration Services](upgrade-integration-services.md). Pour plus d’informations sur la compatibilité descendante avec les versions antérieures de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Compatibilité descendante d’Integration Services](../integration-services-backward-compatibility.md).  
  
## <a name="installing-integration-services"></a>installation d'Integration Services  
 Après avoir pris connaissance de la configuration requise pour l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et vérifié que votre ordinateur répondait à ces critères, vous pouvez installer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
> [!NOTE]  
>  Dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], par défaut, lorsque vous installiez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , tous les utilisateurs du groupe Utilisateurs avaient accès au service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Lorsque vous installez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], les utilisateurs n'ont pas accès au service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Ce service est sécurisé par défaut. Après avoir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrateur doit exécuter l’outil de Configuration de DCOM (Dcomcnfg.exe) pour accorder l’accès des utilisateurs spécifiques à **SQL Server Integration Services 12.0**.  
>   
>  Pour obtenir des instructions sur la manière d'octroyer des autorisations, consultez [Grant Permissions to Integration Services Service](../grant-permissions-to-integration-services-service.md).  
  
 Si vous utilisez l'Assistant Installation pour installer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous utiliserez une série de pages pour spécifier les composants et les options. Les éléments suivants sont des pages dans l’Assistant installation où les options que vous sélectionnez affectent votre installation de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] avec des recommandations de sélection :  
  
-   **Sélection de fonctionnalités**  
  
     Sélectionnez **Integration Services** pour installer le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et pour exécuter des packages en dehors de l'environnement de conception.  
  
     Pour une installation complète de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], qui inclut les outils et la documentation relative au développement et à la gestion des packages, sélectionnez à la fois **Integration Services** et les **Fonctionnalités partagées**suivantes :  
  
    -   **SQL Server Data Tools** pour installer les outils servant à concevoir des packages.  
  
    -   **Outils de gestion - Complet** pour installer [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] afin de gérer les packages.  
  
    -   **Kit de développement logiciel (SDK) des outils clients** pour installer des assemblies gérés concernant la programmation [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     De nombreuses solutions d'entreposage de données requièrent également l'installation de composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supplémentaires, tels que le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
    > [!NOTE]  
    >  Parmi les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous pouvez sélectionner dans la page **Sélection de composant** de l’Assistant Installation, certains n’installent qu’une partie des composants [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Ces composants sont utiles pour des tâches spécifiques, mais les fonctionnalités de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] s'en trouvent limitées. Par exemple, l'option **Services Moteur de base de données** installe les composants [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] requis pour l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L'option **Outils de données SQL Server** installe les composants [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nécessaires à la conception d'un package, mais le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n'est pas installé et vous ne pouvez pas exécuter de packages en-dehors de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Pour garantir une installation complète de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous devez sélectionner **Integration Services** dans la page **Sélection de composant** .  
  
     **Installation sur un ordinateur 64 bits** Sur un ordinateur 64 bits, si vous sélectionnez **Integration Services** , le programme installe uniquement la version 64 bits du runtime et des outils. Si vous devez exécuter les packages en mode 32 bits, vous devez également sélectionner une option supplémentaire pour installer le runtime et les outils 32 bits :  
  
    -   Si l’ordinateur 64 bits exécute le système d’exploitation de x86, sélectionnez **SQL Server Data Tools** ou **outils de gestion - complet**.  
  
    -   Si l’ordinateur 64 bits exécute le [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] système d’exploitation, sélectionnez **outils de gestion - complet**.  
  
     **Installation sur un serveur dédié pour ETL** Pour utiliser un serveur dédié pour les processus d’extraction, de transformation et de chargement (ETL), nous vous recommandons d’installer une instance locale du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] lorsque vous installez [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stocke habituellement les packages dans une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et compte sur l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la planification de ces packages. Si le serveur ETL ne dispose pas d'une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)], vous devrez planifier ou exécuter les packages à partir d'un serveur qui possède une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Cela signifie que les packages ne s'exécuteront pas sur le serveur ETL, mais sur le serveur à partir duquel ils ont été démarrés. En conséquence, les ressources du serveur ETL dédié ne sont pas utilisées comme prévu. De plus, les ressources d'autres serveurs peuvent être éprouvées par les processus ETL en cours d'exécution  
  
-   **Configuration de l’instance**  
  
     Aucune sélection effectuée dans la page **Configuration de l'instance** n'affecte [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ou le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Vous pouvez installer une seule instance du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur un ordinateur. Vous vous connectez au service en utilisant le nom d'ordinateur.  
  
     Par défaut, le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est configuré pour gérer les packages qui sont stockés dans la base de données **msdb** , dans l'instance du moteur de base de données qui est installée au même moment qu' [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Si une instance du moteur de base de données n'est pas installée au même moment qu' [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est configuré pour gérer les packages qui sont stockés dans la base de données **msdb** de l'instance locale par défaut du [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Pour gérer des packages stockés dans une instance nommée ou une instance distante de [!INCLUDE[ssDE](../../includes/ssde-md.md)], ou dans plusieurs instances de [!INCLUDE[ssDE](../../includes/ssde-md.md)], vous devez modifier le fichier de configuration. Pour plus d’informations sur la modification de ce fichier de configuration, consultez [Configuration du service Integration Services &#40;Service SSIS&#41;](../service/integration-services-service-ssis-service.md).  
  
-   **Configuration du serveur**  
  
     Passez en revue les paramètres du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans l'onglet **Comptes de service** de la page **Configuration du serveur** .  
  
     Si Windows 7 ou Windows Server 2008 R2 est installé, le [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service est inscrit pour s’exécuter sous le compte virtuel NT Services\MsDtsServer120 et le **Type de démarrage** est **automatique**.  Vous n'êtes pas tenu d'entrer un mot de passe pour le compte virtuel. Si Microsoft Vista ou Windows Server 2008 est installé, le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est inscrit pour s’exécuter sous le compte Service Réseau intégré et le **Type de démarrage** est **Automatique**. Vous n'êtes pas tenu d'entrer un mot de passe pour le compte de service réseau intégré.  
  
 Par défaut, dans une nouvelle installation, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est configuré de façon à ne pas journaliser les événements en rapport avec l'exécution de packages dans le journal des événements des applications. Ce paramètre limite le nombre d'entrées de journal des événements lorsque vous utilisez la fonctionnalité du collecteur de données de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Les événements qui ne sont pas enregistrés incluent l'ID d'événement 12288, « le Package a démarré », et l'ID d'événement 12289, « le Package a fini avec succès ». Pour enregistrer ces événements dans le journal des événements des applications, ouvrez le Registre pour y apporter des modifications. Dans le Registre, recherchez le nœud HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS et modifiez la valeur DWORD du paramètre LogPackageExecutionToEventLog en remplaçant 0 par 1.  
  
## <a name="understanding-the-integration-services-service"></a>Fonctionnement du service Integration Services  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installe le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est installé lorsque vous sélectionnez l'option **Integration Services** dans la page **Sélection de fonctionnalités** . Lorsque vous acceptez les paramètres par défaut de la page **Configuration du serveur** , le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est activé et son **Type de démarrage** est **Automatique**.  
  
 Vous ne pouvez installer qu'une seule instance du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur un ordinateur. Le service n'est pas spécifique à une instance particulière du moteur de base de données. Vous vous connectez au service en utilisant le nom de l'ordinateur sur lequel le service s'exécute.  
  
## <a name="installing-integration-services-on-64-bit-computers"></a>Installation d'Integration Services sur des ordinateurs 64 bits  
  
### <a name="integration-services-features-installed-on-64-bit-computers"></a>Fonctionnalités d'Integration Services installées sur des ordinateurs 64 bits  
 L'installation installe différentes fonctionnalités [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] selon les options d'installation que vous sélectionnez :  
  
-   Lorsque vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et que vous sélectionnez [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour l'installation, l'ensemble des outils et des fonctionnalités [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 64 bits sont installés.  
  
-   Si vous avez besoin de fonctionnalités disponibles au moment de la conception [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , vous devez également installer [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
-   Si vous avez besoin des versions 32 bits des outils et du runtime [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour exécuter certains packages en mode 32 bits, vous devez également installer [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Les fonctionnalités 64 bits sont installées dans le répertoire **Program Files** et les fonctionnalités 32 bits sont installées séparément dans le répertoire **Program Files (x86)** . (Ce comportement n'est pas spécifique à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] (environnement de développement 32 bits des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]) n'est pas pris en charge sur le système d'exploitation 64 bits [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] et n'est pas installé sur les serveurs [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)].  
  
  
