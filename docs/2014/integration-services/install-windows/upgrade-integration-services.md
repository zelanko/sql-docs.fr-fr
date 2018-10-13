---
title: Mettre à niveau Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, upgrading
- SSIS, upgrading
- SQL Server Integration Services, upgrading
- upgrading Integration Services
ms.assetid: 04f9863c-ba0b-47c5-af91-f2d41b078a23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b6abc8e9e025bc24b4f456b58e0e9625e66b4b71
ms.sourcegitcommit: 5d6e1c827752c3aa2d02c4c7653aefb2736fffc3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2018
ms.locfileid: "49072023"
---
# <a name="upgrade-integration-services"></a>Mettre à niveau Integration Services
  Si [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] ou [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] est installé sur votre ordinateur, vous pouvez effectuer une mise à niveau vers [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
 Lorsque vous mettez à niveau vers [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] sur un ordinateur sur lequel une de ces versions antérieures d' [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est installée, [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] est installé côte à côte avec une version antérieure.  
  
 Avec cette installation côte à côte, plusieurs versions de l'utilitaire dtexec sont installés. Pour être certain d’exécuter la version appropriée de l’utilitaire, à l’invite de commandes, exécutez l’utilitaire en entrant le chemin complet (\<lecteur>:\Program Files\Microsoft SQL Server\\<version\>\DTS\Binn). Pour plus d'informations dtexec, consultez [dtexec Utility](../packages/dtexec-utility.md).  
  
> [!NOTE]  
>  Dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], par défaut, lorsque vous installiez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , tous les utilisateurs du groupe Utilisateurs avaient accès au service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Lorsque vous installez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], les utilisateurs n'ont pas accès au service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Ce service est sécurisé par défaut. Une fois [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installé, l'administrateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit exécuter l'outil de configuration DCOM (Dcomcnfg.exe) pour accorder à des utilisateurs spécifiques l'accès au service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Pour plus d’informations, consultez [Grant Permissions to Integration Services Service](../grant-permissions-to-integration-services-service.md).  
  
## <a name="before-upgrading-integration-services"></a>Avant de procéder à la mise à niveau d'Integration Services  
 Nous vous avons recommandé d'exécuter le Conseiller de mise à niveau avant de procéder à la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Le Conseiller de mise à niveau signale des problèmes que vous pouvez rencontrer si vous effectuez une migration de packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] existants vers le nouveau format de package que [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilise. Pour plus d'informations, consultez [Use Upgrade Advisor to Prepare for Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
> [!NOTE]  
>  Prise en charge de la migration ou l’exécution de packages de Services DTS (Data Transformation) a été supprimé dans la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Les fonctionnalités DTS suivantes ne sont plus disponibles.  
>   
>  -   Runtime DTS ;  
> -   DTS API ;  
> -   Assistant Migration de package pour la migration de packages DTS vers la prochaine version de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
> -   Prise en charge de la maintenance des packages DTS dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
> -   Tâche d'exécution de package DTS 2000 ;  
> -   analyse du Conseiller de mise à niveau des packages DTS.  
>   
>  Pour plus d’informations sur les autres fonctionnalités supprimées, consultez [fonctionnalités Integration Services abandonnées dans SQL Server 2014](../discontinued-integration-services-functionality-in-sql-server-2014.md).  
  
## <a name="upgrading-integration-services"></a>mise à niveau d'Integration Services  
 Vous pouvez effectuer la mise à niveau au moyen de l'une des méthodes suivantes :  
  
-   Exécutez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] le programme d’installation et sélectionnez l’option **mise à niveau à partir de SQL Server 2005, SQL Server 2008 ou SQL Server 2008 R2**, ou **[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]**.  
  
