---
title: Projets Integration Services (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Integration Services], creating
- folders [Integration Services], projects
- files [Integration Services], projects
- folders [Integration Services]
- projects [Integration Services], about projects
ms.assetid: 28ea8120-0a79-4029-93f0-07d521b32bee
author: janinezhang
ms.author: janinez
ms.openlocfilehash: e48dfbf5420c6032b8185cf59b2b132df2c82cf2
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966236"
---
# <a name="integration-services-ssis-projects"></a>Projets Integration Services (SSIS)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fournit [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour le développement de packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .

 Lorsque vous déployez des packages sur une [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] base de données ou le magasin de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] , vous utilisez le [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service pour gérer les packages. Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] n'est disponible que dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Pour plus d’informations sur le service, consultez [Service Integration Services &#40;Service SSIS&#41;](service/integration-services-service-ssis-service.md). Pour plus d’informations sur le déploiement de packages, consultez [déploiement de packages &#40;&#41;SSIS ](packages/legacy-package-deployment-ssis.md).

 Lorsque vous déployez des projets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], vous utilisez des procédures stockées et des vues Transact-SQL dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour gérer les projets. Pour plus d'informations sur le déploiement de projets, consultez [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md). Pour plus d’informations sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], consultez [Serveur Integration Services &#40;SSIS&#41;](catalog/integration-services-ssis-server-and-catalog.md).

 Pour obtenir une vue d’ensemble de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] et [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], consultez [Integration Services &#40;SSIS&#41; et environnements de Studio](integration-services-ssis-development-and-management-tools.md).

## <a name="understanding-integration-services-projects"></a>Fonctionnement des projets Integration Services
 Un projet est un conteneur dans lequel vous développez des packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .

 Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stocke et groupe les fichiers associés au package. Par exemple, un projet inclut les fichiers requis pour créer une solution d'extraction, de transfert et de chargement (ETL) spécifique.

 Avant de créer un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , vous devez vous familiariser avec le contenu de base de ce type de projet. Une fois que vous connaissez le contenu d'un projet, vous pouvez commencer à créer et à utiliser un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .

### <a name="folders-in-integration-services-projects"></a>Dossiers des projets Integration Services
 Le diagramme qui suit montre les dossiers d'un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].

 ![Dossiers d'un projet Integration Services](media/solutionexplorer.gif "Dossiers d'un projet Integration Services")

 Le tableau suivant décrit les dossiers d'un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .

|Dossier|Description|
|------------|-----------------|
|[!INCLUDE[ssIS](../includes/ssis-md.md)] .|Contient les packages. Pour plus d’informations, consultez [Integration Services &#40;SSIS&#41;, packages](../../2014/integration-services/integration-services-ssis-packages.md).|
|Divers|Contient d'autres fichiers que les fichiers de package.|

### <a name="files-in-integration-services-projects"></a>Fichiers des projets Integration Services
 Lorsque vous ajoutez un nouveau projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ou un projet existant à une solution, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] crée des fichiers projet portant les extensions .dtproj, .dtproj.user et .database.

-   Le fichier *.dtproj contient des informations sur les configurations du projet et sur d'autres éléments tels que les packages.

-   Le fichier *.dtproj.user contient des informations sur vos préférences de travail avec le projet.

-   Le fichier *.database contient des informations requises par [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour ouvrir le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .

## <a name="understanding-solutions"></a>Fonctionnement des solutions
 Une solution est un conteneur qui regroupe et gère les projets que vous utilisez lorsque vous développez des solutions d'entreprise de bout en bout. Une solution vous permet de gérer plusieurs projets en une même unité et de regrouper plusieurs projets qui contribuent à une solution d'entreprise.

 Une solution peut contenir des projets de différents types. Si vous souhaitez utiliser le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] pour créer un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , vous travaillez dans un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans une solution fournie par [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].

 Lorsque vous créez une nouvelle solution, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ajoute un dossier Solution à l'Explorateur de solutions et crée des fichiers portant les extensions .sln et .suo :

-   Le fichier *.sln contient des informations sur la configuration de la solution et répertorie les projets de la solution.

-   Le fichier *.suo contient des informations sur vos préférences concernant l'utilisation de la solution.

 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] crée automatiquement une solution lorsque vous créez un projet, mais vous pouvez aussi créer une solution vierge et lui ajouter ultérieurement des projets.

> [!NOTE]
>  Par défaut, lorsque vous créez un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], la solution n'est pas affichée dans le volet **Explorateur de projets** . Pour modifier ce comportement par défaut, dans le menu **Outils** , cliquez sur **Options**. Dans la boîte de dialogue **Options** , développez **Projets et solutions**, puis cliquez sur **Général**. Dans la page **Général** , sélectionnez **Toujours afficher la solution**.

## <a name="related-tasks"></a>Tâches associées
 [Ajouter ou supprimer un projet Integration Services dans une solution](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)

 [Créer un projet Integration Services](../../2014/integration-services/create-a-new-integration-services-project.md)

 [Ajouter un élément à un projet Integration Services](../../2014/integration-services/add-an-item-to-an-integration-services-project.md)

 [Copier des éléments de projet](../../2014/integration-services/copy-project-items.md)

## <a name="related-content"></a>Contenu associé
 [Développement d'un projet Integration Services](../../2014/integration-services/development-of-an-integration-services-project.md)


