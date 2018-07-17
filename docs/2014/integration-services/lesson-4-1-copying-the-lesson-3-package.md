---
title: 'Étape 1 : Copie du package de la leçon 3 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0d053786-5203-43f3-a613-27a8dd2bc44a
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 031c82bb3ebdb3843eb3f9a540728a00cd8cc903
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37329499"
---
# <a name="step-1-copying-the-lesson-3-package"></a>Étape 1 : Copie du package de la leçon 3
  Dans cette tâche, vous allez créer une copie du package Lesson 3.dtsx que vous avez créé à la leçon 3. Si vous n'avez pas terminé la leçon 3, vous pouvez également ajouter au projet le package final de la leçon 3 inclus avec le didacticiel, puis le copier pour l'utiliser. Vous allez utiliser cette nouvelle copie tout au long de la leçon 4.  
  
### <a name="to-create-the-lesson-4-package"></a>Pour créer le package de la leçon 4  
  
1.  Si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools n’est pas déjà ouvert, dans le menu **Démarrer**, pointez sur **Tous les programmes**, puis sur **Microsoft SQL Server**et cliquez sur **SQL Server Data Tools**.  
  
2.  Dans le menu **Fichier**, cliquez sur **Ouvrir**, cliquez sur **Projet/Solution**, sélectionnez **Didacticiel SSIS**, cliquez sur **Ouvrir**, puis double-cliquez sur **SSIS Tutorial.sln**.  
  
3.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Lesson 3.dtsx**et choisissez **Copier**.  
  
4.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Packages SSIS**et choisissez **Coller**.  
  
     Par défaut, le package copié est nommé Lesson 4.dtsx.  
  
5.  Dans l’Explorateur de solutions, double-cliquez sur **Lesson 4.dtsx** pour ouvrir le package.  
  
6.  Cliquez avec le bouton droit dans l’arrière-plan de l’onglet **Flux de contrôle** , puis cliquez sur **Propriétés**.  
  
7.  Dans la fenêtre Propriétés, mettez à jour le `Name` propriété `Lesson 4`.  
  
8.  Cliquez sur la zone pour le **ID** propriété, puis, dans la liste, cliquez sur  **\<générer un nouvel ID >**.  
  
### <a name="to-add-the-completed-lesson-3-package"></a>Pour ajouter le package final de la leçon 3  
  
1.  Ouvrez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , puis le projet SSIS Tutorial.  
  
2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Packages SSIS**, puis cliquez sur **Ajouter le package existant**.  
  
3.  Dans la boîte de dialogue **Ajouter une copie des packages existants** , dans **Emplacement du package**, sélectionnez **Système de fichiers**.  
  
4.  Cliquez sur le bouton de navigation **(...)** , accédez à Lesson 3.dtsx sur votre ordinateur, puis cliquez sur **Ouvrir**.  
  
     Pour télécharger tous les packages de leçons de ce didacticiel, procédez comme suit.  
  
    1.  Accédez à [Exemples de produits Integration Services](http://go.microsoft.com/fwlink/?LinkId=275027)  
  
    2.  Cliquez sur l'onglet **DOWNLOADS** (Téléchargements).  
  
    3.  Cliquez sur le fichier SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
5.  Copiez et collez le package de la leçon 3 selon les étapes 3 à 8 décrites dans la procédure précédente.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 2 : Création d’un fichier corrompu](lesson-4-2-creating-a-corrupted-file.md)  
  
  
