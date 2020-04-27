---
title: Ajouter un serveur de rapports supplémentaire à un pool (montée en puissance SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c1a6b683-15cf-44ae-ac60-ceee63a60aaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b90bb5624e5b5cdbf3f1542ad0bef0d2765da248
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108964"
---
# <a name="add-an-additional-report-server-to-a-farm-ssrs-scale-out"></a>Ajouter un serveur de rapports supplémentaire à une batterie (montée en puissance SSRS)
  L'ajout d'un second serveur de rapports en mode SharePoint, ou plus, à votre batterie de serveurs SharePoint peut améliorer les performances et le temps de réponse du traitement du serveur de rapports. Si vous avez trouvé que les performances ralentissaient alors que vous ajoutiez des utilisateurs, des rapports et autres applications au serveur de rapports, l'ajout de serveurs de rapports peut améliorer les performances. Il est également recommandé d'ajouter un second serveur de rapports pour augmenter la disponibilité des serveurs de rapports lorsqu'il existe des problèmes liés au matériel ou lorsque vous effectuez la maintenance générale sur des serveurs individuels de votre environnement. À compter de la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , les étapes de la montée en puissance parallèle d'un environnement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint suivent le déploiement standard d'une batterie de serveurs SharePoint et exploitent les fonctionnalités d'équilibrage de charge SharePoint.  
  
> [!IMPORTANT]  
>  Le déploiement avec montée en puissance parallèle de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n'est pas pris en charge par toutes les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] la section des [fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
> [!TIP]  
>  À compter de la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], vous n'utilisez pas le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour ajouter des serveurs et effectuer un scale-out des serveurs de rapports. Les produits SharePoint gèrent le déploiement avec montée en puissance parallèle de Reporting Services sous forme de serveurs SharePoint avec l'ajout du service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à la batterie de serveurs.  
  
 Pour plus d’informations sur le déploiement de serveurs de rapports en mode natif avec montée en puissance parallèle, consultez [Configurer un déploiement par montée en puissance parallèle de serveurs de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).  
  
