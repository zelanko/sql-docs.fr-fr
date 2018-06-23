---
title: Sélection des fonctionnalités | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- feature selection, Setup
helpviewer_keywords:
- SQL Server Installation Wizard, Components to Install page
- Components to Install page [SQL Server Installation Wizard]
ms.assetid: 73182088-153b-4634-a060-d14d1fd23b70
caps.latest.revision: 86
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 159c77133a5b0a218fa308ab179b2d25376432bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142419"
---
# <a name="feature-selection"></a>Sélection des fonctionnalités
  Utilisez les cases à cocher de la page **Sélection de fonctionnalités** de l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour sélectionner les composants de votre installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="installing-includessnoversionincludesssnoversion-mdmd-features"></a>Installation des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Dans la page **Sélection de fonctionnalités** , les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont séparées en deux sections principales : **Fonctionnalités de l'instance** et **Fonctionnalités partagées**.  
  
 Les**fonctionnalités de l’instance** font référence aux composants installés une seule fois pour chaque instance pour pouvoir disposer de plusieurs copies de ces derniers (une pour chaque instance). Chaque instance peut être une version distincte qui a un niveau de correctif logiciel différent. Lorsque vous installez un correctif logiciel, s'il s'agit d'un Service Pack, d'un correctif logiciel ou d'une mise à jour cumulative, il met uniquement à jour les fichiers pour une instance sur un ordinateur donné, ainsi que les fonctionnalités partagées si elles n'ont pas déjà été mises à jour.  
  
 Les**fonctionnalités partagées** font référence aux fonctionnalités qui sont communes à toutes les instances sur un ordinateur donné. Chacune de ces fonctionnalités partagées est conçue pour assurer une compatibilité descendante avec les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prises en charge (Service Packs, mises à jour cumulatives et correctifs logiciels) qui peuvent être installées côte à côte.  
  
> [!NOTE]  
>  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :** les composants [!INCLUDE[ssDE](../../includes/ssde-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sont les seules fonctionnalités [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] qui prennent en charge le clustering de basculement. Vous pouvez installer d'autres composants, tels que [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ou [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], sur un nœud de cluster de basculement, mais ils ne prennent pas en charge les clusters et leurs services ne basculent pas si le nœud est placé hors connexion. Pour plus d’informations, consultez [Instances de cluster de basculement AlwaysOn &#40;SQL Server&#41;](../failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
### <a name="instance-features"></a>Fonctionnalités de l'instance  
 Une description de chaque groupe de composants s'affiche dans le volet **Description** en cas de sélection. Vous pouvez choisir n'importe quelle combinaison de cases à cocher. Pour continuer, vous devez faire une sélection.  
  
|Fonctionnalités|Description|  
|--------------|-----------------|  
|du[!INCLUDE[ssDE](../../includes/ssde-md.md)] |[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] inclut le [!INCLUDE[ssDE](../../includes/ssde-md.md)], le service principal de stockage, traitement et de sécurisation des données, réplication, recherche en texte intégral, outils de gestion relationnelles et XML et le [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] serveur (DQS). Les fonctionnalités du moteur de base de données sont les suivantes :<br /><br /> Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est le service central qui permet de stocker, traiter et sécuriser les données.<br /><br /> Réplication : facultatif : la réplication est un ensemble de technologies qui permettent de copier et de distribuer des données et des objets de base de données d'une base de données vers une autre, puis de synchroniser les bases de données afin de préserver leur cohérence.<br /><br /> Recherche en texte intégral : facultatif : la recherche en texte intégral fournit les fonctionnalités nécessaires à l'émission de requêtes de texte intégral sur les données caractères en texte brut des tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (facultatif) : [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) est une solution de nettoyage des données qui vous permet d'identifier les données incohérentes et incorrectes dans votre source de données et qui offre des solutions assistées par ordinateur et interactives de nettoyage des données. Activez cette case à cocher pour installer le serveur DQS. Une fois l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] terminée, vous devez exécuter le fichier DQSInstaller.exe pour *terminer* l'installation du serveur DQS. Si vous avez installé l’instance par défaut de SQL server, ce fichier est disponible sous C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12. MSSQLSERVER\MSSQL\Binn.<br /><br /> <br /><br /> **Clusters de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :** les composants de réplication et de recherche en texte intégral sont requis et sélectionnés automatiquement par le programme d’installation pour les installations du clustering de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lorsque vous sélectionnez Services Moteur de base de données.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] inclut les outils de création et de gestion d’applications de traitement analytique en ligne (OLAP, OnLine Analytical Processing) et d’exploration de données.|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] – Natif|Le mode natif [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] inclut les composants serveur et clients permettant de créer, de gérer et de déployer des rapports tabulaires, de matrice, graphiques et de forme libre. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est également une plateforme évolutive que vous pouvez utiliser pour développer des applications de création de rapports.|  
  
