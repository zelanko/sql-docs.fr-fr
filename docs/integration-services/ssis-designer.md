---
title: "Concepteur SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "08/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.controlflowwindow.f1"
  - "sql13.dts.designer.dataflowwindow.f1"
  - "sql13.dts.designer.eventhandlerwindow.f1"
  - "sql13.dts.designer.treeview.f1"
  - "sql13.dts.designer.progress.f1"
  - "sql13.dts.designer.connectionstray.f1"
helpviewer_keywords: 
  - "SQL Server Integration Services, concepteur SSIS"
  - "Business Intelligence Development Studio, Integration Services"
  - "outils [Integration Services], concepteur SSIS"
  - "SSIS, concepteur SSIS"
  - "Concepteur SSIS, à propos du concepteur SSIS"
  - "Integration Services, concepteur SSIS"
ms.assetid: 006d68ea-1b5c-4c1e-8079-3910288e012c
caps.latest.revision: 59
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 58
---
# Concepteur SSIS
  [!INCLUDE[ssIS](../includes/ssis-md.md)] est un outil graphique permettant de créer et de gérer des packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssIS](../includes/ssis-md.md)] est disponible dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , en tant que projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Vous pouvez utiliser le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] pour effectuer les tâches suivantes :  
  
-   construire le flux de contrôle dans un package ;  
  
-   construire les flux de données dans un package ;  
  
-   ajouter des gestionnaires d'événements au package et aux objets du package ;  
  
-   afficher le contenu du package ;  
  
-   au moment de l'exécution, afficher la progression de l'exécution du package.  
  
 Le diagramme qui suit montre le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] et la fenêtre **Boîte à outils** .  
  
 ![Capture d'écran du concepteur SSIS et de la boîte à outils](../integration-services/media/denali-designerandtoolbox.gif "Capture d'écran du concepteur SSIS et de la boîte à outils")  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] comprend des boîtes de dialogue et des fenêtres supplémentaires permettant d'ajouter des fonctionnalités aux packages, tandis que [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] en propose d'autres pour configurer l'environnement de développement et l'utilisation de packages. Pour plus d’informations, consultez [Interface utilisateur d’Integration Services](../integration-services/integration-services-user-interface.md).  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] ne dépend pas du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (celui qui gère et surveille les packages) ; la création ou la modification de packages dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] ne requiert pas que ce service soit en cours d'exécution. Toutefois, si vous arrêtez ce service alors que le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] est ouvert, vous ne pouvez plus ouvrir les boîtes de dialogue fournies par le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] et vous risquez de recevoir le message d'erreur « Le serveur RPC n'est pas disponible ». Pour réinitialiser le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] et continuer à utiliser le package, vous devez fermer le concepteur, quitter [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], puis rouvrir [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et le package.  
  
## Annuler et rétablir  
 Vous pouvez annuler et rétablir au maximum 20 actions dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] . Pour un package, les opérations annuler/rétablir sont disponibles dans les onglets **Flux de contrôle**, **Flux de données**, **Gestionnaires d’événements** et **Paramètres**, et dans la fenêtre **Variables**. Pour un projet, ces opérations sont disponibles dans la fenêtre **Paramètres du projet**.  
  
 Vous ne pouvez pas annuler/rétablir les modifications apportées à la nouvelle **Boîte à outils SSIS**.  
  
 Lorsque vous apportez des modifications à un composant à l'aide de l'éditeur de composant, vous annulez et rétablissez les modifications en tant qu'ensemble au lieu d'annuler et rétablir des modifications individuelles. L'ensemble de modifications apparaît en tant qu'action unique dans la liste déroulante d'annulation et de rétablissement.  
  
 Pour annuler une action, cliquez sur le bouton Annuler de la barre d’outils, sur l’élément de menu **Modifier/Annuler** ou appuyez sur Ctrl+Z. Pour rétablir une action, cliquez sur le bouton Rétablir de la barre d’outils ou sur l’élément de menu **Modifier/Rétablir**, ou appuyez sur CTRL+Y. Vous pouvez annuler et rétablir plusieurs actions en cliquant sur la flèche en regard du bouton de la barre d’outils, en mettant en surbrillance plusieurs actions de la liste déroulante, puis en cliquant dans la liste.  
  
## Parties du concepteur SSIS  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] comprend cinq onglets permanents : un pour créer le flux de contrôle du package, un pour les flux de données, un pour les paramètres et un pour les gestionnaires d'événements, ainsi qu'un onglet pour afficher le contenu du package. Au moment de l'exécution, un sixième onglet apparaît pour indiquer la progression de l'exécution d'un package et les résultats de l'exécution une fois celle-ci terminée.  
  
 Par ailleurs, le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] contient une zone nommée Gestionnaires de connexions qui permet d'ajouter et de configurer les gestionnaires de connexions utilisés par un package pour se connecter aux données.  
  
