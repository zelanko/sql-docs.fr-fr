---
title: 'Liste de vérification de déploiement : Montée en puissance en ajoutant des serveurs PowerPivot à une batterie de serveurs SharePoint 2010 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 2dbddcc7-427a-4537-a8e2-56d99b9d967d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9a9e726aea4428ac061ca57a4c1bc28199492492
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218131"
---
# <a name="deployment-checklist-scale-out-by-adding-powerpivot-servers-to-a-sharepoint-2010-farm"></a>Liste de vérification de déploiement : Montée en puissance en ajoutant des serveurs PowerPivot à une batterie de serveurs SharePoint 2010
  Si vous anticipez un volume élevé de demandes de traitement de requêtes PowerPivot dans une batterie de serveurs SharePoint, vous pouvez ajouter une instance supplémentaire de PowerPivot pour SharePoint afin d'ajouter de façon transparente un support de traitement des nouvelles requêtes et données.  
  
 Après avoir installé une nouvelle instance, vous disposerez d'une capacité supplémentaire pour interroger les données PowerPivot ou traiter les travaux d'actualisation des données PowerPivot. Vous pourrez éventuellement configurer chaque serveur afin que celui-ci ne gère qu'un type de demande : requête ou actualisation des données.  
  
## <a name="prerequisites"></a>Prérequis  
 SharePoint Server 2010 est installé et configuré.  
  
 SharePoint Server 2010 SP1 est appliqué et la batterie est mise à niveau.  
  
 L'instance existante de PowerPivot pour SharePoint dans la batterie de serveurs est [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (nouvelle installation ou mise à niveau à partir de SQL Server 2008 R2).  
  
 L'ordinateur sur lequel vous installez le nouveau serveur [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot pour SharePoint est associé à la batterie. L'ordinateur et les autres serveurs de la batterie doivent se trouver dans le même domaine.  
  
 Consultez les rubriques supplémentaires suivantes pour comprendre les exigences du système et des versions :  
  
