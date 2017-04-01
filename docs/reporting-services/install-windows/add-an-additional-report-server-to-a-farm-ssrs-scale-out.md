---
title: "Ajouter un serveur de rapports suppl&#233;mentaire &#224; une batterie (mont&#233;e en puissance SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "06/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1a6b683-15cf-44ae-ac60-ceee63a60aaf
caps.latest.revision: 12
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 12
---
# Ajouter un serveur de rapports suppl&#233;mentaire &#224; une batterie (mont&#233;e en puissance SSRS)
  L'ajout d'un second serveur de rapports en mode SharePoint, ou plus, à votre batterie de serveurs SharePoint peut améliorer les performances et le temps de réponse du traitement du serveur de rapports. Si vous avez trouvé que les performances ralentissaient alors que vous ajoutiez des utilisateurs, des rapports et autres applications au serveur de rapports, l'ajout de serveurs de rapports peut améliorer les performances. Il est également recommandé d'ajouter un second serveur de rapports pour augmenter la disponibilité des serveurs de rapports lorsqu'il existe des problèmes liés au matériel ou lorsque vous effectuez la maintenance générale sur des serveurs individuels de votre environnement. À compter de la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], les étapes de la montée en puissance parallèle d'un environnement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint suivent le déploiement standard d'une batterie de serveurs SharePoint et exploitent les fonctionnalités d'équilibrage de charge SharePoint.  
  
> [!IMPORTANT]  
>  Le déploiement avec montée en puissance parallèle de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n'est pas pris en charge par toutes les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez la section [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de l’article [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
> [!TIP]  
>  À compter de la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], vous n'utilisez pas le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour ajouter des serveurs et déployer des serveurs de rapports avec montée en puissance parallèle. Les produits SharePoint gèrent le déploiement avec montée en puissance parallèle de Reporting Services sous forme de serveurs SharePoint avec l'ajout du service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à la batterie de serveurs.  
  
 Pour plus d’informations sur le déploiement de serveurs de rapports en mode natif avec montée en puissance parallèle, consultez [Configurer un déploiement par montée en puissance parallèle de serveurs de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure a native mode report server scale-out deployment.md).  
  
##  <a name="bkmk_loadbalancing"></a> Équilibrage de charge  
 L'équilibrage de la charge des applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sera géré automatiquement par SharePoint à moins que votre environnement n'ait une solution d'équilibrage de charge tierce ou personnalisée. Le comportement d'équilibrage de la charge SharePoint par défaut fait que chaque application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sera équilibrée à travers tous les serveurs d'applications sur lesquels vous avez démarré le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Pour vérifier si le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est installé et démarré, cliquez sur **Gérer les services sur le serveur** dans l'Administration centrale de SharePoint.  
  
##  <a name="bkmk_prerequisites"></a> Conditions préalables  
  
-   Vous devez être administrateur local pour exécuter le programme d'installation de SQL Server.  
  
-   L'ordinateur doit être attaché à un domaine.  
  
-   Vous devez connaître le nom du serveur de base de données existant qui héberge la configuration et les bases de données de contenu SharePoint.  
  
-   Le serveur de base de données doit être configuré pour autoriser les connexions de base de données distantes.  S'il ne l'est pas, vous ne pourrez pas joindre le nouveau serveur à la batterie car il ne pourra pas établir de connexion aux bases de données de configuration SharePoint.  
  
-   Le nouveau serveur devra avoir la même version de SharePoint installée que celle exécutée par les serveurs de batterie actuels. Par exemple, si SharePoint 2013 Service Pack 1 (SP1) est déjà installé sur la batterie de serveurs, vous devrez installer aussi le SP1 sur le nouveau serveur pour qu’il puisse rejoindre la batterie.  
  
##  <a name="bkmk_steps"></a> Étapes  
 Les étapes de cette rubrique partent du principe qu'un administrateur de batterie de serveurs SharePoint installe et configure le serveur. Le diagramme illustre un environnement à trois niveaux classique et les éléments numérotés sont décrits dans la liste suivante :  
  
-   (1) Plusieurs serveurs Web frontaux. Les serveurs Web frontaux ont besoin du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour SharePoint 2016.  
  
-   (2) Un seul serveur d'applications exécutant [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et des sites Web, par exemple Administration centrale. Les étapes suivantes ajoutent un deuxième serveur d'applications à cette couche.  
  
