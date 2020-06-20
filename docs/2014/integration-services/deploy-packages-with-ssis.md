---
title: 'Didacticiel SSIS : déploiement de packages | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- deployment tutorial [Integration Services]
- deploying packages [Integration Services]
- SSIS, tutorials
- Integration Services, tutorials
- deploying packages [Integration Services], installing
- SQL Server Integration Services, tutorials
- walkthroughs [Integration Services]
- deployment utility [Integration Services]
- deploying packages [Integration Services], configurations
ms.assetid: de18468c-cff3-48f4-99ec-6863610e5886
author: janinezhang
ms.author: janinez
ms.openlocfilehash: f30221e3afb898834fcc13476760499fd3a5f9e8
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84951829"
---
# <a name="ssis-tutorial-deploying-packages"></a>Tutoriel SSIS : Déploiement des packages
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] propose des outils qui simplifient le déploiement des packages sur un autre ordinateur. Ces outils de déploiement gèrent aussi les dépendances, telles que les configurations et les fichiers dont les packages ont besoin. Dans ce didacticiel, vous allez apprendre à utiliser ces outils pour installer des packages et leurs dépendances sur un ordinateur cible.

 Pour commencer, vous allez effectuer les tâches de préparation du déploiement. Vous allez créer un nouveau projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] et ajouter des packages et des fichiers de données existants au projet. Vous n'allez pas créer de nouveaux packages entièrement ; en revanche, vous allez travailler uniquement avec des packages finalisés et créés spécialement pour ce didacticiel. Vous n'allez pas modifier les fonctionnalités des packages de ce didacticiel ; cependant, une fois que les packages sont ajoutés au projet, il vous sera peut-être utile d'ouvrir les packages dans le Concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] et d'examiner le contenu de chaque package. Cette opération vous permet d'obtenir des informations sur les dépendances de package telles que les fichiers journaux et d'autres fonctionnalités intéressantes des packages.

 En préparation du déploiement, vous allez aussi mettre à jour les packages pour utiliser des configurations. Les configurations permettent de mettre à jour les propriétés des packages et les objets de package au moment de l'exécution. Dans ce didacticiel, vous allez utiliser des configurations pour mettre à jour les chaînes de connexion des fichiers texte et journaux et les emplacements des fichiers XML et XSD utilisés par le package. Pour plus d’informations, consultez [Configurations de package](../../2014/integration-services/package-configurations.md) et [Créer des configurations de package](../../2014/integration-services/create-package-configurations.md).

 Après avoir vérifié que les packages s'exécutent correctement dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], vous allez créer l'application de déploiement nécessaire pour installer les packages. Cette application de déploiement se compose des fichiers de package et des autres éléments que vous avez ajoutés au projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , des dépendances du package qu'intègre automatiquement [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et de l'utilitaire de déploiement que vous avez créé. Pour plus d’informations, consultez [Créer un utilitaire de déploiement](../../2014/integration-services/create-a-deployment-utility.md).

 Vous allez copier ensuite l'application de déploiement sur l'ordinateur cible et exécuter l'Assistant Installation de package pour installer les packages et les dépendances de package. Les packages seront installés dans la base de données msdb de SQL Server et les fichiers auxiliaires et de prise en charge seront installés dans le système de fichiers. Comme les packages déployés utilisent des configurations, vous allez mettre à jour la configuration pour utiliser des nouvelles valeurs qui permettent aux packages de s'exécuter correctement dans le nouvel environnement.

 Enfin, vous allez exécuter les packages dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] à l'aide de l'utilitaire d'exécution de package.

 L'objectif de ce didacticiel est de simuler la complexité de problèmes de déploiement réels que vous pouvez rencontrer. Cependant, si vous ne pouvez pas déployer les packages sur un autre ordinateur, vous pouvez toujours effectuer ce didacticiel en installant les packages dans la base de données msdb d'une instance locale de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], puis en exécutant les packages à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] sur la même instance.

## <a name="what-you-will-learn"></a>Contenu du didacticiel
 La meilleure façon de se familiariser avec les nouveaux outils, contrôles et fonctionnalités disponibles dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] consiste à les utiliser. Ce didacticiel vous guide dans les étapes de création d'un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] puis d'ajout des packages et autres fichiers nécessaires au projet. Une fois le projet terminé, vous allez créer une application de déploiement, copier cette application sur l'ordinateur de destination, puis installer les packages sur l'ordinateur de destination.

## <a name="requirements"></a>Configuration requise
 Ce didacticiel est destiné aux utilisateurs qui sont déjà familiarisés avec les opérations fondamentales du système de fichiers, mais qui ont une exposition limitée aux nouvelles fonctionnalités disponibles dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Pour mieux comprendre [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] les concepts de base que vous allez utiliser dans ce didacticiel, il peut s’avérer utile de commencer par suivre les [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] didacticiels suivants : [exécuter l’Assistant importation et exportation SQL Server](import-export-data/start-the-sql-server-import-and-export-wizard.md) et [didacticiel SSIS : création d’un package ETL simple](../integration-services/ssis-how-to-create-an-etl-package.md).

 **Ordinateur source.** Les composants suivants doivent être installés sur l'ordinateur sur lequel vous allez créer l'application de déploiement :

-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec la base de données AdventureWorks. Pour des raisons de sécurité, les exemples de bases de données ne sont pas installés par défaut. Vous pouvez télécharger l’exemple de base de données à partir de [CodePlex](https://msftdbprodsamples.codeplex.com/releases/view/125550).

-   Vous devez disposer des autorisations pour créer et supprimer des tables dans AdventureWorks.

-   Ce didacticiel nécessite aussi les données exemple, les packages finalisés, les configurations et un fichier LisezMoi. Les fichiers correspondants à ces éléments sont installés en même temps que les exemples. Si vous ne parvenez pas à trouver les données exemple, reportez-vous à la procédure précédente et effectuez l'installation comme décrit.

-   L'environnement de développement pour les solutions décisionnelles, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].

 **Ordinateur de destination.** Les composants suivants doivent être installés sur l'ordinateur vers lequel vous déployez des packages :

-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec la base de données AdventureWorks.

-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].

-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].

-   Vous devez disposer d’autorisations pour créer et supprimer des tables dans AdventureWorks, ainsi que pour exécuter des packages dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].

-   Vous devez disposer de l’autorisation d’accès en lecture et en écriture sur la table sysssispackages dans la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] base de données système msdb.

 Si vous envisagez de déployer les packages sur le même ordinateur que celui où vous créez l'application de déploiement, ce dernier doit avoir la configuration requise pour les ordinateurs source et de destination.

 **Durée estimée pour effectuer ce didacticiel :** 2 heures.

## <a name="lessons-in-this-tutorial"></a>Leçons du didacticiel
 [Leçon 1 : préparation de la création de l’ensemble de déploiement](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md) Dans cette leçon, vous allez vous préparer à déployer une solution ETL en créant un nouveau [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projet et en ajoutant les packages et autres fichiers requis au projet.

 [Leçon 2 : création de l’ensemble de déploiement](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md) Dans cette leçon, vous allez créer un utilitaire de déploiement et vérifier que le groupe de déploiement comprend les fichiers nécessaires.

 [Leçon 3 : installation de packages](../integration-services/lesson-3-install-ssis-package.md) Dans cette leçon, vous allez copier l’ensemble de déploiement sur l’ordinateur cible, installer les packages, puis exécuter les packages.

![Icône de Integration Services (petite)](media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.