-   Exécutez **setup.exe** à l’invite de commandes et spécifiez le `/ACTION=upgrade` option. Pour plus d’informations, consultez la section « Scripts d’Installation pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], « dans [installer SQL Server 2014 à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
 Vous ne pouvez pas utiliser la mise à niveau pour exécuter les actions suivantes :  
  
-   Reconfigurer une installation existante de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   Passer d'une version 32 bits à une version 64 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d'une version 64 bits à une version 32 bits.  
  
-   Passer d'une version localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à une autre version localisée.  
  
 Lors d’une mise à niveau, vous pouvez mettre à niveau à la fois [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et [!INCLUDE[ssDE](../../includes/ssde-md.md)], mais vous pouvez également choisir de mettre à niveau uniquement [!INCLUDE[ssDE](../../includes/ssde-md.md)]ou uniquement [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Si vous mettez à niveau uniquement le [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] ou [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] reste fonctionnel, mais vous n’avez pas les fonctionnalités de [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]. Si vous mettez uniquement à niveau [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] sera totalement fonctionnel, mais uniquement en mesure de stocker des packages dans le système de fichiers, à moins qu'une instance du [!INCLUDE[ssDECurrent](../../includes/ssdecurrent-md.md)] ne soit disponible sur un autre ordinateur.  
  
## <a name="upgrading-both-integration-services-and-the-database-engine-to-includesscurrentincludessscurrent-mdmd"></a>Mise à niveau d'Integration Services et du moteur de base de données vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Cette section décrit les conséquences liées à l'exécution d'une mise à niveau qui obéit aux critères suivants :  
  
-   Mise à niveau de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et d’une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   Installation de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et de l’instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)] sur le même ordinateur.  
  
### <a name="what-the-upgrade-process-does"></a>Ce que fait le processus de mise à niveau  
 Le processus de mise à niveau effectue les tâches suivantes :  
  
-   Installe les fichiers [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] , ainsi que le service et les outils ([!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] et [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]). Lorsque plusieurs instances de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] sont installées sur le même ordinateur, lorsque vous mettez à niveau à partir d'une instance quelconque vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], les fichiers, les services et les outils [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] sont installés.  
  
-   Met à niveau l’instance de la [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] à la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version.  
  
-   Déplace les données depuis le [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] ou [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] tables système pour la [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] tables système, comme suit :  
  
    -   Déplace les packages sans modification de la table système msdb.dbo.sysdtspackages90 vers la table système msdb.dbo.sysssispackages.  
  
        > [!NOTE]  
        >  Bien que les données soient déplacées vers une autre table système, la mise à niveau n'effectue pas la migration des packages vers le nouveau format.  
  
    -   Déplace les métadonnées de dossier de la table système msdb.sysdtsfolders90 vers la table système msdb.sysssisfolders.  
  
    -   Déplace les données du journal de la table système msdb.sysdtslog90 vers la table système msdb.sysssislog.  
  
-   Supprime les tables système msdb.sysdts\*90 et les procédures stockées utilisées pour y accéder après avoir déplacé les données vers les nouvelles tables msdb.sysssis\* . Toutefois, la mise à niveau remplace la table sysdtslog90 par une vue qui est également nommée sysdtslog90. Cette nouvelle vue sysdtslog90 présente la nouvelle table système msdb.sysssislog. Cela garantit que les rapports basés sur la table du journal continuent à s'exécuter sans interruption.  
  
-   Pour contrôler l'accès aux packages, crée trois nouveaux rôles de base de données fixes : db_ssisadmin, db_ssisltduser et db_ssisoperator. Les rôles [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de db_dtsadmin, db_dtsltduser et db_dtsoperator ne sont pas supprimés, mais deviennent membres des nouveaux rôles correspondants.  
  
