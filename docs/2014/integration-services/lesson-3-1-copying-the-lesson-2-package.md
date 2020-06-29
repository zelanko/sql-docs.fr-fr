---
title: 'Étape 1 : Copie du package de la leçon 2 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4bd91402-4e37-41de-ab78-8ca5a1948a37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9ed7db19463b7383e5b2819ada624f9a3aa51b36
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440536"
---
# <a name="step-1-copying-the-lesson-2-package"></a>Étape 1 : Copie du package de la leçon 2
  Dans cette tâche, vous allez créer une copie du package Lesson 2.dtsx que vous avez créé à la leçon 2. Vous pouvez également ajouter au projet le package final de la leçon 2 fourni avec le didacticiel, puis le copier à la place. Vous utiliserez cette nouvelle copie tout au long de la leçon 3.  
  
### <a name="to-create-the-lesson-3-package"></a>Pour créer le package de la leçon 3  
  
1.  Si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools n’est pas déjà ouvert, dans le menu **Démarrer**, pointez sur **Tous les programmes**, puis sur **Microsoft SQL Server 2012**et cliquez sur **SQL Server Data Tools**.  
  
2.  Dans le menu **Fichier** , cliquez sur **Ouvrir**, cliquez sur **Projet/Solution**, sélectionnez **Didacticiel SSIS** , cliquez sur **Ouvrir**, puis double-cliquez sur **SSIS Tutorial.sln**.  
  
3.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Lesson 2.dtsx**et choisissez **Copier**.  
  
4.  Dans Explorateur de solutions, cliquez avec le bouton droit sur **packages SSIS**, puis cliquez sur **coller**.  
  
     Par défaut, le package copié est nommé Lesson 3.dtsx.  
  
5.  Dans Explorateur de solutions, double-cliquez sur la **leçon 3. dtsx** pour ouvrir le package.  
  
6.  Cliquez avec le bouton droit dans l’arrière-plan de l’onglet **Flux de contrôle** , puis cliquez sur **Propriétés**.  
  
7.  Dans le Fenêtre Propriétés, mettez à jour la `Name` propriété avec la valeur `Lesson 3` .  
  
8.  Cliquez sur la zone de la propriété **ID** , puis dans la liste, cliquez sur **\<Generate New ID>**.  
  
### <a name="to-add-the-completed-lesson2-package"></a>Pour ajouter le package final de la leçon 2  
  
1.  Ouvrez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , puis le projet SSIS Tutorial.  
  
2.  Dans Explorateur de solutions, cliquez avec le bouton droit sur **packages SSIS**, puis cliquez sur **Ajouter un package existant**.  
  
3.  Dans la boîte de dialogue **Ajouter une copie des packages existants** , dans **emplacement du package**, sélectionnez système de **fichiers**.  
  
4.  Cliquez sur le bouton de navigation **(...)** , accédez à **Lesson 2.dtsx** sur votre ordinateur, puis cliquez sur **Ouvrir**.  
  
     Pour télécharger tous les packages de leçons de ce didacticiel, procédez comme suit.  
  
    1.  Accédez à [Exemples de produits Integration Services](https://go.microsoft.com/fwlink/?LinkId=275027)  
  
    2.  Cliquez sur l’onglet **téléchargements** .  
  
    3.  Cliquez sur le fichier SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
5.  Copiez et collez le package de la leçon 3 selon les étapes 3 à 8 décrites dans la procédure précédente.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 2 : Activation et configuration du mode d’écriture dans un journal](lesson-3-2-adding-and-configuring-logging.md)  
  
  