-   [Équilibrage de charge](#bkmk_loadbalancing)  
  
-   [Conditions préalables](#bkmk_prerequisites)  
  
-   [Étapes](#bkmk_steps)  
  
-   [Configuration supplémentaire](#bkmk_additional)  
  
##  <a name="load-balancing"></a><a name="bkmk_loadbalancing"></a>Équilibrage de charge  
 L'équilibrage de la charge des applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sera géré automatiquement par SharePoint à moins que votre environnement n'ait une solution d'équilibrage de charge tierce ou personnalisée. Le comportement d'équilibrage de la charge SharePoint par défaut fait que chaque application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sera équilibrée à travers tous les serveurs d'applications sur lesquels vous avez démarré le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour vérifier si le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est installé et démarré, cliquez sur **Gérer les services sur le serveur** dans l'Administration centrale de SharePoint.  
  
##  <a name="prerequisites"></a><a name="bkmk_prerequisites"></a> Conditions préalables  
  
-   Vous devez être administrateur local pour exécuter le programme d'installation de SQL Server.  
  
-   L'ordinateur doit être attaché à un domaine.  
  
-   Vous devez connaître le nom du serveur de base de données existant qui héberge la configuration et les bases de données de contenu SharePoint.  
  
-   Le serveur de base de données doit être configuré pour autoriser les connexions de base de données distantes.  S'il ne l'est pas, vous ne pourrez pas joindre le nouveau serveur à la batterie car il ne pourra pas établir de connexion aux bases de données de configuration SharePoint.  
  
-   Le nouveau serveur devra avoir la même version de SharePoint installée que celle exécutée par les serveurs de batterie actuels. Par exemple, si SharePoint 2010 Service Pack 1 (SP1) est déjà installé sur la batterie, vous devrez installer également le SP1 sur le nouveau serveur pour qu'il puisse rejoindre la batterie.  
  
-   Consultez les rubriques supplémentaires suivantes pour comprendre les exigences du système et des versions :  
  
     [Instructions d'utilisation des fonctionnalités BI de SQL Server dans une batterie de serveurs SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
##  <a name="steps"></a><a name="bkmk_steps"></a>Étapes  
 Les étapes de cette rubrique partent du principe qu'un administrateur de batterie de serveurs SharePoint installe et configure le serveur. Le diagramme illustre un environnement à trois niveaux classique et les éléments numérotés sont décrits dans la liste suivante :  
  
-   (1) Plusieurs serveurs Web frontaux. Les serveurs Web frontaux ont besoin du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour SharePoint 2010.  
  
-   (2) Un seul serveur d'applications exécutant [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et des sites Web, par exemple Administration centrale. Les étapes suivantes ajoutent un deuxième serveur d'applications à cette couche.  
  
-   (3) Deux serveurs de base de données SQL Server.  
  
-   (4) Représente une solution d'équilibrage de la charge réseau matérielle ou logicielle  
  
 ![Ajout d'un serveur d'applications Reporting Services](../../../2014/sql-server/install/media/rs-sharepointscale.gif "Ajout d'un serveur d'applications Reporting Services")  
  
 Les étapes suivantes impliquent qu'un administrateur procède à l'installation et à la configuration du serveur. Le serveur sera installé en tant que nouveau serveur d'applications dans la batterie et ne sera pas utilisé comme serveur Web frontal.  
  
|Étape|Description et lien|  
|----------|--------------------------|  
|Exécutez l'Outil de préparation des produits SharePoint 2010.|Vous devez disposer du support d'installation pour SharePoint 2010. L’outil de préparation est **PrerequisiteInstaller. exe** sur le support d’installation.|  
|Installez un produit SharePoint 2010.|1) sélectionnez le type d’installation de la **batterie de serveurs** .<br /><br /> 2) sélectionnez **terminé** pour le type de serveur.<br /><br /> 3) Lorsque l’installation est terminée, n’exécutez pas l’Assistant Configuration des produits SharePoint si SharePoint 2010 SP1 est installé sur votre batterie de serveurs SharePoint existante. Vous devez installer SharePoint SP1 avant d'exécuter l'Assistant Configuration des produits SharePoint.|  
|Installer SharePoint Server 2010 SP1|Si SharePoint 2010 SP1 est installé sur votre batterie de serveurs SharePoint existante, téléchargez et installez SharePoint[https://support.microsoft.com/kb/2460045](https://go.microsoft.com/fwlink/p/?linkID=219697)2010 SP1 à partir de :.<br /><br /> Pour plus d'informations sur SharePoint 2010 SP1, consultez [Problèmes connus lors de l'installation d'Office 2010 SP1 et de SharePoint 2010 SP1](https://support.microsoft.com/kb/2532126):|  
|Exécutez l'Assistant Configuration des produits SharePoint pour ajouter le serveur à la batterie.|1) dans le groupe de programmes **produits Microsoft sharepoint 2010** , cliquez sur **Assistant Configuration des produits Microsoft SharePoint 2010**.<br /><br /> 2) dans la page **se connecter à une batterie de serveurs** , sélectionnez **se connecter à une batterie** de serveurs existante, puis cliquez sur **suivant**.<br /><br /> 3) dans la page **spécifier les paramètres de la base de données de configuration** , tapez le nom du serveur de base de données utilisé pour la batterie de serveurs existante et le nom de la base de données de configuration. Cliquez sur **Suivant**.<br />** \* Important \* \* ** Si un message d’erreur semblable au suivant s’affiche et que vous avez vérifié que vous disposez des autorisations, vérifiez les Protocoles activés pour la configuration réseau SQL Server dans **SQL Server Configuration Manager**: «échec de la connexion au serveur de base de données. Assurez-vous que la base de données existe, qu’il s’agit d’un serveur SQL Server et que vous disposez des autorisations appropriées pour accéder au serveur.»<br />** \* Important \* \* ** Si vous voyez l' **État du produit et du correctif**de la batterie de serveurs de pages, vous devez passer en revue les informations de la page et mettre à jour le serveur avec les fichiers nécessaires pour pouvoir continuer à joindre le serveur à la batterie de serveurs.<br /><br /> 4) dans la page **spécifier les paramètres de sécurité** de la batterie, tapez le mot de passe de votre batterie de serveurs, puis cliquez sur **suivant**. Cliquez sur **Suivant** dans la page de confirmation pour exécuter l'Assistant.<br /><br /> 5) cliquez sur **suivant** pour exécuter l' **Assistant Configuration de batterie de serveurs**.|  
|Vérifiez que le serveur a été ajouté à la batterie de serveurs SharePoint.|1) Dans l’Administration centrale de SharePoint, cliquez sur **Gérer les serveurs de cette batterie** dans le groupe **Paramètres système** .<br /><br /> 2) Vérifiez que le nouveau serveur est ajouté et que l'état est correct.<br /><br /> 3) Notez que le service **SQL Server Reporting Services** service n’est pas en cours d’exécution. Le service sera installé à l'étape suivante.<br /><br /> 4) pour supprimer ce serveur du rôle WFE, cliquez sur **gérer les services sur le serveur** et arrêtez l' **application Web service Microsoft SharePoint Foundation**.|  
|Installez et configurez le mode SharePoint de Reporting Services.|Exécutez l'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Pour plus d’informations sur l’installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] du mode SharePoint, consultez [installer Reporting Services mode sharepoint pour SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) si le serveur ne sera utilisé qu’en tant que serveur d’applications et que le serveur ne sera pas utilisé comme WFE, vous n’avez pas besoin de sélectionner **Reporting Services complément pour les produits SharePoint** sur :<br /><br /> la page **rôle d’installation** , sélectionnez **installation de fonctionnalités SQL Server**<br /><br /> la page **sélection de fonctionnalités** , sélectionnez **Reporting Services-SharePoint**<br /><br /> OU<br /><br /> la page **configuration de Reporting Services** Vérifiez que l’option **installer uniquement** est sélectionnée pour **Reporting Services mode SharePoint**.|  
|Vérifiez que Reporting Services est opérationnel.|1) Dans l’Administration centrale de SharePoint, cliquez sur **Gérer les serveurs de cette batterie** dans le groupe **Paramètres système** .<br /><br /> 2) Vérifiez le service **SQL Server Reporting Services**.<br /><br /> Pour plus d’informations, consultez [vérifier une installation de Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)|  
  
