---
title: 'Étape 1 : Copier le package de la leçon 2 | Microsoft Docs'
ms.custom: ''
ms.date: 01/04/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 4bd91402-4e37-41de-ab78-8ca5a1948a37
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 235e6e3d5ce700c230641364df548765f3be4255
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086546"
---
# <a name="lesson-3-1-copy-the-lesson-2-package"></a>Leçon 3-1 : Copier le package de la leçon 2

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Au cours de cette tâche, vous créez une copie du package Lesson 2.dtsx de la leçon 2. Si vous n’avez pas terminé la leçon 2, vous pouvez ajouter au projet le package final de la leçon 2 inclus dans ce tutoriel, puis le copier à la place. Vous allez utiliser cette nouvelle copie tout au long de la leçon 3.

## <a name="create-the-lesson-3-package"></a>Créer le package de la leçon 3

Utilisez cette procédure si vous copiez le package final de la leçon 2.  Pour copier l’exemple de la leçon 2, consultez la section suivante.

1.  Si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools n’est pas déjà ouvert, sélectionnez **Démarrer** > **Tous les programmes** > **Microsoft SQL Server 2017**, puis **SQL Server Data Tools**.

2.  Dans le menu **Fichier**, sélectionnez **Ouvrir** > **Projet/Solution**, sélectionnez le dossier **SSIS Tutorial**, sélectionnez **Ouvrir**, puis double-cliquez sur **SSIS Tutorial.sln**.

3.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Lesson 2.dtsx** et sélectionnez **Copier**.

4.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Packages SSIS** et sélectionnez **Coller**.

    Par défaut, le nom du package copié est Lesson 3.dtsx.

5.  Dans l’**Explorateur de solutions**, double-cliquez sur **Lesson 3.dtsx** pour ouvrir le package.

6.  Cliquez avec le bouton droit dans l’arrière-plan de l’aire de conception **Flux de contrôle**, puis sélectionnez **Propriétés**.

7.  Dans la fenêtre **Propriétés**, remplacez la propriété **Name** par **Lesson 3**.

8.  Sélectionnez la zone de la propriété **ID**, la flèche déroulante, puis **\<Générer un nouvel ID>** .

## <a name="add-the-completed-lesson-2-package"></a>Ajouter le package final de la leçon 2

1.  Ouvrez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools et ouvrez le projet Didacticiel SSIS.

2.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Packages SSIS**, puis sélectionnez **Ajouter le package existant**.

3.  Dans la boîte de dialogue **Ajouter une copie des packages existants**, sous **Emplacement du package**, sélectionnez **Système de fichiers**.

4.  Sélectionnez le bouton de navigation **(...)** , accédez à **Lesson 2.dtsx** sur votre ordinateur, puis sélectionnez **Ouvrir**.

5.  Copiez et collez le package de la leçon 3 en effectuant les étapes 3 à 8 décrites dans la section précédente.  
  
## <a name="go-to-next-task"></a>Passer à la tâche suivante
[Étape 2 : Ajouter et configurer la journalisation](../integration-services/lesson-3-2-adding-and-configuring-logging.md)  
  
