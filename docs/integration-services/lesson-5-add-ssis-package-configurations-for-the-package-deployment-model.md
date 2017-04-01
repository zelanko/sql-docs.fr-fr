---
title: "Le&#231;on 5 : Ajouter des configurations de package SSIS pour le mod&#232;le de d&#233;ploiement de package | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# Le&#231;on 5 : Ajouter des configurations de package SSIS pour le mod&#232;le de d&#233;ploiement de package
Les configurations de package permettent de définir, en dehors de l'environnement de développement, des propriétés et des variables appliquées au moment de l'exécution. Les configurations permettent de développer des packages souples et faciles à déployer et à distribuer. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] offre les types de configuration suivants :  
  
-   Fichier de configuration XML  
  
-   Variable d'environnement  
  
-   Entrée de Registre  
  
-   Variable de package parent  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table  
  
Dans cette leçon, vous allez modifier le package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] simple que vous avez créé dans [Leçon 4 : Ajouter une redirection de flux d’erreur avec SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md) pour utiliser le modèle de déploiement de package et tirer parti des configurations de package. Vous pouvez également copier le package final de la leçon 4 inclus dans le didacticiel. À l’aide de l’Assistant Configuration de package, vous allez créer une configuration XML qui met à jour la propriété **Directory** du conteneur de boucles Foreach en utilisant une variable de niveau package mappée à la propriété Directory. Une fois que vous avez créé le fichier de configuration, vous allez modifier la valeur de la variable en dehors de l'environnement de développement et faire pointer la propriété modifiée vers un nouveau dossier de données exemple. Quand vous réexécutez le package, le fichier de configuration renseigne la valeur de la variable qui, à son tour, met à jour la propriété **Directory**. Ainsi, le package parcourra les fichiers du nouveau dossier de données et non les fichiers du dossier d'origine qui a été codé de manière irréversible dans le package.  
  
> [!IMPORTANT]  
> Pour suivre ce didacticiel, vous devez disposer de l'exemple de base de données **AdventureWorksDW2012** . Pour plus d'informations sur l'installation et le déploiement d' **AdventureWorksDW2012**, consultez [Reporting Services Product Samples sur CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## Tâches de la leçon  
Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Copie du package de la leçon 4](../integration-services/step-1-copying-the-lesson-4-package.md)  
  
-   [Étape 2 : activation et configuration des configurations de package](../integration-services/step-2-enabling-and-configuring-package-configurations.md)  
  
-   [Étape 3 : modification de la valeur de configuration de la propriété Directory](../integration-services/step-3-modifying-the-directory-property-configuration-value.md)  
  
-   [Étape 4 : Test de la leçon 5 du Package du didacticiel](../integration-services/step-4-testing-the-lesson-5-tutorial-package.md)  
  
## Démarrer la leçon  
  
-   [Étape 1 : Copie du package de la leçon 4](../integration-services/step-1-copying-the-lesson-4-package.md)  
  
  
  