##  <a name="additional-configuration"></a><a name="bkmk_additional"></a>Configuration supplémentaire  
 Vous pouvez optimiser des serveurs [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] individuels dans un déploiement avec montée en puissance parallèle afin d'effectuer un traitement en arrière-plan uniquement, de sorte que ces serveurs ne soient pas en concurrence en matière d'utilisation des ressources pour l'exécution de rapports interactifs. Le traitement en arrière-plan comprend les planifications, les abonnements et les alertes de données.  
  
 Pour modifier le comportement des serveurs de rapports individuels, affectez ** \<à IsWebServiceEnable>** la valeur false dans le fichier de configuration **RSreportServer. config** .  
  
 Par défaut, les serveurs de rapports sont configurés avec \<IsWebServiceEnable> défini à TRUE. Lorsque tous les serveurs sont configurés avec la valeur TRUE, les charges de traitement interactif et de traitement en arrière-plan sont équilibrées sur tous les nœuds de la batterie de serveurs.  
  
 Si vous configurez tous les serveurs de rapports avec \<IsWebServiceEnable> défini à False, un message d’erreur semblable à ce qui suit s’affiche quand vous essayez d’utiliser les fonctionnalités [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
 Le service Web Reporting Services n'est pas activé. Configurez au moins une instance du service Reporting Services SharePoint pour \<que IsWebServiceEnable> défini sur true. Pour plus d’informations, consultez [modifier un fichier de Configuration Reporting Services &#40;RSReportServer. config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des serveurs Web ou d’applications aux batteries de serveurs dans SharePoint 2013](https://technet.microsoft.com/library/cc261752.aspx)   
 [Configurer les services (SharePoint Server 2010)](https://technet.microsoft.com/library/ee794878.aspx)  
  
  
