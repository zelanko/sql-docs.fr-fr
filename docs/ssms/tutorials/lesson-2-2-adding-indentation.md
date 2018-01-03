---
title: "Ajout d’une mise en retrait | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
caps.latest.revision: "25"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5559f970627449d56863f4c9d933d5e6636f0bd2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="lesson-2-2---adding-indentation"></a>Leçon 2-2 - Ajout d’une mise en retrait
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] L’Éditeur de requête vous permet de mettre en retrait de grandes sections de code en une seule étape et de changer la longueur de mise en retrait.  
  
## <a name="indenting-code"></a>Mise en retrait du code  
  
#### <a name="to-indent-multiple-lines-of-code"></a>Pour mettre en retrait plusieurs lignes de code  
  
1.  Dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
2.  Créez une deuxième requête qui sélectionne les colonnes **BusinessEntityID**, FirstName, **MiddleName**, et **LastName** dans la table **Person** du schéma **Person** . Placez chaque colonne sur une ligne distincte afin que le code ressemble à ce qui suit :  
  
    ```  
    -- Search for a contact  
    SELECT   
    BusinessEntityID,  
    FirstName,   
    MiddleName,   
    LastName  
    FROM Person.Person  
    WHERE LastName = 'Sanchez';  
    GO  
    ```  
  
3.  Sélectionnez tout le texte de `BusinessEntityID` à `LastName`.  
  
4.  Dans la barre d'outils **Éditeur SQL** , cliquez sur **Augmenter le retrait** pour mettre en retrait toutes les lignes en même temps.  
  
#### <a name="to-change-the-default-indentation"></a>Pour modifier la mise en retrait par défaut  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Développez **Éditeur de texte**, développez **Tous les langages**, cliquez sur **Tabulations** et définissez les valeurs de mise en retrait qui conviennent. Notez que vous pouvez modifier la valeur des mises en retrait ainsi que celle des tabulations. Vous pouvez également convertir ou non les tabulations en espaces.  
  
    ![Apparence de la boîte de dialogue Onglets](./media/lesson-2-2-adding-indentation/tabsdialog.gif "Apparence de la boîte de dialogue Onglets")  
  
3.  Cliquez sur **OK**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
[Agrandissement de l'Éditeur de requête](../../tools/sql-server-management-studio/lesson-2-3-maximizing-query-editor.md)  
  
  
  
