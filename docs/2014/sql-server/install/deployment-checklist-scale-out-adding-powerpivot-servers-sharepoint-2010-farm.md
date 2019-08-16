---
title: 'Liste de vérification du déploiement: Montée en puissance parallèle en ajoutant des serveurs PowerPivot à une batterie de serveurs SharePoint 2010 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2dbddcc7-427a-4537-a8e2-56d99b9d967d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: db17c7d395507072745ec8c4b7dd606efea75230
ms.sourcegitcommit: 187f6d327421e64f1802a3085f88bbdb0c79b707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69530927"
---
# <a name="deployment-checklist-scale-out-by-adding-powerpivot-servers-to-a-sharepoint-2010-farm"></a>Liste de vérification du déploiement: scale-out en ajoutant des serveurs PowerPivot à une batterie SharePoint 2010
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
|Déterminez le compte de service de l'instance Analysis Services qui se trouve déjà dans la batterie|Chaque instance supplémentaire que vous installez doit s'exécuter sous le même compte que la première instance. Utilisez l'une de ces méthodes pour déterminer le compte de service :<br /><br /> Dans l’administration centrale, dans la section sécurité, cliquez sur **configurer les comptes de service**. Sélectionnez **service Windows-SQL Server Analysis Services**. Une fois le service sélectionné, le nom du compte de service s'affiche dans la page.<br /><br /> Sur un serveur qui dispose déjà d’une installation de service PowerPivot, ouvrez l’application console **services** dans outils d’administration. Double-cliquez sur **SQL Server Analysis Services**. Cliquez sur l’onglet **ouvrir une session** pour afficher le compte de service.<br />**Important Utilisezuniquement\* l’administration centrale pour modifier les comptes de service. \* \* \*** Si vous utilisez un autre outil ou une autre méthode, les autorisations ne seront pas mises à jour correctement dans la batterie.|  
|Exécutez le programme d'installation pour installer une deuxième instance de PowerPivot pour SharePoint|[Installer PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)<br /><br /> Choisissez un serveur d'applications joint à la batterie, mais qui ne dispose pas d'une instance existante de PowerPivot sur le serveur.<br /><br /> Pendant l'installation, lorsque vous êtes invité à spécifier un compte de service, entrez le compte provenant de l'étape précédente. Toutes les instances du service Analysis Services doivent s'exécuter sous le même compte de domaine. Cette spécification autorise l'utilisation de la fonctionnalité de comptes gérés dans SharePoint qui vous permet de mettre à jour le mot de passe à un emplacement pour toutes les instances de service du même type.|  
|Configurez la deuxième instance|Vous pouvez utiliser l’une ou l’autre approche pour configurer l’instance: [Outils de configuration de PowerPivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools) ou [configuration PowerPivot à l’aide de Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell)<br /><br /> Lors de la configuration d'une deuxième instance, vous devez uniquement configurer les services locaux. Toutes les autres tâches de configuration (telles que la création d'applications de service ou la configuration de l'actualisation des données) sont effectuées lors de la configuration initiale et utilisées par les instances suivantes que vous installez.|  
|Tâches de post-installation|Aucune étape n'est spécifiquement requise. Vous n'avez pas besoin de créer des applications de service, d'activer des fonctionnalités, de déployer des solutions ni de modifier l'identité d'application de service. Les applications Web et applications de service existantes découvriront et utiliseront automatiquement le nouveau logiciel serveur.<br /><br /> Éventuellement, si vous avez installé un deuxième serveur pour utiliser un serveur pour les requêtes et un autre pour l'actualisation des données, vous pouvez désormais configurer les propriétés d'instance de serveur pour spécifier le type de requêtes traitées par chaque serveur. Pour plus d’informations, consultez [configurer l’actualisation des données dédiées ou &#40;le&#41;traitement des requêtes uniquement PowerPivot pour SharePoint](../../analysis-services/configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md).|  
|Vérifier l'installation de la deuxième instance|Vous pouvez utiliser les étapes suivantes pour vérifier le traitement des requêtes PowerPivot sur le serveur que vous venez d'installer.<br /><br /> 1) dans l’administration centrale, ouvrez la page gérer les services sur le serveur pour vérifier que le serveur et ses services s’affichent.<br />-Dans serveur, cliquez sur la flèche orientée vers le bas, cliquez sur modifier le serveur, puis sélectionnez le serveur sur lequel est installée la nouvelle PowerPivot pour SharePoint.<br />-Vérifiez que les service système PowerPivot SQL Server Analysis Services et SQL Server sont démarrées.<br /><br /> 2) dans l’administration centrale, arrêtez les autres serveurs PowerPivot pour SharePoint afin que le serveur que vous venez d’installer soit le seul disponible. Pour plus d’informations, consultez [Démarrer ou arrêter un serveur PowerPivot pour SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/start-or-stop-a-power-pivot-for-sharepoint-server).<br /><br /> 3) cliquez sur un classeur PowerPivot pour l’ouvrir à partir de la bibliothèque.<br /><br /> 4) cliquez sur un segment ou faites pivoter les données pour lancer une requête. Le serveur charge les données PowerPivot en arrière-plan. À l'étape suivante, vous allez vous connecter au serveur pour vérifier que les données sont chargées et mises en cache.<br /><br /> 5) Démarrez SQL Server Management Studio à partir du groupe de programmes Microsoft SQL Server dans le menu Démarrer. Si cet outil n'est pas installé sur votre serveur, vous pouvez passer à la dernière étape pour confirmer la présence de fichiers mis en cache.<br /><br /> 6) dans type de serveur, sélectionnez **Analysis Services**.<br /><br /> 7) dans nom du serveur, entrez  **\<Server-Name > \powerpivot**, où  **\<Server-Name >** est le nom de l’ordinateur sur lequel est installée la nouvelle PowerPivot pour SharePoint.<br /><br /> 8) cliquez sur **se connecter**.<br /><br /> 9) dans l’Explorateur d’objets, cliquez sur **bases de données** pour afficher la liste des fichiers de données PowerPivot qui sont chargés.<br /><br /> 10) sur le système de fichiers de l’ordinateur, vérifiez le dossier suivant pour déterminer si les fichiers sont mis en cache sur le disque. La présence de fichiers mis en cache est une vérification supplémentaire que votre déploiement est opérationnel. Pour consulter le cache des fichiers, accédez au dossier \Program Files\Microsoft SQL Server\MSAS11.POWERPIVOT\OLAP\Backup.<br /><br /> 11) redémarrez les services que vous avez arrêtés précédemment.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration &#40;initiale PowerPivot pour SharePoint&#41;](../../../2014/sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)   
 [Installation de PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)   
 [Administration et configuration d’un serveur PowerPivot dans l’Administration centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration)  
  
  
