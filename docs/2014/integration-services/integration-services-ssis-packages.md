---
title: Packages Integration Services (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, about packages
- packages [Integration Services], about packages
- SSIS packages, about packages
- SSIS packages
- SQL Server Integration Services packages
- containers [Integration Services], packages
- packages [Integration Services]
- Integration Services packages, about packages
- Integration Services packages
ms.assetid: 9266bc64-7e1a-4e78-913b-a8deaa9843bf
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c610f28e0b36e6dcf0ad34345c78868d09a4f1eb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48058879"
---
# <a name="integration-services-ssis-packages"></a>Packages Integration Services (SSIS)
  Un package est une collection organisée de connexions, d'éléments de flux de contrôle, d'éléments de flux de données, de gestionnaires d'événements, de variables, de paramètres et de configurations que vous assemblez à l'aide des outils de conception graphiques de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ou que vous créez via un programme.  Vous enregistrez le package terminé dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], le magasin de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] , ou le système de fichiers, ou vous pouvez déployer le projet ssISnoversion sur le serveur [!INCLUDE[ssIS](../includes/ssis-md.md)] . Le package est l'unité de travail qui est extraite, exécutée et enregistrée.  
  
 Lorsque vous créez un package, il s'agit d'un objet vide qui ne fait rien. Pour doter un package de fonctionnalités, vous ajoutez à celui-ci un flux de contrôle et, éventuellement un ou plusieurs flux de données.  
  
 Le schéma suivant illustre un package simple contenant un flux de contrôle avec une tâche de flux de données, qui contient à son tour un flux de données.  
  
 ![Package avec un flux de contrôle et un flux de données](media/ssis-package.gif "Package avec un flux de contrôle et un flux de données")  
  
 Après avoir créé le package de base, vous pouvez l'enrichir en y ajoutant des fonctionnalités avancées telles que la journalisation et des variables. Pour plus d'informations, consultez la section relative aux objets qui étendent les fonctionnalités des packages.  
  
 Vous pouvez ensuite configurer le package achevé en définissant les propriétés de niveau package qui mettent en œuvre la sécurité, autorisent le redémarrage des packages à partir de points de contrôle ou incorporent des transactions dans le flux de travail des packages. Pour plus d'informations, consultez la section relative aux propriétés qui prennent en charge les fonctionnalités étendues.  
  
