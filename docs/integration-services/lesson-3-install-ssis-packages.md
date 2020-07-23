---
title: 'Leçon 3 : Installer des packages SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 87bc4d82-39d8-424f-886f-98cf1e4bb07a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4db3158c378d32dd472a9845e785be95130780b6
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922162"
---
# <a name="lesson-3-install-ssis-packages"></a>Leçon 3 : Installer des packages SSIS

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]


Dans la [Leçon 2 : Créer l’application de déploiement dans SSIS](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md), vous avez créé un utilitaire de déploiement et l’application de déploiement qui contient les éléments que vous devez installer comme packages sur un autre ordinateur. Vous avez vérifié également la liste de fichiers dans l'application de déploiement et examiné le contenu du fichier de manifeste créé lorsque vous avez créé l'utilitaire de déploiement.  
  
Dans cette leçon, vous allez copier l'application de déploiement dans l'ordinateur de destination et exécuter l'Assistant Installation de package pour installer les packages, les dépendances de package et les fichiers annexes sur cet ordinateur. Les packages seront installés dans la base de données **msdb**[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les autres éléments seront installés dans le système de fichiers. Une fois le package installé, vous allez tester le déploiement en exécutant les packages à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] à l'aide de l'utilitaire d'exécution de package.  
  
**Durée estimée pour effectuer cette leçon :** 30 minutes  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Copie du bundle de déploiement](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
-   [Étape 2 : Exécution de l’Assistant Installation de package](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
-   [Étape 3 : Test des packages déployés](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
[Étape 1 : Copie du bundle de déploiement](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
  
  