-   Si le [!INCLUDE[ssIS](../../includes/ssis-md.md)] magasin de packages (autrement dit, l’emplacement de système de fichiers géré par le [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service) est l’emplacement par défaut sous **\SQL Server\90**, **\SQL Server\100**, ou **\SQL Server\110** ces packages sont déplacés vers le nouvel emplacement par défaut sous **server\120**.  
  
-   Met à jour le fichier de configuration du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de sorte qu’il pointe vers l’instance mise à niveau de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
### <a name="what-the-upgrade-process-does-not-do"></a>Ce que ne fait pas le processus de mise à niveau  
 Le processus de mise à niveau n'effectue pas les tâches suivantes :  
  
-   **Pas** supprimer le [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] ou [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] service.  
  
-   N'effectue pas la migration des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] existants vers le nouveau format utilisé par [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour les packages. Pour plus d’informations sur la migration de packages, consultez [Mettre à niveau des packages Integration Services](upgrade-integration-services-packages.md).  
  
-   Ne déplace pas de packages à partir d'emplacements du système de fichiers, autre que l'emplacement par défaut, qui ont été ajoutés au fichier de configuration du service. Si vous avez déjà modifié le fichier de configuration du service de manière à ajouter des dossiers de système de fichiers supplémentaires, les packages stockés dans ces dossiers ne seront pas déplacés à un nouvel endroit.  
  
-   Dans les étapes du travail de l’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui appellent directement l’utilitaire **dtexec** (dtexec.exe), ne met pas à jour le chemin du système de fichiers pour l’utilitaire **dtexec** . Vous devez modifier manuellement ces étapes du travail pour mettre à jour le chemin d’accès au système de fichiers en vue de spécifier l’emplacement [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour l’utilitaire **dtexec** .  
  
### <a name="what-you-can-do-after-upgrading"></a>Ce que vous pouvez faire après la mise à niveau  
 Une fois la mise à niveau terminée, vous pouvez accomplir les tâches suivantes :  
  
-   Exécuter les travaux de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui exécutent les packages.  
  
-   Utilisez [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour gérer les [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages qui sont stockés dans une instance de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Vous devez modifier le fichier de configuration du service pour ajouter l'instance de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] à la liste des emplacements gérés par le service.  
  
    > [!NOTE]  
    >  Les premières versions de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ne peuvent pas se connecter au service [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] .  
  
-   Identifier la version des packages dans la table système msdb.dbo.sysssispackages en vérifiant la valeur de la colonne packageformat. La table possède une colonne packageformat qui identifie la version de chaque package. La valeur 2 dans la colonne packageformat indique un package [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] et la valeur 3 un package [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]. Tant que vous n'effectuez pas la migration des packages vers le nouveau format, la valeur de la colonne packageformat ne change pas.  
  
-   Vous ne pouvez pas utiliser le [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] outils pour concevoir, exécuter ou gérer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages. Les outils [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] incluent les versions correspondantes de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], de l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et de l'utilitaire d'exécution de package (dtexecui.exe). Le processus de mise à niveau ne supprime pas le [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]outils. Toutefois, vous ne serez pas en mesure de faire appel à ces outils pour continuer à utiliser les packages [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] ou [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] sur un serveur qui a été mis à niveau.  
  
-   Par défaut, dans le cadre d'une installation mise à niveau, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est configuré de façon à journaliser les événements en rapport avec l'exécution de packages dans le journal d'événements de l'application. Ce paramètre peut générer trop d'entrées de journal d'événements lorsque vous utilisez la fonctionnalité collecteur de données de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Les événements enregistrés incluent l'ID d'événement 12288, « le Package a démarré », et l'ID d'événement 12289, « le Package a fini avec succès ». Pour arrêter l'enregistrement de ces deux événements dans le journal d'événements de l'application, ouvrez le Registre pour y apporter des modifications. Dans le Registre, recherchez le nœud HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS et modifiez la valeur DWORD du paramètre LogPackageExecutionToEventLog en remplaçant 1 par 0.  
  
## <a name="upgrading-only-the-database-engine-to-includesscurrentincludessscurrent-mdmd"></a>Mise à niveau du seul moteur de base de données vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Cette section décrit les conséquences liées à l'exécution d'une mise à niveau qui obéit aux critères suivants :  
  
-   Mise à niveau d’une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)]uniquement. Autrement dit, l’instance de la [!INCLUDE[ssDE](../../includes/ssde-md.md)] est maintenant une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], mais l’instance de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les outils clients proviennent de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
-   L’instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)] se trouve sur un ordinateur, tandis que [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les outils clients se trouvent sur un autre ordinateur.  
  
### <a name="what-you-can-do-after-upgrading"></a>Ce que vous pouvez faire après la mise à niveau  
 Les tables système qui stockent les packages dans l’instance mise à niveau de la [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne sont pas les mêmes que ceux utilisés dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]. Par conséquent, le [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] versions de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] et [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] ne peut pas découvrir les packages dans les tables système sur l’instance mise à niveau de la [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Comme ces packages ne peuvent pas être découverts, l'utilisation que vous pouvez en faire est limitée :  
  
-   Vous ne pouvez pas utiliser le [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] outils, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] et [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], sur d’autres ordinateurs pour charger ou gérer des packages à partir de l’instance mise à niveau de la [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
    > [!NOTE]  
    >  Bien que les packages dans l’instance mise à niveau de la [!INCLUDE[ssDE](../../includes/ssde-md.md)] n’ont pas encore été migrés vers le nouveau format de package, ils ne sont pas détectables par la [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] outils. Par conséquent, les packages ne peuvent pas être utilisés par les outils [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
-   Vous ne pouvez pas utiliser [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] ou [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] sur d’autres ordinateurs pour exécuter des packages qui sont stockés dans msdb sur l’instance mise à niveau de la [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   Vous ne pouvez pas utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] travaux de l’Agent sur [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ordinateurs pour exécuter [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] ou [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] packages qui sont stockés dans l’instance mise à niveau de la [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="external-resources"></a>Ressources externes  
 Entrée de blog [Making your Existing Custom SSIS Extensions and Applications Work in Denali](http://go.microsoft.com/fwlink/?LinkId=238157), sur blogs.msdn.com.  
  
  
