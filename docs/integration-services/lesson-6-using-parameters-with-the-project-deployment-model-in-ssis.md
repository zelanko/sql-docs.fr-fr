---
title: 'Leçon 6 : Utiliser des paramètres avec le modèle de déploiement de projet dans SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f6370319091d4326adbe2d11d1f92e19cd88695a
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71282648"
---
# <a name="lesson-6-use-parameters-with-the-project-deployment-model-in-ssis"></a>Leçon 6 : Utiliser des paramètres avec le modèle de déploiement de projet dans SSIS

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



SQL Server 2012 a introduit un nouveau modèle de déploiement qui permet de déployer vos projets sur le serveur Integration Services. Le serveur Integration Services vous permet de gérer et d'exécuter les packages, et de configurer leurs valeurs d'exécution.  
  
Dans cette leçon, vous modifiez le package que vous avez créé dans la [Leçon 5 : Ajouter des configurations de package SSIS pour le modèle de déploiement de package](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) pour utiliser le modèle de déploiement de projet. Vous remplacerez la valeur de configuration par un paramètre pour spécifier l'emplacement des exemples de données. Vous pouvez également copier le package final de la leçon 5 inclus dans le didacticiel.  
  
À l’aide de l’Assistant Configuration de projet Integration Services, vous convertissez le projet en modèle de déploiement de projet. Ce modèle utilise un paramètre plutôt qu’une valeur de configuration pour définir la propriété Directory. Cette leçon couvre partiellement les étapes que vous suivriez pour convertir les packages SSIS existants en nouveau modèle de déploiement de projet.  
  
Quand vous réexécutez le package, le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] utilise le paramètre pour renseigner la valeur de la variable. À son tour, la variable met à jour que la propriété Directory. Le package effectue une itération dans les fichiers du dossier de données spécifié par le nouveau paramètre.  
  
> [!NOTE]
> Si ce n’est déjà fait, consultez les [prérequis de la leçon 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites).
    
## <a name="lesson-tasks"></a>Tâches de la leçon  
Cette leçon contient les tâches suivantes :  
  
1.  [Étape 1 : Copier le package de la leçon 5](../integration-services/lesson-6-1-copying-the-lesson-5-package.md)  
  
2.  [Étape 2 : Convertir un projet en modèle de déploiement de projet](../integration-services/lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [Étape 3 : Tester le package de la leçon 6](../integration-services/lesson-6-3-testing-the-lesson-6-package.md)  
  
4.  [Étape 4 : Déployer le package de la leçon 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
[Étape 1 : Copier le package de la leçon 5](../integration-services/lesson-6-1-copying-the-lesson-5-package.md)  
  
