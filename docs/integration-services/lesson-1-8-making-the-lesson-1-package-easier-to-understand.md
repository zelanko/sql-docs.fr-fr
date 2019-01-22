---
title: 'Étape 8 : Annoter et mettre en forme le package de la leçon 1 | Microsoft Docs'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: e3751e53-77c7-47d0-8fe8-73ed1a53413a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d5890cf61593d894daf7539d324922bfcf0d8651
ms.sourcegitcommit: dd794633466b1da8ead9889f5e633bdf4b3389cd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54143629"
---
# <a name="lesson-1-8-annotate-and-format-the-lesson-1-package"></a>Leçon 1-8 : Annoter et mettre en forme le package de la leçon 1 

La configuration du package de la leçon 1 étant terminée, c’est probablement le moment de mettre un peu d’ordre dans la disposition du package. Si les formes dans les dispositions de flux de données et de contrôle sont de tailles différentes ou ne sont pas disposées uniformément, le package peut être plus difficile à comprendre.  
  
[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools fournit des outils qui facilitent la mise en forme de la disposition des packages. Les fonctionnalités de mise en forme offrent notamment la possibilité d’attribuer la même taille aux formes, de les aligner et de changer l’espace horizontal et vertical entre elles.  
  
Une autre manière d'améliorer la compréhension des fonctionnalités des packages est d'ajouter des annotations décrivant ces fonctionnalités.  
  
Au cours de cette tâche, vous exploitez les fonctionnalités de mise en forme disponibles dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools pour améliorer la disposition du flux de données et pour ajouter une annotation.  
  
## <a name="format-the-layout-of-the-data-flow"></a>Mettre en forme la disposition du flux de données  
  
1.  Si le package de la leçon 1 n’est pas encore ouvert, double-cliquez sur le fichier **Lesson 1.dtsx** dans l’**Explorateur de solutions**.  
  
2.  Sélectionnez l’onglet **Flux de données**.  
  
3.  Pour sélectionner tous les composants de flux de données à la fois, utilisez **Modifier** > **Tout sélectionner**.
  
4.  Dans le menu **Format**, sélectionnez **Uniformiser la taille**, puis sélectionnez **Les deux**.  
  
5.  Avec les objets du flux de données sélectionnés, dans le menu **Format**, sélectionnez **Aligner**, puis sélectionnez **Centrer**.  

6.  Avec les objets du flux de données sélectionnés, dans le menu **Format**, pointez sur **Espacement vertical**, puis sélectionnez **Égaliser**.  
  
## <a name="add-an-annotation-to-the-data-flow"></a>Ajouter une annotation au flux de données  
  
1.  Cliquez avec le bouton droit n’importe où sur l’arrière-plan de la zone de conception du flux de données, puis sélectionnez **Ajouter une annotation**.  
  
2.  Entrez ou collez le texte suivant dans la zone de l’annotation.  
  
        The data flow extracts data from a file, looks up values in the CurrencyKey column in the DimCurrency table and the DateKey column in the DimDate table, and writes the data to the NewFactCurrencyRate table.
  
    Pour renvoyer à la ligne le texte de la zone d’annotation, placez le curseur à l’endroit où vous souhaitez démarrer une nouvelle ligne, puis appuyez sur **Entrée**.  
  
    Si vous n’ajoutez aucun texte dans la zone de l’annotation, cette dernière disparaît quand vous cliquez en dehors.  
  
## <a name="go-to-next-task"></a>Passer à la tâche suivante
[Étape 9 : Tester le package de la leçon 1](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
  
  
