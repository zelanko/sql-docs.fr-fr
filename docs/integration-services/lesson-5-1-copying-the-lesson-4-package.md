---
description: 'Leçon 5-1 : Copier le package de la leçon 4'
title: 'Étape 1 : Copier le package de la leçon 4 | Microsoft Docs'
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 8aa7d690-4649-4c0a-ac6f-9504637ee426
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 95eca1c1b598387d7ff2c9bab688c022f76e73c2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88345605"
---
# <a name="lesson-5-1-copy-the-lesson-4-package"></a>Leçon 5-1 : Copier le package de la leçon 4

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Au cours de cette tâche, vous créez une copie du package **Lesson 4.dtsx** de la leçon 4. Si vous n’avez pas terminé la leçon 4, vous pouvez ajouter au projet le package final de la leçon 4 inclus dans le tutoriel, puis le copier pour l’utiliser. Vous allez utiliser cette nouvelle copie tout au long de la leçon 5.  
  
## <a name="create-the-lesson-5-package"></a>Créer le package de la leçon 5  
  
Utilisez cette procédure si vous copiez le package final de la leçon 4.  Pour copier l’exemple de la leçon 4, consultez la section suivante.

1.  Si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools n’est pas déjà ouvert, sélectionnez **Démarrer** > **Tous les programmes** > **Microsoft SQL Server 2017**, puis **SQL Server Data Tools**.

2.  Dans le menu **Fichier**, sélectionnez **Ouvrir** > **Projet/Solution**, le dossier **SSIS Tutorial**, puis **Ouvrir**.  Double-cliquez ensuite sur **SSIS Tutorial.sln**.

3.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Lesson 4.dtsx** et sélectionnez **Copier**.

4.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **SSIS Packages** et sélectionnez **Coller**.

    Par défaut, le nom du package copié est **Lesson 4.dtsx**.

5.  Dans l’**Explorateur de solutions**, double-cliquez sur **Lesson 4.dtsx** pour ouvrir le package.

6.  Cliquez avec le bouton droit n’importe où dans l’arrière-plan de l’aire de conception **Flux de contrôle**, puis sélectionnez **Propriétés**.

7.  Dans la fenêtre **Propriétés**, remplacez la propriété **Name** par **Lesson 5**.

8.  Sélectionnez la zone de la propriété **ID**, la flèche déroulante, puis **\<Generate New ID>** .

## <a name="add-the-completed-lesson-4-package"></a>Ajouter le package final de la leçon 4

1.  Ouvrez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools et ouvrez le projet Didacticiel SSIS.

2.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Packages SSIS**, puis sélectionnez **Ajouter le package existant**.

3.  Dans la boîte de dialogue **Ajouter une copie des packages existants** , dans **Emplacement du package**, sélectionnez **Système de fichiers**.

4.  Sélectionnez le bouton de navigation **(...)** , accédez à **Lesson 4.dtsx** sur votre ordinateur, puis sélectionnez **Ouvrir**.

5.  Copiez et collez le package de la leçon 4 en effectuant les étapes 3 à 8 décrites dans la section précédente.
  
## <a name="go-to-next-task"></a>Passer à la tâche suivante  
[Étape 2 : Activer et définir les configurations du package](../integration-services/lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