### Onglet Flux de contrôle  
 Le flux de contrôle d'un package est construit sur l'aire de conception de l'onglet **Flux de contrôle** . Vous devez faire glisser des éléments de la **Boîte à outils** vers la surface de dessin, puis les relier en un flux de contrôle en cliquant sur l'icône d'un élément, puis en faisant glisser la flèche vers un autre élément.  
  
 Pour en savoir plus, voir [Control Flow](../integration-services/control-flow/control-flow.md).  
  
### Onglet Flux de données  
 Si un package contient une tâche de flux de données, vous pouvez ajouter des flux de données au package. Les flux de données d'un package sont construits sur la surface de dessin de l'onglet **Flux de données** . Vous devez faire glisser des éléments de la **Boîte à outils** vers la surface de dessin, puis les relier en un flux de données en cliquant sur l'icône d'un élément, puis en faisant glisser la flèche vers un autre élément.  
  
 Pour en savoir plus, voir [Data Flow](../integration-services/data-flow/data-flow.md).  
  
### Onglet paramètres  
 Les paramètres d'Integration Services (SSIS) vous permettent d'affecter des valeurs aux propriétés des packages au moment de l'exécution du package. Vous pouvez créer des paramètres de projet au niveau du projet et des paramètres de package au niveau du package. Les paramètres du projet sont utilisés pour fournir une entrée externe que le projet reçoit à un ou plusieurs packages du projet. L'utilisation de paramètres de package vous permet de modifier l'exécution du package sans avoir à modifier et à redéployer le package. Cet onglet vous permet de gérer les paramètres du package.  
  
 Pour plus d’informations sur les paramètres, consultez [Paramètres Integration Services (SSIS)](https://msdn.microsoft.com/library/hh213214.aspx).  
  
> **IMPORTANT**  Les paramètres sont disponibles uniquement pour les projets développés pour le modèle de déploiement de projet. Par conséquent, vous verrez l'onglet Paramètres uniquement pour les packages qui font partie d'un projet configuré pour utiliser le modèle de déploiement du projet.  
  
### Onglet Gestionnaires d'événements  
 Les événements d'un package sont construits sur la surface de dessin de l'onglet **Gestionnaires d'événements** . Sous l'onglet **Gestionnaires d'événements** , vous devez sélectionner le package ou l'objet du package pour lequel vous voulez créer un gestionnaire d'événements, puis sélectionner l'événement à associer au gestionnaire d'événements. Un gestionnaire d'événements contient un flux de contrôle et des flux de données facultatifs.  
  
 Pour en savoir plus, voir [Add an Event Handler to a Package](../Topic/Add%20an%20Event%20Handler%20to%20a%20Package.md).  
  
### Onglet Explorateur de package  
 Les packages peuvent être complexes et inclure de nombreuses tâches, gestionnaires de connexions, variables et autres éléments. L'Explorateur de package permet d'afficher une liste complète des éléments du package.  
  
 Pour plus d’informations, consultez [Afficher des objets de packages](../integration-services/view-package-objects.md).  
  
#### Onglet Progression/Résultats d'exécution  
 L'onglet **Progression** indique la progression de l'exécution du package. À la fin de l'exécution du package, les résultats de l'exécution sont disponibles sous l'onglet **Résultats d'exécution** .  
  
> **REMARQUE :** Pour activer ou désactiver l’affichage de messages sous l’onglet **Progression**, basculez l’option **Création de rapports de progression de débogage** dans le menu **SSIS**.  
  
##### Zone Gestionnaires de connexion  
 Ajoutez et modifiez les gestionnaires de connexions utilisés par un package dans la zone **Gestionnaires de connexions** . [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclut des gestionnaires de connexions permettant de se connecter à différentes sources de données, telles que des fichiers texte, des bases de données OLE DB et des fournisseurs .NET.  
  
 Pour plus d’informations, consultez [Connexions Integration Services &#40;SSIS&#41;](../integration-services/connection-manager/integration-services-ssis-connections.md) et [Créer des gestionnaires de connexions](../Topic/Create%20Connection%20Managers.md).  
  
## Tâches associées  
  
-   [Créer des packages dans les outils de données SQL Server](../integration-services/create-packages-in-sql-server-data-tools.md)  
  
## Voir aussi  
 [Interface utilisateur d'Integration Services](../integration-services/integration-services-user-interface.md)  
  
  