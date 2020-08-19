---
description: 'Leçon 2-1 : Copier le package de la leçon 1'
title: 'Étape 1 : Copier le package de la leçon 1 | Microsoft Docs'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 7f1616c2-2b4e-4010-be50-27d7b897403a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7a1e8c0c58c7003f14573f23e82ea8149955623
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88425251"
---
# <a name="lesson-2-1-copy-the-lesson-1-package"></a>Leçon 2-1 : Copier le package de la leçon 1

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Dans cette tâche, vous créez une copie du package **Lesson 1.dtsx**. Si vous n’avez pas effectué la leçon 1, vous pouvez utiliser le package final de la leçon 1 qui est inclus dans ce tutoriel. Vous utilisez la nouvelle copie tout au long de la leçon 2.  
  
## <a name="create-the-lesson-2-package"></a>Créer le package de la leçon 2  

Utilisez cette procédure si vous copiez la leçon 1 effectuée.  Pour copier l’exemple de leçon 1, consultez la section suivante.
  
1.  Si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools n’est pas déjà ouvert, sélectionnez **Démarrer** > **Tous les programmes** > **Microsoft SQL Server 2017**, puis **SQL Server Data Tools**.  
  
2.  Dans le menu **Fichier**, sélectionnez **Ouvrir** > **Projet/Solution**, sélectionnez le dossier **SSIS Tutorial**, sélectionnez **Ouvrir**, puis double-cliquez sur **SSIS Tutorial.sln**.  
  
3.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Lesson 1.dtsx** et sélectionnez **Copier**.  
  
4.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **SSIS Packages** et sélectionnez **Coller**.  
  
    Par défaut, le package copié est nommé **Lesson 2.dtsx**.  
  
5.  Dans l’**Explorateur de solutions**, double-cliquez sur **Lesson 2.dtsx** pour ouvrir le package.  
  
6.  Cliquez avec le bouton droit n’importe où dans l’arrière-plan de l’aire de conception **Flux de contrôle**, puis sélectionnez **Propriétés**.  
  
7.  Dans la fenêtre **Propriétés**, définissez la propriété **Nom** sur **Leçon 2**.  
  
8.  Sélectionnez la zone de la propriété **ID**, la flèche déroulante, puis **\<Generate New ID>** .  
  
## <a name="use-the-sample-lesson-1-package"></a>Utiliser l’exemple de package de la leçon 1  
  
1.  Ouvrez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools et ouvrez le projet Didacticiel SSIS.  
  
2.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Packages SSIS**, puis sélectionnez **Ajouter le package existant**.  
  
3.  Dans la boîte de dialogue **Ajouter une copie des packages existants**, sous **Emplacement du package**, sélectionnez **Système de fichiers**.  
  
4.  Sélectionnez le bouton de navigation **(...)** , accédez à **Lesson 1.dtsx** sur votre ordinateur, puis sélectionnez **Ouvrir**.  
  
5.  Copiez et collez le package de la leçon 1 selon les étapes 3 à 8 décrites dans la section précédente.  
  
## <a name="go-to-next-task"></a>Passer à la tâche suivante

[Étape 2 : Ajouter et configurer le conteneur de boucles Foreach](../integration-services/lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