> [!IMPORTANT]  
>  1.  Le programme d'installation ne configure pas l'équilibrage de charge et l'adressage par URL unique pour les nœuds multiples d'un déploiement par montée en puissance parallèle de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Pour effectuer un déploiement avec montée en puissance parallèle, vous devez utiliser Windows Server, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Application Center ou un logiciel tiers de gestion de clusters. Pour plus d’informations sur la configuration de déploiement de batterie de serveurs Web, consultez [configuration de Reporting Services pour un déploiement évolutif](http://go.microsoft.com/fwlink/?LinkId=199448) (http://go.microsoft.com/fwlink/?LinkId=199448).  
> 2.  Pour connaître la configuration de navigateur requise des composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [Planification de la prise en charge des navigateurs pour Reporting Services et Power View &#40;Reporting Services 2014&#41;](../../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md).  
> 3.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n'est pas pris en charge simultanément dans les configurations côte à côte sur la plateforme 64 bits et sur le sous-système 32 bits (WOW64) d'un serveur 64 bits.  
  
### <a name="shared-features"></a>Fonctionnalités partagées  
 Les fonctionnalités partagées par toutes les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un même ordinateur sont installées dans un répertoire unique. Cela comprend les éléments suivants :  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] : SharePoint|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Le mode SharePoint est une application basée sur serveur pour créer, gérer et remettre des rapports par courrier électronique, plusieurs formats de fichier et interactif Web sous forme de formations. Le mode SharePoint intègre la consultation et la gestion de rapports avec les produits SharePoint. Pour plus d’informations, consultez [Serveur de rapports Reporting Services &#40;mode SharePoint&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md).|  
|Complément[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint Products|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Complément pour les produits SharePoint inclut des composants d’interface utilisateur et de gestion pour intégrer un produit SharePoint avec un [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] serveur de rapports en mode SharePoint. Pour plus d’informations, consultez [Où trouver le complément Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).|  
|Data Quality Client|Le client de qualité des données est une application autonome qui se connecte au serveur DQS et fournit une interface utilisateur graphique intuitive pour effectuer des opérations de nettoyage et de correspondance des données et effectuer des tâches administratives dans DQS.|  
|Connectivité des outils clients|Les outils clients incluent les composants permettant la communication entre les clients et les serveurs, notamment les bibliothèques réseau pour DB-Library, OLEDB pour OLAP, ODBC, ADODB et ADOMD+.|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] propose un ensemble d’outils graphiques et d’objets programmables permettant de déplacer, de copier et de transformer les données.|  
|Compatibilité descendante des outils clients|La compatibilité descendante des outils clients inclut les composants suivants :<br /><br /> Objets SQL-DMO (Distributed Management Objects). Pour plus d’informations, consultez [Fonctionnalités SQL Server supprimées dans SQL Server 2014](../../../2014/getting-started/discontinued-sql-server-features-in-sql-server-2014.md).<br /><br /> DSO (Decision Support Objects). Pour plus d’informations, consultez [Modifications avec rupture dans les fonctionnalités Analysis Services de SQL Server 2014](../../../2014/analysis-services/breaking-changes-to-analysis-services-features-in-sql-server-2014.md).|  
|Kit de développement logiciel (SDK) des outils clients|Inclut le Kit de développement logiciel (SDK) contenant des ressources pour les programmeurs.|  
|Composants de documentation|Les composants de documentation incluent les composants permettant d'afficher et de gérer le contenu d'aide.|  
|Outils de gestion - Base|**Outils de gestion - De base :** Notamment :<br /><br /> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] prise en charge pour le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], **sqlcmd** utilitaire et le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur PowerShell<br /><br /> **Outils de gestion – Complet :** Cela comprend les composants suivants en plus de ceux de la version de base :<br /><br /> Prise en charge de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]<br /><br /> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]<br /><br /> Database Engine Tuning Advisor<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Gestion de l’utilitaire|  
|Distributed Replay Controller|Le contrôleur Distributed Replay orchestre les actions des clients de relecture distribuée. Chaque environnement Distributed Replay ne doit contenir qu'une seule instance de contrôleur. Pour plus d'informations, consultez [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md).|  
|Distributed Replay Client|Les clients Distributed Replay fonctionnent ensemble pour simuler les charges de travail sur une instance de SQL Server. Chaque environnement Distributed Replay peut contenir un ou plusieurs clients. Pour plus d'informations, consultez [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md).|  
|Kit de développement logiciel (SDK) de l'option Connectivité client de SQL|Inclut le Kit de développement logiciel (SDK) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (ODBC/OLE DB) pour le développement d'applications de base de données.|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] est une plateforme pour intégrer des données issues de systèmes disparates de toute une organisation dans une source unique de données de référence à des fins de précision et d'audit. L'option [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] installe [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], des assemblys, un composant logiciel enfichable Windows PowerShell et des dossiers et des fichiers pour les applications et services Web.|  
  
 Par défaut, ces composants partagés sont installés dans %Program Files%Microsoft SQL Server\\. Pour modifier le chemin d'installation, cliquez sur le bouton **Parcourir** . La modification du chemin d'installation d'un composant partagé affecte également les autres composants partagés. En effet, les installations ultérieures placeront les composants partagés dans le même emplacement que celui de l'installation d'origine.  
  
 **Répertoire racine de l’instance** -par défaut, le répertoire racine de l’instance est C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\. Pour spécifier un répertoire racine non défini par défaut, cliquez sur le bouton **Parcourir** ou fournissez un nom de chemin.  
  
 Sur les systèmes d'exploitation x64, vous pouvez spécifier où les composants 64 bits doivent être installés et où les composants 32 bits doivent l'être sur le sous-système WOW64.  
  
