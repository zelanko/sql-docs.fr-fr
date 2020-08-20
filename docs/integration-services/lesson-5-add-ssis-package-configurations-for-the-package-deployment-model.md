---
description: 'Leçon 5 : Ajouter des configurations de package SSIS pour le modèle de déploiement de package'
title: 'Leçon 5 : Ajouter des configurations de package SSIS pour le modèle de déploiement de package | Microsoft Docs'
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c50bdc080ca6437cdb2291f901c429526976ab88
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466607"
---
# <a name="lesson-5-add-ssis-package-configurations-for-the-package-deployment-model"></a>Leçon 5 : Ajouter des configurations de package SSIS pour le modèle de déploiement de package

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Les configurations de package permettent de définir, en dehors de l’environnement de développement, des propriétés et des variables appliquées au moment de l’exécution. Les configurations permettent de développer des packages souples et faciles à déployer et à distribuer. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] offre les types de configuration suivants :  
  
-   Fichier de configuration XML  
  
-   Variable d’environnement  
  
-   Entrée de Registre  
  
-   Variable de package parent  
  
-   Table [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
Dans cette leçon, vous modifiez l’exemple de package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] que vous avez créé dans [Leçon 4 : Ajouter une redirection de flux d’erreur avec SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md) pour utiliser le modèle de déploiement de package et tirer parti des configurations de package. Vous pouvez également copier le package final de la leçon 4 inclus dans ce tutoriel. 

À l’aide de l’Assistant Configuration de package, vous créez une configuration XML qui met à jour la propriété **Directory** du conteneur de boucles Foreach. Vous utilisez une variable de niveau package mappée à la propriété **Directory**. Après avoir créé le fichier de configuration, vous remplacez la valeur de la variable en dehors de l’environnement de développement par le chemin du dossier New Sample Data. Lorsque vous exécutez à nouveau le package, le fichier de configuration renseigne la valeur de la variable qui, à son tour, met à jour la propriété **Directory** . Le package parcourt alors les fichiers dans le nouveau dossier de données, plutôt que dans le dossier d’origine codé en dur.  
  
> [!NOTE]
> Si ce n’est déjà fait, consultez les [prérequis de la leçon 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites).
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Copier le package de la leçon 4](../integration-services/lesson-5-1-copying-the-lesson-4-package.md)  
  
-   [Étape 2 : Activer et définir les configurations du package](../integration-services/lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
-   [Étape 3 : Modifier la valeur de configuration de la propriété Directory](../integration-services/lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
-   [Étape 4 : Tester le package de la leçon 5](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
  
-   [Étape 1 : Copier le package de la leçon 4](../integration-services/lesson-5-1-copying-the-lesson-4-package.md)  
  
  
  
