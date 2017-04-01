---
title: "&#201;tape 1 : Copie du package de la le&#231;on 2 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 4bd91402-4e37-41de-ab78-8ca5a1948a37
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# &#201;tape 1 : Copie du package de la le&#231;on 2
Dans cette tâche, vous allez créer une copie du package Lesson 2.dtsx que vous avez créé à la leçon 2. Vous pouvez également ajouter au projet le package final de la leçon 2 fourni avec le didacticiel, puis le copier à la place. Vous utiliserez cette nouvelle copie tout au long de la leçon 3.  
  
### Pour créer le package de la leçon 3  
  
1.  Si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools n’est pas encore ouvert, dans le menu **Démarrer**, pointez sur **Tous les programmes**, puis sur **Microsoft SQL Server 2012** et cliquez sur **SQL Server Data Tools**.  
  
2.  Dans le menu **Fichier**, cliquez sur **Ouvrir**, sur **Projet/Solution**, sélectionnez **Didacticiel SSIS**, cliquez sur **Ouvrir**, puis double-cliquez sur **SSIS Tutorial.sln**.  
  
3.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Lesson 2.dtsx** et choisissez **Copier**.  
  
4.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Packages SSIS** et cliquez sur **Coller**.  
  
    Par défaut, le package copié est nommé Lesson 3.dtsx.  
  
5.  Dans l’Explorateur de solutions, double-cliquez sur **Lesson 3.dtsx** pour ouvrir le package.  
  
6.  Cliquez avec le bouton droit dans l’arrière-plan de l’onglet **Flux de contrôle**, puis cliquez sur **Propriétés**.  
  
7.  Dans la fenêtre Propriétés, mettez à jour la propriété **Nom** en lui affectant la valeur **Leçon 3**.  
  
8.  Cliquez sur la zone de la propriété **ID** puis, dans la liste, cliquez sur **<Generate New ID>**.  
  
### Pour ajouter le package final de la leçon 2  
  
1.  Ouvrez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], puis le projet SSIS Tutorial.  
  
2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Packages SSIS**, puis cliquez sur **Ajouter le package existant**.  
  
3.  Dans la boîte de dialogue **Ajouter une copie des packages existants**, sous **Emplacement du package**, sélectionnez **Système de fichiers**.  
  
4.  Cliquez sur le bouton Parcourir **(...)**, accédez à **Lesson 2.dtsx** sur votre ordinateur, puis cliquez sur **Ouvrir**.  
  
    Pour télécharger tous les packages de leçons de ce didacticiel, procédez comme suit.  
  
    1.  Accédez à [Exemples de produits Integration Services](http://go.microsoft.com/fwlink/?LinkId=275027)  
  
    2.  Cliquez sur l'onglet **DOWNLOADS** (Téléchargements).  
  
    3.  Cliquez sur le fichier SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
5.  Copiez et collez le package de la leçon 3 comme décrit aux étapes 3 à 8 de la procédure précédente.  
  
## Tâche suivante de la leçon  
[Étape 2 : ajout et configuration de la journalisation](../integration-services/step-2-adding-and-configuring-logging.md)  
  
