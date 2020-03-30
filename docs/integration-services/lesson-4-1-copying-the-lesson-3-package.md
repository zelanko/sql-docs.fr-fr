---
title: 'Étape 1 : Copier le package de la leçon 3 | Microsoft Docs'
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 0d053786-5203-43f3-a613-27a8dd2bc44a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5fb38e4be2b7d7c780dae3ee819e146958541c9f
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71295966"
---
# <a name="lesson-4-1-copy-the-lesson-3-package"></a>Leçon 4-1 : Copier le package de la leçon 3

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Au cours de cette tâche, vous créez une copie du package Lesson 3.dtsx de la leçon 3. Si vous n’avez pas terminé la leçon 3, vous pouvez ajouter au projet le package final de la leçon 3 inclus dans le tutoriel, puis le copier pour l’utiliser. Vous allez utiliser cette nouvelle copie tout au long de la leçon 4.  
  
## <a name="create-the-lesson-4-package"></a>Créer le package de la leçon 4  
  
Utilisez cette procédure si vous copiez le package final de la leçon 3.  Pour copier l’exemple de la leçon 3, consultez la section suivante.

1.  Si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools n’est pas déjà ouvert, sélectionnez **Démarrer** > **Tous les programmes** > **Microsoft SQL Server 2017**, puis **SQL Server Data Tools**.

2.  Dans le menu **Fichier**, sélectionnez **Ouvrir** > **Projet/Solution**, sélectionnez le dossier **SSIS Tutorial**, sélectionnez **Ouvrir**, puis double-cliquez sur **SSIS Tutorial.sln**.

3.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Lesson 3.dtsx** et sélectionnez **Copier**.

4.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **SSIS Packages** et sélectionnez **Coller**.

    Par défaut, le nom du package copié est **Lesson 4.dtsx**.

5.  Dans l’**Explorateur de solutions**, double-cliquez sur **Lesson 4.dtsx** pour ouvrir le package.

6.  Cliquez avec le bouton droit n’importe où dans l’arrière-plan de l’aire de conception **Flux de contrôle**, puis sélectionnez **Propriétés**.

7.  Dans la fenêtre **Propriétés**, remplacez la propriété **Name** par **Lesson 4**.

8.  Sélectionnez la zone de la propriété **ID**, la flèche déroulante, puis **\<Générer un nouvel ID>** .

## <a name="add-the-completed-lesson-3-package"></a>Ajouter le package final de la leçon 3

1.  Ouvrez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools et ouvrez le projet Didacticiel SSIS.

2.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Packages SSIS**, puis sélectionnez **Ajouter le package existant**.

3.  Dans la boîte de dialogue **Ajouter une copie des packages existants** , dans **Emplacement du package**, sélectionnez **Système de fichiers**.

4.  Sélectionnez le bouton de navigation **(...)** , accédez à **Lesson 3.dtsx** sur votre ordinateur, puis sélectionnez **Ouvrir**.

5.  Copiez et collez le package de la leçon 3 en effectuant les étapes 3 à 8 décrites dans la section précédente.

  
## <a name="go-to-next-task"></a>Passer à la tâche suivante  
[Étape 2 : Créer un fichier endommagé](../integration-services/lesson-4-2-creating-a-corrupted-file.md)  
  