## <a name="package-content"></a>Contenu des packages  
 Un flux de contrôle comprend un ou plusieurs conteneurs ou tâches qui s'exécutent quand le package s'exécute. Pour contrôler l'ordre ou définir les conditions d'exécution des tâches et des conteneurs les uns à la suite des autres dans le flux de contrôle du package, vous utilisez des contraintes de priorité afin de connecter les tâches et les conteneurs dans le package. Un sous-ensemble de tâches et de conteneurs peut également être regroupé et exécuté de façon répétée en tant qu'unité dans le flux de contrôle du package. Pour plus d’informations, consultez [Control Flow](control-flow/control-flow.md).  
  
 Un flux de données comprend les sources et les destinations qui extraient et chargent les données, les transformations qui modifient et étendent les données, ainsi que les chemins qui relient les sources, les transformations et les destinations. Vous ne pouvez ajouter un flux de données à un package que si le flux de contrôle du package comprend une tâche de flux de données. La tâche de flux de données est l'exécutable qui, dans le package [!INCLUDE[ssIS](../includes/ssis-md.md)] , crée, ordonne et exécute le flux de données. Une instance distincte du moteur de flux de données est ouverte pour chaque tâche de flux de données comprise dans un package. Pour plus d'informations, consultez [Data Flow Task](control-flow/data-flow-task.md) et [Data Flow](data-flow/data-flow.md).  
  
 En règle générale, un package comprend au moins un gestionnaire de connexions. Un gestionnaire de connexions est un lien entre un package et une source de données, qui définit la chaîne de connexion permettant d'accéder aux données utilisées par les tâches, les transformations et les gestionnaires d'événements du package. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dispose de types de connexion pour des sources de données telles que les fichiers texte et XML, les bases de données relationnelles, et les bases de données et les projets [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Pour plus d’informations, consultez [Connexions Integration Services &#40;SSIS&#41;](connection-manager/integration-services-ssis-connections.md).  
  
## <a name="package-templates"></a>Modèles de packages  
 Les packages sont fréquemment utilisés comme modèles permettant de générer des packages qui partagent des fonctionnalités de base. Vous construisez le package de base, puis le copiez, ou vous pouvez préciser que le package est un modèle. Par exemple, un package qui télécharge et copie des fichiers, puis extrait les données peut inclure les tâches FTP et de système de fichiers dans une boucle Foreach qui énumère les fichiers dans un dossier. Il peut également inclure des gestionnaires de connexions de fichiers plats pour accéder aux données, ainsi que des sources de fichiers plats pour extraire les données. La destination des données varie, et elle est ajoutée à chaque nouveau package après sa copie à partir du package de base. Vous pouvez également créer des packages, puis les utiliser comme modèles pour les nouveaux packages que vous ajoutez à un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Pour plus d'informations, consultez [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md).  
  
 Création d’un package tout d’abord, soit par programme ou à l’aide du concepteur SSIS, un GUID est ajouté à son `ID` propriété et un nom à son `Name` propriété. Si vous créez un nouveau package en copiant un package existant ou en utilisant un modèle de package, le nom et le GUID sont également copiés. Cela peut causer un problème si vous utilisez la journalisation, car le GUID et le nom du package sont écrits dans les journaux pour identifier le package auquel les informations consignées appartiennent. Par conséquent, vous devez mettre à jour le nom et le GUID des nouveaux packages pour les différencier plus facilement du package à partir duquel ils ont été copiés et entre eux dans les données du journal.  
  
 Pour modifier le GUID du package, vous régénérez un GUID dans le `ID` propriété dans la fenêtre Propriétés dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Pour modifier le nom du package, vous pouvez mettre à jour la valeur de la `Name` propriété dans la fenêtre Propriétés. Vous pouvez également utiliser l’invite de commandes **dtutil** ou mettre à jour le GUID et le nom par programmation. Pour plus d’informations, consultez [Définir les propriétés d’un package](set-package-properties.md) et [Utilitaire dtutil](dtutil-utility.md).  
  
## <a name="objects-that-extend-package-functionality"></a>Objets étendant les fonctionnalités des packages  
 Les packages peuvent comprendre des objets supplémentaires qui offrent des fonctionnalités avancées ou étendent les fonctionnalités existantes, telles que les gestionnaires d'événements, les configurations, la journalisation et les variables.  
  
### <a name="event-handlers"></a>Gestionnaires d'événements  
 Un gestionnaire d'événements est un flux de travail qui s'exécute en réponse aux événements déclenchés par un package, une tâche ou un conteneur. Par exemple, vous pouvez utiliser un gestionnaire d'événements pour vérifier l'espace disque lorsqu'un événement se produit avant l'exécution ou si une erreur se produit, et envoyer à un administrateur un message électronique indiquant l'espace disponible ou des informations sur l'erreur. Un gestionnaire d'événements est construit comme un package, avec un flux de contrôle et des flux de données facultatifs. Vous pouvez ajouter des gestionnaires d'événements à des tâches ou à des conteneurs spécifiques dans le package. Pour plus d’informations, consultez [Gestionnaires d’événements Integration Services &#40;SSIS&#41;](integration-services-ssis-event-handlers.md).  
  
### <a name="configurations"></a>Configurations  
 Une configuration est un ensemble de paires propriété/valeur qui définit les propriétés du package et ses tâches, conteneurs, variables, connexions et gestionnaires d'événements lorsque le package s'exécute. Les configurations permettent de mettre à jour les propriétés sans modifier le package. Lorsque le package est exécuté, les informations de configuration sont chargées et mettent à jour les valeurs des propriétés. Par exemple, une configuration peut mettre à jour la chaîne de connexion.  
  
 La configuration est enregistrée puis déployée avec le package lorsque celui-ci est installé sur un autre ordinateur. Lorsque vous installez le package, vous pouvez mettre à jour les valeurs de la configuration afin qu'il puisse être pris en charge dans un autre environnement. Pour plus d’informations, consultez [Créer des configurations de package](../../2014/integration-services/create-package-configurations.md).  
  
### <a name="logging-and-log-providers"></a>Journalisation et modules fournisseurs d'informations  
 Un journal est une collection d'informations relatives au package, qui sont rassemblées lorsque celui-ci s'exécute. Par exemple, un journal peut indiquer l'heure de début et de fin de l'exécution d'un package. Un module fournisseur d'informations définit le type de destination et le format que le package et ses conteneurs et ses tâches peuvent utiliser pour consigner les informations d'exécution. Les journaux sont associés à un package, mais les tâches et les conteneurs figurant dans le package peuvent consigner des informations dans n'importe quel journal de package. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] comprend une série de modules fournisseurs d’informations intégrés qui facilitent la journalisation. Par exemple, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] comprend des modules fournisseurs d'informations pour les fichiers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les fichiers texte. Vous pouvez également créer des modules fournisseurs d'informations personnalisés et les utiliser pour la journalisation. Pour plus d’informations, consultez [Journalisation Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md).  
  
### <a name="variables"></a>Variables  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] prend en charge les variables système et les variables définies par l’utilisateur. Les variables système fournissent des informations utiles sur les objets de package lors de l'exécution, tandis que les variables définies par l'utilisateur prennent en charge des scénarios personnalisés dans les packages. Vous pouvez utiliser les deux types de variables dans les expressions, les scripts et les configurations.  
  
 Les variables de niveau package comprennent les variables système prédéfinies disponibles pour un package et les variables définies par l'utilisateur et dont la portée s'étend au package. Pour plus d’informations, consultez [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).  
  
### <a name="parameters"></a>Paramètres  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] vous permettent d'affecter des valeurs aux propriétés dans des packages au moment de l'exécution du package. Vous pouvez créer des *paramètres de projet* au niveau du projet et des *paramètres de package* au niveau du package. Les paramètres du projet sont utilisés pour fournir une entrée externe que le projet reçoit à un ou plusieurs packages du projet. L'utilisation de paramètres de package vous permet de modifier l'exécution du package sans avoir à modifier et à redéployer le package. Pour plus d’informations, consultez [Integration Services &#40;SSIS&#41; Parameters](integration-services-ssis-package-and-project-parameters.md) (Paramètres Integration Services &#40;SSIS&#41;).  
  
## <a name="package-properties-that-support-extended-features"></a>Propriétés de package prenant en charge les fonctionnalités étendues  
 L'objet de package peut être configuré de manière à prendre en charge des fonctionnalités telles que le redémarrage du package aux points de contrôle, la signature du package avec un certificat numérique, la définition du niveau de protection du package et la sécurisation de l'intégrité des données à l'aide de transactions.  
  
### <a name="restarting-packages"></a>Redémarrage des packages  
 Le package comprend des propriétés de point de contrôle qui vous permettent de le redémarrer en cas d'échec d'une ou plusieurs de ses tâches. Par exemple, si un package possède deux tâches de flux de données qui mettent à jour deux tables différentes et que la deuxième tâche échoue, le package peut être réexécuté sans qu'il soit nécessaire de répéter la première tâche de flux de données. Le redémarrage d'un package peut être source de gain de temps pour les packages dont l'exécution est longue. La fonctionnalité de redémarrage vous permet de démarrer le package à partir de la tâche défaillante sans devoir réexécuter l'ensemble du package. Pour plus d'informations, consultez [Redémarrer des packages à l'aide de points de contrôle](packages/restart-packages-by-using-checkpoints.md).  
  