-   [Instructions d’utilisation des fonctionnalités BI de SQL Server dans une batterie de serveurs SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
> [!NOTE]  
>  Dans une batterie de plusieurs serveurs, toutes les instances de PowerPivot pour SharePoint doivent avoir la même version. Si vous avez appliqué des Service Packs ou des mises à jour à d'autres serveurs PowerPivot qui sont déjà dans la batterie, la nouvelle instance que vous ajoutez doit être mise à jour dans la même version que l'instance déjà existante dans la batterie. La nouvelle instance ne sera pas disponible tant que les mises à jour n'auront pas été appliquées.  
  
## <a name="steps"></a>Étapes  
 Utilisez cette liste de vérification pour ajouter des serveurs PowerPivot supplémentaires à une batterie de serveurs SharePoint. Ces instructions supposent que vous disposez déjà d'un serveur PowerPivot pour SharePoint dans la batterie et que vous ajoutez un deuxième serveur pour gérer la charge de traitement supplémentaire. À part certaines différences dans les conditions d'installation requises, la configuration après installation et la vérification, les étapes de déploiement d'une solution avec montée en puissance parallèle sont identiques à l'ajout d'un seul serveur PowerPivot à une batterie existante.  
  
|Étape|Lien|  
|----------|----------|  
|Déterminez le compte de service de l'instance Analysis Services qui se trouve déjà dans la batterie|Chaque instance supplémentaire que vous installez doit s'exécuter sous le même compte que la première instance. Utilisez l'une de ces méthodes pour déterminer le compte de service :<br /><br /> Dans l’Administration centrale, dans la section sécurité, cliquez sur **configurer les comptes de Service**. Sélectionnez **Service Windows – SQL Server Analysis Services**. Une fois le service sélectionné, le nom du compte de service s'affiche dans la page.<br /><br /> Sur un serveur qui a déjà une installation de service PowerPivot, ouvrez le **Services** application dans les outils d’administration de la console. Double-cliquez sur **SQL Server Analysis Services**. Cliquez sur le **ouverture de session** onglet pour afficher le compte de service.<br />**\*\* Important \* \***  uniquement utiliser l’Administration centrale pour modifier les comptes de service. Si vous utilisez un autre outil ou une autre méthode, les autorisations ne seront pas mises à jour correctement dans la batterie.|  
|Exécutez le programme d'installation pour installer une deuxième instance de PowerPivot pour SharePoint|[Installer PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)<br /><br /> Choisissez un serveur d'applications joint à la batterie, mais qui ne dispose pas d'une instance existante de PowerPivot sur le serveur.<br /><br /> Pendant l'installation, lorsque vous êtes invité à spécifier un compte de service, entrez le compte provenant de l'étape précédente. Toutes les instances du service Analysis Services doivent s'exécuter sous le même compte de domaine. Cette spécification autorise l'utilisation de la fonctionnalité de comptes gérés dans SharePoint qui vous permet de mettre à jour le mot de passe à un emplacement pour toutes les instances de service du même type.|  
|Configurez la deuxième instance|Vous pouvez utiliser deux approches pour configurer l’instance : [PowerPivot Configuration Tools](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md) ou [Configuration de PowerPivot à l’aide de Windows PowerShell](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)<br /><br /> Lors de la configuration d'une deuxième instance, vous devez uniquement configurer les services locaux. Toutes les autres tâches de configuration (telles que la création d'applications de service ou la configuration de l'actualisation des données) sont effectuées lors de la configuration initiale et utilisées par les instances suivantes que vous installez.|  
|Tâches de post-installation|Aucune étape n'est spécifiquement requise. Vous n'avez pas besoin de créer des applications de service, d'activer des fonctionnalités, de déployer des solutions ni de modifier l'identité d'application de service. Les applications Web et applications de service existantes découvriront et utiliseront automatiquement le nouveau logiciel serveur.<br /><br /> Éventuellement, si vous avez installé un deuxième serveur pour utiliser un serveur pour les requêtes et un autre pour l'actualisation des données, vous pouvez désormais configurer les propriétés d'instance de serveur pour spécifier le type de requêtes traitées par chaque serveur. Pour plus d’informations, consultez [configurer l’actualisation des données dédié ou traitement Query-Only &#40;PowerPivot pour SharePoint&#41;](../../analysis-services/configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md).|  
|Vérifier l'installation de la deuxième instance|Vous pouvez utiliser les étapes suivantes pour vérifier le traitement des requêtes PowerPivot sur le serveur que vous venez d'installer.<br /><br /> (1) dans l’Administration centrale, ouvrez Gérer les services sur la page du serveur pour confirmer que le serveur et ses services apparaissent.<br />-Dans le serveur, cliquez sur la flèche vers le bas, cliquez sur Modifier le serveur, puis sélectionnez le serveur qui possède la nouvelle installation de PowerPivot pour SharePoint.<br />-Vérifiez que SQL Server Analysis Services et Service de système de SQL Server PowerPivot sont démarrés.<br /><br /> (2) dans l’Administration centrale, arrêtez les autres serveurs PowerPivot pour SharePoint afin que le serveur que vous venez d’installer est le seul disponible. Pour plus d’informations, consultez [démarrer ou arrêter un PowerPivot pour SharePoint Server](../../analysis-services/power-pivot-sharepoint/start-or-stop-a-power-pivot-for-sharepoint-server.md).<br /><br /> (3) cliquez sur un classeur PowerPivot pour l’ouvrir à partir de la bibliothèque.<br /><br /> (4) cliquez sur un segment ou faites pivoter les données pour lancer une requête. Le serveur charge les données PowerPivot en arrière-plan. À l'étape suivante, vous allez vous connecter au serveur pour vérifier que les données sont chargées et mises en cache.<br /><br /> (5) démarrer SQL Server Management Studio à partir du groupe de programmes Microsoft SQL Server dans le menu Démarrer. Si cet outil n'est pas installé sur votre serveur, vous pouvez passer à la dernière étape pour confirmer la présence de fichiers mis en cache.<br /><br /> (6) dans le Type de serveur, sélectionnez **Analysis Services**.<br /><br /> (7) dans le nom du serveur, entrez  **\<nom-serveur > \powerpivot**, où  **\<nom-serveur >** est le nom de l’ordinateur qui contient la nouvelle installation de PowerPivot pour SharePoint.<br /><br /> 8) cliquez sur **connecter**.<br /><br /> 9) dans l’Explorateur d’objets, cliquez sur **bases de données** pour afficher la liste des fichiers de données PowerPivot qui sont chargés.<br /><br /> 10) sur le système de fichiers d’ordinateur, vérifiez le dossier suivant pour déterminer si les fichiers sont mis en cache sur le disque. La présence de fichiers mis en cache est une vérification supplémentaire que votre déploiement est opérationnel. Pour consulter le cache des fichiers, accédez au dossier \Program Files\Microsoft SQL Server\MSAS11.POWERPIVOT\OLAP\Backup.<br /><br /> 11) redémarrez les services que vous avez arrêtés précédemment.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration initiale &#40;PowerPivot pour SharePoint&#41;](../../../2014/sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)   
 [Installation PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)   
 [Administration et configuration d’un serveur PowerPivot dans l’Administration centrale](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
  
