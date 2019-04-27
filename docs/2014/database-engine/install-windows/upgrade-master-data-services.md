---
title: Mettre à niveau Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9c3543f3-3eb9-455d-a9bf-f17e9506ad21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: da78f21c6346281dc23332f40e8e6f46ff07aa06
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62774653"
---
# <a name="upgrade-master-data-services"></a>Mettre à niveau Master Data Services
  Il existe quatre scénarios de mise à niveau vers Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2. Choisissez le scénario qui convient à votre situation.  
  
-   [Mise à niveau sans mise à niveau du moteur de base de données](#noengine)  
  
-   [Mise à niveau avec mise à niveau du moteur de base de données](#engine)  
  
-   [Effectuer une mise à niveau dans un scénario basé sur deux ordinateurs](#twocomputer)  
  
-   [Effectuer une mise à niveau par restauration d'une base de données à partir d'une sauvegarde](#restore)  
  
> [!IMPORTANT]
>  -   La mise à niveau de la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP1 vers la version CTP2 n'est pas prise en charge.  
> -   Enregistrez votre base de données avant d'effectuer toute mise à niveau.  
> -   La mise à niveau recrée les procédures stockées et met à niveau les tables utilisées par [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Les personnalisations appliquées à l'un ou l'autre de ces composants peuvent être perdues.  
> -   Les packages de déploiement de modèle peuvent être utilisés uniquement dans l'édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisée pour les créer. Vous ne pouvez pas déployer des packages de déploiement de modèle créés dans [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] / [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
> -   Vous pouvez continuer à utiliser la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 du complément Master Data Services pour Excel après la mise à niveau de Master Data Services et de Data Quality Services vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2. Toutefois, aucune version antérieure du complément Master Data Services pour Excel ne fonctionnera après la mise à niveau vers SQL Server 2014 CTP2. Vous pouvez télécharger la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 du complément Master Data Services pour Excel [ici](https://go.microsoft.com/fwlink/?LinkId=328664).  
  
##  <a name="noengine"></a> Mise à niveau sans mise à niveau du moteur de base de données  
 Ce scénario peut être considéré comme une installation côte à côte, car les deux [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] / [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sont installés en parallèle, sur le même ordinateur ou sur des ordinateurs distincts.  
  
 Dans ce scénario, vous continuez à utiliser [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] pour héberger la base de données MDS. Toutefois, vous devez mettre à niveau le schéma de la base de données MDS, puis créer une application Web [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour accéder à la base de données MDS. La base de données MDS ne sera plus accessible par l'application Web [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
 Si vous choisissez d’installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et une version antérieure de SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]/[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) sur le même ordinateur, vous pouvez le faire car les fichiers sont installés dans un emplacement différent.  
  
-   Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], par défaut, les fichiers sont installés à l’emplacement suivant : *lecteur*:\Program Files\Microsoft SQL Server\120\Master Data Services.  
  
-   Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], par défaut, les fichiers sont installés à l’emplacement suivant : *lecteur*:\Program Files\Microsoft SQL Server\110\Master Data Services.  
  
-   Dans [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], par défaut, les fichiers sont installés à l’emplacement suivant : *lecteur*:\Program Files\Microsoft SQL Server\Master Data Services.  
  
 Pour effectuer cette tâche, procédez comme suit.  
  
1.  Installez [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] et toutes les autres fonctionnalités que vous souhaitez.  
  
    1.  Ouvrez l'Assistant Installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    2.  Dans le volet gauche, cliquez sur **Installation**.  
  
    3.  Dans le volet droit, cliquez sur **Nouvelle installation autonome SQL Server ou ajout de fonctionnalités à une installation existante**.  
  
    4.  Dans la page **Sélection des fonctionnalités** , sélectionnez **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** , puis toutes les autres fonctionnalités à installer.  
  
    5.  Terminez l'Assistant.  
  
2.  Lorsque l'installation est terminée, mettez à niveau le schéma de base de données MDS.  
  
    1.  Ouvrez la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
        > [!IMPORTANT]  
        >  Pour mettre à niveau le schéma de la base de données MDS, vous devez ouvrir une session avec le compte Administrateur spécifié lors de la création de la base de données MDS. Dans la base de données MDS, dans mdm.tblUser, cet utilisateur à la valeur d' **ID** **1**. Pour plus d’informations sur la modification de cet utilisateur, consultez [modifier le compte d’administrateur système &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
    2.  Dans le volet gauche, cliquez sur **Configuration de la base de données**.  
  
    3.  Dans le volet droit, cliquez sur **sélectionner la base de données** et spécifiez les informations de votre [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] instance de base de données.  
  
    4.  Cliquez sur **Mettre à niveau la base de données** pour démarrer l' **Assistant Mise à niveau de base de données**. Pour plus d’informations, consultez [Assistant Mise à niveau de base de données &#40;Gestionnaire de configuration Master Data Services&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).  
  
3.  Lorsque la mise à niveau est terminée, créez une application Web [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    1.  Ouvrez la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
    2.  Dans le volet gauche, cliquez sur **Configuration Web**.  
  
    3.  Dans le volet droit, dans la liste **Site Web** , sélectionnez l'une des options suivantes :  
  
        -   **Site Web par défaut**, puis cliquez sur **Créer une application**.  
  
        -   **Créer un nouveau site**. Lorsque vous créez un site web, une application web est automatiquement créée.  
  
        > [!IMPORTANT]  
        >  Votre application Web MDS existante issue d'une version précédente de SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) est disponible à la sélection dans la version SQL Server 2014 du Gestionnaire de configuration Master Data Services. Vous ne devez pas sélectionner l'application Web existante, mais plutôt créer une application Web [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour MDS. Sinon, vous allez recevoir une erreur lorsque vous tenterez d'associer l'application Web à la base de données MDS mise à niveau, indiquant que la page demandée n'est pas accessible, car les données de configuration de la page sont erronées.  
        >   
        >  Si vous souhaitez utiliser le même nom (alias) pour l'application Web MDS que le nom de votre application Web existante ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]), vous devez d'abord supprimer l'application Web et le pool d'applications associé d'IIS, puis créer une application Web avec le même nom avec la version SQL Server 2014 du Gestionnaire de configuration Master Data Services. Pour plus d’informations sur la suppression d’une application web et de pools d’applications d’IIS, consultez [Supprimer une application (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) et [Supprimer un pool d’applications (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).  
  
4.  Associez maintenant la nouvelle application Web à la base de données MDS mise à niveau.  
  
    1.  Sous la section **Associer l'application à une base de données** , cliquez sur **Sélectionner**.  
  
    2.  Sélectionnez la base de données MDS.  
  
    3.  Cliquez sur **Appliquer**.  
  
##  <a name="engine"></a> Mise à niveau avec mise à niveau du moteur de base de données  
 Dans ce scénario, vous allez mettre à niveau le moteur de base de données et l'application [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou SQL Server 2012 vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Pour effectuer cette tâche, procédez comme suit.  
  
1.  **Pour [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] uniquement**: Ouvrez **le panneau de configuration** > **programmes et fonctionnalités** désinstaller Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
2.  Mettez à niveau le moteur de base de données vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    1.  Ouvrez l'Assistant Installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    2.  Dans le volet gauche, cliquez sur **Installation**.  
  
    3.  Dans le volet droit, cliquez sur **mise à niveau à partir de SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 ou SQL Server 2012**.  
  
    4.  Terminez l'Assistant.  
  
3.  **Pour [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] uniquement**: Lorsque la mise à niveau est terminée, ajoutez le **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** fonctionnalité.  
  
    1.  Ouvrez l'Assistant Installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    2.  Dans le volet gauche, cliquez sur **Installation**.  
  
    3.  Dans le volet droit, cliquez sur **Nouvelle installation autonome SQL Server ou ajout de fonctionnalités à une installation existante**.  
  
    4.  Sur le **Type d’Installation** page de l’Assistant, sélectionnez le **ajouter des fonctionnalités à une instance existante** option, puis choisissez l’instance où la base de données MDS est installé.  
  
    5.  Sur le **sélection des fonctionnalités** page sous **fonctionnalités partagées**, sélectionnez **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]**.  
  
    6.  Terminez l'Assistant.  
  
4.  Mettez à niveau le schéma de la base de données MDS.  
  
    1.  Ouvrez la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
        > [!IMPORTANT]  
        >  Pour mettre à niveau le schéma de la base de données MDS, vous devez ouvrir une session avec le compte Administrateur spécifié lors de la création de la base de données MDS. Dans la base de données MDS, dans mdm.tblUser, cet utilisateur à la valeur d' **ID** **1**. Pour plus d’informations sur la modification de cet utilisateur, consultez [modifier le compte d’administrateur système &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
    2.  Dans le volet gauche, cliquez sur **Configuration de la base de données**.  
  
    3.  Dans le volet droit, cliquez sur **sélectionner la base de données** et spécifiez les informations de votre instance de base de données.  
  
    4.  Cliquez sur **Mettre à niveau la base de données** pour démarrer l' **Assistant Mise à niveau de base de données**. Pour plus d’informations, consultez [Assistant Mise à niveau de base de données &#40;Gestionnaire de configuration Master Data Services&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).  
  
    5.  Cliquez sur **Appliquer**.  
  
5.  Lorsque la mise à niveau est terminée, créez une application Web [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    1.  Ouvrez la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
    2.  Dans le volet gauche, cliquez sur **Configuration Web**.  
  
    3.  Dans le volet droit, dans la liste **Site Web** , sélectionnez l'une des options suivantes :  
  
        -   **Site Web par défaut**, puis cliquez sur **Créer une application**.  
  
        -   **Créer un nouveau site**. Lorsque vous créez un site web, une application web est automatiquement créée.  
  
        > [!IMPORTANT]  
        >  Votre application Web MDS existante issue d'une version précédente de SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) est disponible à la sélection dans la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du Gestionnaire de configuration Master Data Services. Vous ne devez pas sélectionner l'application Web existante, mais plutôt créer une application Web [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour MDS. Sinon, vous allez recevoir une erreur lorsque vous tenterez d'associer l'application Web à la base de données MDS mise à niveau, indiquant que la page demandée n'est pas accessible, car les données de configuration de la page sont erronées.  
        >   
        >  Si vous souhaitez utiliser le même nom (alias) pour l'application Web MDS que le nom de votre application Web existante ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]), vous devez d'abord supprimer l'application Web et le pool d'applications associé d'IIS, puis créer une application Web avec le même nom avec la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du Gestionnaire de configuration Master Data Services. Pour plus d’informations sur la suppression d’une application web et de pools d’applications d’IIS, consultez [Supprimer une application (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) et [Supprimer un pool d’applications (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).  
  
6.  Associez maintenant la nouvelle application Web à la base de données MDS mise à niveau.  
  
    1.  Sous la section **Associer l'application à une base de données** , cliquez sur **Sélectionner**.  
  
    2.  Sélectionnez la base de données MDS.  
  
    3.  Cliquez sur **Appliquer**.  
  
##  <a name="twocomputer"></a> Effectuer une mise à niveau dans un scénario basé sur deux ordinateurs  
 Ce scénario implique la mise à niveau d'un système dans lequel SQL Server est installé sur deux ordinateurs : l'un étant doté de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et l'autre étant doté de SQL Server 2008 R2 ou SQL Server 2012.  
  
 Si [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] est installé, continuez à utiliser [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] respectivement pour héberger votre base de données MDS sur un seul ordinateur. Toutefois, vous devez mettre à niveau le schéma de la base de données MDS, puis utiliser l'application Web [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour accéder à la base de données MDS. La base de données MDS ne sera plus accessible par l'application Web [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
-   Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], par défaut, les fichiers sont installés à l’emplacement suivant : *lecteur*:\Program Files\Microsoft SQL Server\120\Master Data Services.  
  
-   Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], par défaut, les fichiers sont installés à l’emplacement suivant : *lecteur*:\Program Files\Microsoft SQL Server\110\Master Data Services.  
  
-   Dans [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], par défaut, les fichiers sont installés à l’emplacement suivant : *lecteur*:\Program Files\Microsoft SQL Server\Master Data Services.  
  
 Pour effectuer cette tâche, procédez comme suit.  
  
1.  Installez [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] et toutes les autres fonctionnalités que vous souhaitez.  
  
    1.  Ouvrez l'Assistant Installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    2.  Dans le volet gauche, cliquez sur **Installation**.  
  
    3.  Dans le volet droit, cliquez sur **Nouvelle installation autonome SQL Server ou ajout de fonctionnalités à une installation existante**.  
  
    4.  Dans la page **Sélection des fonctionnalités** , sélectionnez **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** , puis toutes les autres fonctionnalités à installer.  
  
    5.  Terminez l'Assistant.  
  
2.  Lorsque l'installation est terminée, mettez à niveau le schéma de base de données MDS.  
  
    1.  Ouvrez la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
        > [!IMPORTANT]  
        >  Pour mettre à niveau le schéma de la base de données MDS, vous devez ouvrir une session avec le compte Administrateur spécifié lors de la création de la base de données MDS. Dans la base de données MDS, dans mdm.tblUser, cet utilisateur à la valeur d' **ID** **1**. Pour plus d’informations sur la modification de cet utilisateur, consultez [modifier le compte d’administrateur système &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
    2.  Dans le volet gauche, cliquez sur **Configuration de la base de données**.  
  
    3.  Dans le volet droit, cliquez sur **sélectionner la base de données** et spécifiez les informations de votre [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] de la base de données d’instance sur un autre ordinateur, si [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] est installé sur un autre ordinateur.  
  
    4.  Cliquez sur **Mettre à niveau la base de données** pour démarrer l' **Assistant Mise à niveau de base de données**. Pour plus d’informations, consultez [Assistant Mise à niveau de base de données &#40;Gestionnaire de configuration Master Data Services&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).  
  
3.  Lorsque la mise à niveau est terminée, créez une application Web SQL Server 2014.  
  
    1.  Ouvrez la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
    2.  Dans le volet gauche, cliquez sur **Configuration Web**.  
  
    3.  Dans le volet droit, dans la liste **Site Web** , sélectionnez l'une des options suivantes :  
  
        -   **Site Web par défaut**, puis cliquez sur **Créer une application**.  
  
        -   **Créer un nouveau site**. Lorsque vous créez un site web, une application web est automatiquement créée.  
  
        > [!IMPORTANT]  
        >  Votre application Web MDS existante issue d'une version précédente de SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) est disponible à la sélection dans la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du Gestionnaire de configuration Master Data Services. Vous ne devez pas sélectionner l'application Web existante, mais plutôt créer une application Web [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour MDS. Sinon, vous allez recevoir une erreur lorsque vous tenterez d'associer l'application Web à la base de données MDS mise à niveau, indiquant que la page demandée n'est pas accessible, car les données de configuration de la page sont erronées.  
        >   
        >  Si vous souhaitez utiliser le même nom (alias) pour l'application Web MDS que le nom de votre application Web existante ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]), vous devez d'abord supprimer l'application Web et le pool d'applications associé d'IIS, puis créer une application Web avec le même nom avec la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du Gestionnaire de configuration Master Data Services. Pour plus d’informations sur la suppression d’une application web et de pools d’applications d’IIS, consultez [Supprimer une application (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) et [Supprimer un pool d’applications (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).  
  
4.  Associez maintenant l'application Web à la base de données MDS mise à niveau.  
  
    1.  Sous la section **Associer l'application à une base de données** , cliquez sur **Sélectionner**.  
  
    2.  Sélectionnez la base de données MDS.  
  
    3.  Cliquez sur **Appliquer**.  
  
##  <a name="restore"></a> Effectuer une mise à niveau par restauration d'une base de données à partir d'une sauvegarde  
 Dans ce scénario, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est installé avec SQL Server 2008 R2 ou SQL Server 2012 sur le même ordinateur ou sur deux ordinateurs différents. De même, une base de données a été sauvegardée sur une version antérieure à la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2, avant la mise à niveau, et la base de données doit être restaurée à partir de cette sauvegarde.  
  
-   Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], par défaut, les fichiers sont installés à l’emplacement suivant : *lecteur*:\Program Files\Microsoft SQL Server\120\Master Data Services.  
  
-   Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], par défaut, les fichiers sont installés à l’emplacement suivant : *lecteur*:\Program Files\Microsoft SQL Server\110\Master Data Services.  
  
-   Dans [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], par défaut, les fichiers sont installés à l’emplacement suivant : *lecteur*:\Program Files\Microsoft SQL Server\Master Data Services.  
  
 Pour effectuer cette tâche, procédez comme suit.  
  
1.  Installez [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] et toutes les autres fonctionnalités que vous souhaitez.  
  
    1.  Ouvrez l'Assistant Installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    2.  Dans le volet gauche, cliquez sur **Installation**.  
  
    3.  Dans le volet droit, cliquez sur **Nouvelle installation autonome SQL Server ou ajout de fonctionnalités à une installation existante**.  
  
    4.  Dans la page **Sélection des fonctionnalités** , sélectionnez **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** , puis toutes les autres fonctionnalités à installer.  
  
    5.  Terminez l'Assistant.  
  
2.  Restaurez la base de données qui a été sauvegardée.  
  
3.  Lorsque l'installation est terminée, mettez à niveau le schéma de base de données MDS.  
  
    1.  Ouvrez la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
        > [!IMPORTANT]  
        >  Pour mettre à niveau le schéma de la base de données MDS, vous devez ouvrir une session avec le compte Administrateur spécifié lors de la création de la base de données MDS. Dans la base de données MDS, dans mdm.tblUser, cet utilisateur à la valeur d' **ID** **1**. Pour plus d’informations sur la modification de cet utilisateur, consultez [modifier le compte d’administrateur système &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
    2.  Dans le volet gauche, cliquez sur **Configuration de la base de données**.  
  
    3.  Dans le volet droit, cliquez sur **sélectionner la base de données** et spécifiez les informations de votre [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] instance de base de données.  
  
    4.  Cliquez sur **Mettre à niveau la base de données** pour démarrer l' **Assistant Mise à niveau de base de données**. Pour plus d’informations, consultez [Assistant Mise à niveau de base de données &#40;Gestionnaire de configuration Master Data Services&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).  
  
4.  Lorsque la mise à niveau est terminée, créez une application Web [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    1.  Ouvrez la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
    2.  Dans le volet gauche, cliquez sur **Configuration Web**.  
  
    3.  Dans le volet droit, dans la liste **Site Web** , sélectionnez l'une des options suivantes :  
  
        -   **Site Web par défaut**, puis cliquez sur **Créer une application**.  
  
        -   **Créer un nouveau site**. Lorsque vous créez un site web, une application web est automatiquement créée.  
  
        > [!IMPORTANT]  
        >  Votre application Web MDS existante issue d'une version précédente de SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) est disponible à la sélection dans la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du Gestionnaire de configuration Master Data Services. Vous ne devez pas sélectionner l'application Web existante, mais plutôt créer une application Web [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour MDS. Sinon, vous allez recevoir une erreur lorsque vous tenterez d'associer l'application Web à la base de données MDS mise à niveau, indiquant que la page demandée n'est pas accessible, car les données de configuration de la page sont erronées.  
        >   
        >  Si vous souhaitez utiliser le même nom (alias) pour l'application Web MDS que le nom de votre application Web existante ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]), vous devez d'abord supprimer l'application Web et le pool d'applications associé d'IIS, puis créer une application Web avec le même nom avec la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du Gestionnaire de configuration Master Data Services. Pour plus d’informations sur la suppression d’une application web et de pools d’applications d’IIS, consultez [Supprimer une application (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) et [Supprimer un pool d’applications (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).  
  
5.  Associez maintenant la nouvelle application Web à la base de données MDS mise à niveau.  
  
    1.  Sous la section **Associer l'application à une base de données** , cliquez sur **Sélectionner**.  
  
    2.  Sélectionnez la base de données MDS.  
  
    3.  Cliquez sur **Appliquer**.  
  
## <a name="troubleshooting"></a>Résolution des problèmes  
 **Problème :** Lorsque vous ouvrez le [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] application web, un message d’erreur « version du client n’est pas compatible avec la version de base de données » s’affiche.  
  
 **Solution :** Ce problème se produit lorsqu’un [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] application web Master Data Manager tente d’accéder à une base de données qui a été mis à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Master Data Services. Vous devez utiliser une application Web [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à la place.  
  
 Ce problème peut également se produire si vous n'avez pas arrêté puis redémarré le **pool d'applications MDS** dans IIS lors de la mise à niveau du schéma de la base de données MDS. Redémarrez le **pool d'applications MDS** pour corriger le problème.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