### <a name="securing-packages"></a>Sécurisation des packages  
 Vous pouvez signer un package au moyen d'une signature numérique et le chiffrer à l'aide d'un mot de passe ou d'une clé utilisateur. Une signature numérique authentifie la source du package. Toutefois, vous devez également configurer [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour vérifier la signature numérique lors du chargement du package. Pour plus d’informations, consultez [Identifier la source de packages à l’aide de signatures numériques](security/identify-the-source-of-packages-with-digital-signatures.md) et [Contrôle d’accès pour les données sensibles présentes dans les packages](security/access-control-for-sensitive-data-in-packages.md).  
  
### <a name="supporting-transactions"></a>Prise en charge des transactions  
 La définition d'un attribut de transaction au package permet d'associer les tâches, les conteneurs et les connexions du package à la transaction. Grâce aux attributs de transaction, le package et ses éléments réussissent ou échouent en tant qu'unité. Les packages peuvent également exécuter d'autres packages et inscrire d'autres packages dans les transactions, ce qui vous permet d'exécuter plusieurs packages en tant qu'unité de travail unique. Pour plus d’informations, consultez [Transactions Integration Services](integration-services-transactions.md).  
  
## <a name="custom-log-entries-available-on-the-package"></a>Entrées de journal personnalisées disponibles dans le package  
 Le tableau suivant répertorie les entrées de journal personnalisées pour les packages. Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../../2014/integration-services/custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`PackageStart`|Indique que le package a commencé à s'exécuter.<br /><br /> Remarque : cette entrée de journal est automatiquement écrite dans le journal. Vous ne pouvez pas l'exclure.|  
|`PackageEnd`|Indique que le package est terminé.<br /><br /> Remarque : cette entrée de journal est automatiquement écrite dans le journal. Vous ne pouvez pas l'exclure.|  
|`Diagnostic`|Fournit des informations sur la configuration système qui affecte l'exécution du package, notamment le nombre d'exécutables pouvant s'exécuter simultanément.|  
  
## <a name="configuration-of-packages"></a>Configuration des packages  
 Vous pouvez définir les propriétés dans la fenêtre **Propriétés** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ou par programmation.  
  
 Pour plus d’informations sur la façon de définir ces propriétés à l’aide de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], consultez [Définir les propriétés d’un package](set-package-properties.md).  
  
 Pour plus d’informations sur la définition par programmation de ces propriétés, consultez <xref:Microsoft.SqlServer.Dts.Runtime.Package>.  
  
## <a name="related-tasks"></a>Tâches associées  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , [!INCLUDE[ssIS](../includes/ssis-md.md)] met à votre disposition deux outils graphiques : le concepteur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et l'Assistant Importation et Exportation [!INCLUDE[ssIS](../includes/ssis-md.md)] . Consultez les rubriques suivantes pour plus de détails.  
  
-   [Exécuter l’Assistant Importation et Exportation SQL Server](import-export-data/start-the-sql-server-import-and-export-wizard.md)  
  
-   [Créer des packages dans les outils de données SQL Server](create-packages-in-sql-server-data-tools.md)  
  
-   Consultez la section **Génération de packages par programmation** du Guide du développeur.  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Implémentation de SQL Server Integration Services avec Microsoft Dynamics Mobile](http://msdn.microsoft.com/library/cc563950)  
  
-   [Comment : configurer un Package SQL Server Integration Services pour Microsoft Dynamics AX](http://msdn.microsoft.com/library/bb986852)  
  
  
