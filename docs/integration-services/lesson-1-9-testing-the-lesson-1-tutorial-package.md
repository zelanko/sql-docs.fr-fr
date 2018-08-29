---
title: 'Étape 9 : Test du package du didacticiel de la leçon 1 | Microsoft Docs'
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 842f9b1b2572183bc222749e7d0e850d5cb76ae9
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40406508"
---
# <a name="lesson-1-9---testing-the-lesson-1-tutorial-package"></a>Leçon 1-9 : Test du package du didacticiel de la leçon 1
Au cours de cette leçon, vous allez effectuer les tâches suivantes :  
  
-   création d'un nouveau projet [!INCLUDE[ssIS](../includes/ssis-md.md)] ;  
  
-   configuration des gestionnaires de connexions dont le package a besoin pour se connecter aux données sources et de destination ;  
  
-   ajout d'un flux de données qui récupère les données à partir d'une source de fichier plat, effectue les transformations de recherche nécessaires sur les données et configure les données pour la destination.  
  
Le package est à présent terminé. Il est temps de le tester.  
  
## <a name="checking-the-package-layout"></a>Vérification de la disposition du package  
Avant de tester le package, vous devez vérifier que le flux de contrôle et le flux de données dans le package de la leçon 1 contiennent les objets affichés dans les diagrammes suivants.  
  
**Flux de contrôle**  
  
![Flux de contrôle dans le package](../integration-services/media/task9lesson1control.gif "Flux de contrôle dans le package")  
  
**Flux de données**  
  
![Flux de données dans le package](../integration-services/media/task9lesson1data.gif "Flux de données dans le package")  
  
### <a name="to-run-the-lesson-1-tutorial-package"></a>Pour exécuter le package du didacticiel de la leçon 1  
  
1.  Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.  
  
    Le package s'exécute et 1 097 lignes sont ajoutées à la table de faits **FactCurrency** de la base de données **AdventureWorksDW2012**.  
  
2.  Une fois l'exécution du package terminée, dans le menu **Déboguer** , cliquez sur **Arrêter le débogage**.  
  
## <a name="next-lesson"></a>Leçon suivante  
[Leçon 2 : Ajout d’un bouclage avec SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a> Voir aussi  
[Exécution de projets et de packages](packages/run-integration-services-ssis-packages.md) 
  
  
  
