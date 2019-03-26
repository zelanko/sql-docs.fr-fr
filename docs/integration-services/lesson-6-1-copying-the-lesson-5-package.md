---
title: 'Étape 1 : Copier le package de la leçon 5 | Microsoft Docs'
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: a25fcc13-987e-4f3d-8f0c-76f7e6e59920
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 566c3db45d64f0ce013ed538691bd8ce6af60f0f
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58275200"
---
# <a name="lesson-6-1-copy-the-lesson-5-package"></a>Leçon 6-1 : Copier le package de la leçon 5

Au cours de cette tâche, vous créez une copie du package **Lesson 5.dtsx** de la leçon 5. Si vous n’avez pas terminé la leçon 5, vous pouvez ajouter au projet le package final de la leçon 5 inclus dans le tutoriel, puis le copier pour l’utiliser. Vous allez utiliser cette nouvelle copie tout au long de la leçon 6. 

> [!IMPORTANT]
> Après la copie du package de la leçon 5, si vous avez les packages des leçons précédentes dans votre solution, cliquez avec le bouton droit sur chaque package des leçons 1 à 5 et sélectionnez **Exclure du projet**. Quand vous avez terminé, vous devez avoir uniquement **Lesson 6.dtsx** dans votre solution.   
  
## <a name="create-the-lesson-6-package"></a>Créer le package de la leçon 6  
  
Utilisez cette procédure si vous copiez le package final de la leçon 5.  Pour copier l’exemple de la leçon 5, consultez la section suivante.

1.  Si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools n’est pas déjà ouvert, sélectionnez **Démarrer** > **Tous les programmes** > **Microsoft SQL Server 2017**, puis **SQL Server Data Tools**.

2.  Dans le menu **Fichier**, sélectionnez **Ouvrir** > **Projet/Solution**, sélectionnez le dossier **SSIS Tutorial**, sélectionnez **Ouvrir**, puis double-cliquez sur **SSIS Tutorial.sln**.

3.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Lesson 5.dtsx** et sélectionnez **Copier**.

4.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **SSIS Packages** et sélectionnez **Coller**.

    Par défaut, le nom du package copié est **Lesson 5.dtsx**.

5.  Dans l’**Explorateur de solutions**, double-cliquez sur **Lesson 5.dtsx** pour ouvrir le package

6.  Cliquez avec le bouton droit n’importe où dans l’arrière-plan de l’aire de conception **Flux de contrôle**, puis sélectionnez **Propriétés**.

7.  Dans la fenêtre **Propriétés**, remplacez la propriété **Name** par **Lesson 6**.

8.  Sélectionnez la zone de la propriété **ID**, la flèche déroulante, puis **\<Générer un nouvel ID>**.

## <a name="add-the-completed-lesson-5-package"></a>Ajouter le package final de la leçon 5

1.  Ouvrez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools et ouvrez le projet Didacticiel SSIS.

2.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Packages SSIS**, puis sélectionnez **Ajouter le package existant**.

3.  Dans la boîte de dialogue **Ajouter une copie des packages existants** , dans **Emplacement du package**, sélectionnez **Système de fichiers**.

4.  Sélectionnez le bouton de navigation **(...)**, accédez à **Lesson 5.dtsx** sur votre ordinateur, puis sélectionnez **Ouvrir**.

5.  Copiez et collez le package de la leçon 5 en effectuant les étapes 3 à 8 décrites dans la section précédente.

## <a name="go-to-next-task"></a>Passer à la tâche suivante
[Étape 2 : Convertir le projet en modèle de déploiement de projet](../integration-services/lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