## <a name="disk-space-requirements"></a>Espace disque nécessaire  
 Utilisez la page Résumé sur l'espace nécessaire pour examiner l'espace disque nécessaire pour les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sélectionnées pour votre installation.  
  
### <a name="options"></a>Options  
 Si la quantité d'espace disque requis est trop élevée, envisagez les options suivantes :  
  
-   Remplacez les répertoires d'installation par un lecteur disposant de davantage d'espace disque.  
  
-   Modifiez les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour votre installation.  
  
-   Créez davantage d'espace libre sur le lecteur spécifié en déplaçant d'autres fichiers ou applications.  
  
## <a name="installing-adventureworks-sample-databases"></a>Installation des exemples de bases de données AdventureWorks  
 Par défaut, les exemples de bases de données et les exemples de code ne sont pas installés dans le cadre de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations sur l’installation des exemples de code et de bases de données, consultez la [Microsoft SQL Server Community Projects & Samples](http://go.microsoft.com/fwlink/?LinkId=87843) (http://go.microsoft.com/fwlink/?LinkId=87843).  
  
 Les informations supplémentaires sur les exemples sont disponibles après que [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] a été installé. À partir de la **Démarrer** menu, cliquez sur **tous les programmes**, cliquez sur **[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**, cliquez sur **Documentation et didacticiels** , puis cliquez sur  **[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Samples Overview**.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditions et composants de SQL Server 2014](../editions-and-components-of-sql-server-2016.md)  
  
  