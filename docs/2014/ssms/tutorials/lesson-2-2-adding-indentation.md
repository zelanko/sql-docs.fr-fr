---
title: Ajout d’une mise en retrait | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
caps.latest.revision: 24
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a81ee88e551e45989d32fbd9f71623444a737ef2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143398"
---
# <a name="adding-indentation"></a>Ajout d'une mise en retrait
  L'Éditeur de requête vous permet de mettre en retrait de grandes sections de code en une seule étape et de modifier la longueur de mise en retrait.  
  
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
  
     ![Apparence de la boîte de dialogue Onglets](media/tabsdialog.gif "Apparence de la boîte de dialogue Onglets")  
  
3.  Cliquez sur **OK**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Agrandissement de l'Éditeur de requête](lesson-2-3-maximizing-query-editor.md)  
  
  