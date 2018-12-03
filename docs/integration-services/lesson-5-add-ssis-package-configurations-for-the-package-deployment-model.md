---
title: 'Leçon 5 : Ajouter des configurations de package SSIS pour le modèle de déploiement de package | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 424ec0d1cc37cab9791497ce9dede701ccdc3451
ms.sourcegitcommit: ba7fb4b9b4f0dbfe77a7c6906a1fde574e5a8e1e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52302422"
---
# <a name="lesson-5-add-ssis-package-configurations-for-the-package-deployment-model"></a>Leçon 5 : Ajouter des configurations de package SSIS pour le modèle de déploiement de package
Les configurations de package permettent de définir, en dehors de l'environnement de développement, des propriétés et des variables appliquées au moment de l'exécution. Les configurations permettent de développer des packages souples et faciles à déployer et à distribuer. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] offre les types de configuration suivants :  
  
-   Fichier de configuration XML  
  
-   Variable d'environnement  
  
-   Entrée de Registre  
  
-   Variable de package parent  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table  
  
Dans cette leçon, vous allez modifier le package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] simple que vous avez créé dans [Leçon 4 : Ajouter une redirection de flux d’erreur avec SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md) pour utiliser le modèle de déploiement de package et tirer parti des configurations de package. Vous pouvez également copier le package final de la leçon 4 inclus dans le didacticiel. À l’aide de l’Assistant Configuration de package, vous allez créer une configuration XML qui met à jour la propriété **Directory** du conteneur de boucles Foreach en utilisant une variable de niveau package mappée à la propriété Directory. Une fois que vous avez créé le fichier de configuration, vous allez modifier la valeur de la variable en dehors de l'environnement de développement et faire pointer la propriété modifiée vers un nouveau dossier de données exemple. Lorsque vous exécutez à nouveau le package, le fichier de configuration renseigne la valeur de la variable qui, à son tour, met à jour la propriété **Directory** . Ainsi, le package parcourra les fichiers du nouveau dossier de données et non les fichiers du dossier d'origine qui a été codé de manière irréversible dans le package.  
  
> [!IMPORTANT]  
> Pour suivre ce didacticiel, vous devez disposer de l'exemple de base de données **AdventureWorksDW2012** . Pour plus d'informations sur l'installation et le déploiement d' **AdventureWorksDW2012**, consultez [Reporting Services Product Samples sur CodePlex](https://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Copie du package de la leçon 4](../integration-services/lesson-5-1-copying-the-lesson-4-package.md)  
  
-   [Étape 2 : Activation et configuration des configurations de package](../integration-services/lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
-   [Étape 3 : Modification de la valeur de configuration de la propriété Directory](../integration-services/lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
-   [Étape 4 : Test de la leçon 5 du Package du didacticiel](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
  
-   [Étape 1 : Copie du package de la leçon 4](../integration-services/lesson-5-1-copying-the-lesson-4-package.md)  
  
  
  
