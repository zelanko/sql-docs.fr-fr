---
title: 'Leçon 5 : ajout de configurations de package pour le modèle de déploiement de package | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 25922725e202bc7b38e2c6141a097df1af119ed2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "62767416"
---
# <a name="lesson-5-adding-package-configurations-for-the-package-deployment-model"></a>Leçon 5 : Ajout de configurations de package pour le modèle de déploiement de package
  Les configurations de package permettent de définir, en dehors de l'environnement de développement, des propriétés et des variables appliquées au moment de l'exécution. Les configurations permettent de développer des packages souples et faciles à déployer et à distribuer. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] offre les types de configuration suivants :  
  
-   Fichier de configuration XML  
  
-   Variable d’environnement  
  
-   Entrée de Registre  
  
-   Variable de package parent  
  
-   Table [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
 Dans cette leçon, vous allez modifier le package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] simple que vous avez créé dans [Lesson 4: Adding Error Flow Redirection](lesson-4-add-error-flow-redirection-with-ssis.md) pour utiliser le modèle de déploiement de package et tirer parti des configurations de package. Vous pouvez également copier le package final de la leçon 4 inclus dans le didacticiel. À l'aide de l'Assistant Configuration de package, vous allez créer une configuration XML qui met à jour la propriété `Directory` du conteneur de boucles Foreach en utilisant une variable de niveau package mappée à la propriété Directory. Une fois que vous avez créé le fichier de configuration, vous allez modifier la valeur de la variable en dehors de l'environnement de développement et faire pointer la propriété modifiée vers un nouveau dossier de données exemple. Lorsque vous réexécutez le package, le fichier de configuration remplit la valeur de la variable, et la variable à son tour met à jour `Directory` la propriété. Ainsi, le package parcourra les fichiers du nouveau dossier de données et non les fichiers du dossier d'origine qui a été codé de manière irréversible dans le package.  
  
> [!IMPORTANT]  
>  Pour suivre ce didacticiel, vous devez disposer de l'exemple de base de données **AdventureWorksDW2012** . Pour plus d'informations sur l'installation et le déploiement d' **AdventureWorksDW2012**, consultez [Reporting Services Product Samples sur CodePlex](https://go.microsoft.com/fwlink/?LinkID=526910).  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Copie du package de la leçon 4](lesson-5-1-copying-the-lesson-4-package.md)  
  
-   [Étape 2 : Activation et configuration des configurations de package](lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
-   [Étape 3 : Modification de la valeur de configuration de la propriété Directory](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
-   [Étape 4 : Test du package du tutoriel de la leçon 5](lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
  
-   [Étape 1 : Copie du package de la leçon 4](lesson-5-1-copying-the-lesson-4-package.md)  
  
  
