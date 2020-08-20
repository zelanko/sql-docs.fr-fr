---
description: 'Leçon 4 : Ajouter une redirection de flux d’erreurs avec SSIS'
title: 'Leçon 4 : Ajouter une redirection de flux d’erreurs avec SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d7ef0a6862e334221fd497a5adc44ffd0ab7990d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466573"
---
# <a name="lesson-4-add-error-flow-redirection-with-ssis"></a>Leçon 4 : Ajouter une redirection de flux d’erreurs avec SSIS

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Pour traiter les erreurs qui risquent de se produire dans le processus de transformation, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] vous permet de décider par composant et par colonne comment traiter les données que [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ne peut pas transformer. Vous pouvez choisir d’ignorer un échec dans certaines colonnes, de rediriger dans sa totalité la ligne qui a échoué ou de faire échouer le composant. Par défaut, les composants de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sont configurés pour échouer lorsque des erreurs se produisent. Le composant en échec entraîne à son tour l’échec du package et l’arrêt du traitement.  
  
Au lieu de laisser les échecs arrêter l’exécution du package, vous pouvez configurer et gérer les erreurs de traitement potentielles quand elles se produisent. Une option consiste à ignorer les échecs complètement afin que votre package s’exécute toujours correctement. Vous pouvez également rediriger la ligne qui a échoué vers un autre chemin de traitement, où vous pouvez rendre persistantes les données et l’erreur, puis les examiner ou les retraiter.  
  
Au cours de cette leçon, vous allez créer une copie du package que vous avez développé dans [Leçon 3 : Ajouter la journalisation avec SSIS](../integration-services/lesson-3-add-logging-with-ssis.md). Avec ce nouveau package, vous allez créer une version endommagée de l’un des exemples de fichiers de données. Le fichier endommagé entraîne une erreur de traitement lors de l’exécution du package.  
  
Pour gérer les données d’erreur, vous ajoutez et configurez une destination de fichier plat qui écrit toutes les lignes ayant échoué dans un fichier d’erreur. 
  
Avant que [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] n’écrive les données d’erreur dans le fichier, vous incluez un composant Script qui obtient les descriptions d’erreur. Vous reconfigurez ensuite la transformation Lookup Currency Key pour rediriger vers la transformation Script toutes les données qui n’ont pas pu être traitées.  
  
## <a name="prerequisites"></a>Conditions préalables

> [!NOTE]
> Si ce n’est déjà fait, consultez les [prérequis de la leçon 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites).
 
## <a name="lesson-task"></a>Tâches de la leçon
Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Copier le package de la leçon 3](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [Étape 2 : Créer un fichier endommagé](../integration-services/lesson-4-2-creating-a-corrupted-file.md)  
  
-   [Étape 3 : Ajouter une redirection de flux d’erreurs](../integration-services/lesson-4-3-adding-error-flow-redirection.md)  
  
-   [Étape 4 : Ajouter une destination de fichier plat](../integration-services/lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [Étape 5 : Tester le package du tutoriel de la leçon 4](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
[Étape 1 : Copier le package de la leçon 3](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
  
  