-   (3) Deux serveurs de base de données SQL Server.  
  
-   (4) Représente une solution d'équilibrage de la charge réseau matérielle ou logicielle  
  
 ![Adding a Reporting Services application server](../../reporting-services/install-windows/media/rs-sharepointscale.gif "Adding a Reporting Services application server")  
  
 Les étapes suivantes impliquent qu'un administrateur procède à l'installation et à la configuration du serveur. Le serveur sera installé en tant que nouveau serveur d'applications dans la batterie et ne sera pas utilisé comme serveur Web frontal.  
  
|Étape|Description et lien|  
|----------|--------------------------|  
|Ajoutez un serveur SharePoint à une batterie de serveurs.|Vous devez installer SharePoint pour déployer une autre application Reporting Services.<br/><br/>Pour SharePoint 2013, consultez [Ajouter des serveurs Web ou d’applications aux batteries de serveurs dans SharePoint 2013](https://technet.microsoft.com/library/cc261752(v=office.15).aspx).<br/><br/>Pour SharePoint 2016, consultez [Ajouter un serveur SharePoint à une batterie de serveurs dans SharePoint Server 2016](https://technet.microsoft.com/library/cc261752(v=office.16).aspx).|  
|Installez et configurez le mode SharePoint de Reporting Services.|Exécutez l'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour plus d’informations sur l’installation du mode SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [Installer le premier serveur de rapports en mode SharePoint](http://msdn.microsoft.com/fr-fr/b29d0f45-0068-4c84-bd7e-5b8a9cd1b538).<br /><br /> Si le serveur ne doit être utilisé qu’en tant que serveur d’applications et non en tant que serveur Web frontal, vous n’avez pas besoin de sélectionner **Complément Reporting Services pour les produits SharePoint**.<br /><br /> 1) Dans la page **Rôle d’installation**, sélectionnez **Installation de fonctionnalités SQL Server**.<br /><br /> 2) Dans la page **Sélection des fonctionnalités**, sélectionnez **Reporting Services - SharePoint**.<br /><br /> 3) Dans la page **Configuration de Reporting Services**, vérifiez que l’option **Installer uniquement** est sélectionnée pour **Mode SharePoint de Reporting Services**.|  
|Vérifiez que Reporting Services est opérationnel.|1) Dans l’Administration centrale de SharePoint, cliquez sur **Gérer les serveurs de cette batterie** dans le groupe **Paramètres système**.<br /><br /> 2) Vérifiez le service **SQL Server Reporting Services**.<br /><br />Pour plus d'informations, consultez [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)|  
  
##  <a name="bkmk_additional"></a> Configuration supplémentaire  
 Vous pouvez optimiser des serveurs [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] individuels dans un déploiement avec montée en puissance parallèle afin d'effectuer un traitement en arrière-plan uniquement, de sorte que ces serveurs ne soient pas en concurrence en matière d'utilisation des ressources pour l'exécution de rapports interactifs. Le traitement en arrière-plan comprend les planifications, les abonnements et les alertes de données.  
  
 Pour modifier le comportement de serveurs de rapports individuels, attribuez à **<IsWebServiceEnable>\>** la valeur false dans le fichier de configuration **RSreportServer.config**.  
  
 Par défaut, les serveurs de rapports sont configurés avec \<IsWebServiceEnable> défini à TRUE. Lorsque tous les serveurs sont configurés avec la valeur TRUE, les charges de traitement interactif et de traitement en arrière-plan sont équilibrées sur tous les nœuds de la batterie de serveurs.  
  
 Si vous configurez tous les serveurs de rapports avec \<IsWebServiceEnable> défini à False, vous voyez s’afficher un message d’erreur semblable à ce qui suit quand vous essayez d’utiliser les fonctionnalités [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
      The Reporting Services Web Service is not enabled. Configure at least one instance of the Reporting Services SharePoint Service to have <IsWebServiceEnable> set to true. 
 
 Pour plus d’informations, consultez [Modifier un fichier de configuration &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
## Voir aussi  
[Ajouter un serveur SharePoint à une batterie de serveurs dans SharePoint Server 2016](https://technet.microsoft.com/library/cc261752(v=office.16).aspx)  
[Ajouter des serveurs Web ou d’applications aux batteries de serveurs dans SharePoint 2013](https://technet.microsoft.com/library/cc261752(v=office.15).aspx)
  
  