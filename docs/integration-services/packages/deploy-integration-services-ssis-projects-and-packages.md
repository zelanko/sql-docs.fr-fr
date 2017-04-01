---
title: "D&#233;ployer des projets et des packages Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bea8ce8d-cf63-4257-840a-fc9adceade8c
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# D&#233;ployer des projets et des packages Integration Services (SSIS)
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prend en charge deux modèles de déploiement : le modèle de déploiement de projet et le modèle de déploiement de package hérité. Le modèle de déploiement de projet vous permet de déployer vos projets sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Pour plus d’informations sur le déploiement de projets sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Déployer des projets sur le serveur Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md).  
  
 Pour plus d’informations sur le modèle de déploiement de package hérité, consultez [Déploiement de packages hérités &#40;SSIS&#41;](../../integration-services/packages/legacy-package-deployment-ssis.md).  
  
> [!NOTE]  
>  Le modèle de déploiement du projet a été présenté pour la première fois dans [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]. Si vous utilisez ce modèle, vous ne pouvez pas déployer un ou plusieurs packages sans déployer le projet dans son ensemble. La fonctionnalité de déploiement incrémentiel de packages présentée pour la première fois dans [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] vous permet de déployer un ou plusieurs packages sans déployer la totalité du projet. Pour en savoir sur cette fonctionnalité, consultez [Déployer des packages sur le serveur Integration Services](../../integration-services/packages/deploy-packages-to-integration-services-server.md) .  
  
## Comparer le modèle de déploiement de projet et le modèle de déploiement de package hérité  
 Le type de modèle de déploiement que vous choisissez pour un projet détermine les options de développement et d'administration qui sont disponibles pour ce projet. Le tableau suivant présente les différences et les ressemblances entre l'utilisation du modèle de déploiement de projet et l'utilisation du modèle de déploiement de package.  
  
|En cas d'utilisation du modèle de déploiement de projet|En cas d’utilisation du modèle de déploiement de package hérité|  
|---------------------------------------------|----------------------------------------------------|  
|Un projet est l'unité de déploiement.|Un package est l'unité de déploiement.|  
|Des paramètres sont utilisés pour affecter des valeurs aux propriétés du package.|Des configurations sont utilisées pour affecter des valeurs aux propriétés du package.|  
|Un projet, contenant des packages et des paramètres, est généré dans un fichier de déploiement de projet (extension .ispac).|Les packages (extension .dtsx) et les configurations (extension .dtsConfig) sont enregistrés individuellement dans le système de fichiers.|  
|Un projet, contenant des packages et des paramètres, est déployé dans le catalogue SSISDB sur une instance de SQL Server.|Les packages et les configurations sont copiés dans le système de fichiers sur un autre ordinateur. Les packages peuvent également être enregistrés dans la base de données MSDB sur une instance de SQL Server.|  
|L'intégration du CLR est requise sur le moteur de base de données.|L'intégration du CLR n'est pas requise sur le moteur de base de données.|  
|Les valeurs des paramètres spécifiques à l'environnement sont stockées dans des variables d'environnement.|Les valeurs de la configuration spécifique à l'environnement sont stockées dans des fichiers de configuration.|  
|Les projets et les packages contenus dans le catalogue peuvent être validés sur le serveur avant l'exécution. Vous pouvez effectuer la validation à l'aide de SQL Server Management Studio, de procédures stockées ou de code managé.|Les packages sont validés juste avant l'exécution. Vous pouvez également valider un package avec dtExec ou du code managé.|  
|Les packages sont exécutés en démarrant une exécution sur le moteur de base de données. Un identificateur de projet, des valeurs de paramètre explicites (facultatif) et des références environnementales (facultatif) sont affectés à une exécution avant son démarrage.<br /><br /> Vous pouvez également exécuter des packages à l'aide de **dtExec**.|Les packages sont exécutés à l'aide des utilitaires d'exécution **dtExec** et **DTExecUI**. Les configurations applicables sont identifiées par des arguments d'invite de commandes (facultatif).|  
|Pendant l'exécution, les événements qui sont produits par le package sont automatiquement capturés et sont enregistrés dans le catalogue. Vous pouvez interroger ces événements avec des vues Transact-SQL.|Pendant l'exécution, les événements qui sont produits par un package ne sont pas automatiquement capturés. Un module fournisseur d'informations doit être ajouté au package pour capture les événements.|  
|Les packages sont exécutés dans un processus Windows distinct.|Les packages sont exécutés dans un processus Windows distinct.|  
|L'Agent SQL Server est utilisé pour planifier l'exécution du package.|L'Agent SQL Server est utilisé pour planifier l'exécution du package.|  
  
 Le modèle de déploiement du projet a été présenté pour la première fois dans [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]. Si vous utilisez ce modèle, vous ne pouvez pas déployer un ou plusieurs packages sans déployer le projet dans son ensemble. La fonctionnalité de déploiement incrémentiel de packages présentée pour la première fois dans [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] vous permet de déployer un ou plusieurs packages sans déployer la totalité du projet. Pour en savoir sur cette fonctionnalité, consultez [Déployer des packages sur le serveur Integration Services](../../integration-services/packages/deploy-packages-to-integration-services-server.md) .  
  
## Fonctionnalités du modèle de déploiement de projet  
 Le tableau suivant répertorie les fonctionnalités disponibles pour les projets développés uniquement pour le modèle de déploiement de projet.  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Paramètres|Un paramètre spécifie les données qui seront utilisées par un package. Vous pouvez définir l'étendue des paramètres au niveau du package ou au niveau du projet avec des paramètres de package et des paramètres de projet, respectivement. Des paramètres peuvent être utilisés dans des expressions ou des tâches. Lorsque le projet est déployé dans le catalogue, vous pouvez affecter une valeur littérale pour chaque paramètre ou utiliser la valeur par défaut qui a été affectée au moment de la conception. Au lieu d'une valeur littérale, vous pouvez également référencer une variable d'environnement. Les valeurs de variable d'environnement sont résolues au moment de l'exécution du package.|  
|Environnements|Un environnement est un conteneur de variables qui peuvent être référencées par les projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Chaque projet peut avoir plusieurs références environnementales, mais une instance d'exécution de package unique ne peut faire référence qu'à des variables d'un environnement unique. Les environnements vous permettent d'organiser les valeurs que vous affectez à un package. Par exemple, vous pouvez avoir des environnements nommés « Dev », « test » et « Production ».|  
|Variables d'environnement|Une variable d'environnement définit une valeur littérale qui peut être affectée à un paramètre pendant l'exécution du package. Pour utiliser une variable d'environnement, créez une référence environnementale (dans le projet qui correspond à l'environnement ayant le paramètre), affectez une valeur de paramètre au nom de la variable d'environnement, puis spécifiez la référence environnementale correspondante lorsque vous configurez une instance d'exécution.|  
|Catalogue SSISDB|Tous les objets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sont stockés et gérés sur une instance de SQL Server dans une base de données appelée catalogue SSISDB. Ce catalogue vous permet d'utiliser des dossiers pour organiser vos projets et environnements. Chaque instance de SQL Server ne peut disposer que d'un seul catalogue. Chaque catalogue peut avoir zéro dossier ou plus. Chaque dossier peut avoir zéro projet ou plus et zéro environnement ou plus. Un dossier du catalogue peut également être utilisé comme limite pour les autorisations sur des objets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|Procédures stockées et vues du catalogue|Un grand nombre de procédures stockées et de vues peuvent être utilisées pour gérer les objets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] du catalogue. Par exemple, vous pouvez spécifier des valeurs pour des paramètres et des variables d'environnement, créer et démarrer des exécutions, et surveiller des opérations de catalogue. Vous pouvez même afficher exactement la valeur qui sera utilisée par un package avant le démarrage de l'exécution.|  
  
## Déploiement de projet  
 Au centre du modèle de déploiement de projet se trouve le fichier de déploiement de projet (extension .ispac). Le fichier de déploiement de projet est une unité de déploiement autonome qui inclut uniquement les informations essentielles relatives aux packages et aux paramètres du projet. Le fichier de déploiement de projet ne capture pas toutes les informations contenues dans le fichier projet Integration Services (extension .dtproj). Par exemple, les fichiers texte supplémentaires que vous utilisez pour l'écriture de commentaires ne sont pas stockés dans le fichier de déploiement de projet, et ne sont donc pas déployés dans le catalogue.  
  
## Tâches requises  
  
-   [Déployer des projets sur le serveur Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md)  
  
## Contenu connexe  
 Entrée de blog, [Thoughts on Branching Strategies for SSIS Projects](http://go.microsoft.com/fwlink/?LinkId=245739), sur mattmasson.com.  
  
## Voir aussi  
 [Utilitaire dtexec](../../integration-services/packages/dtexec-utility.md)  
  
  