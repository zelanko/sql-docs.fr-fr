---
description: 'Étape 9 : Tester le package du tutoriel de la leçon 1'
title: 'Étape 9 : Tester le package du tutoriel de la leçon 1 | Microsoft Docs'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 758f5e0c312afc2a8310743f917cc00a1c43462c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88462009"
---
# <a name="lesson-1-9-test-the-lesson-1-package"></a>Leçon 1-9 : Tester le package de la leçon 1

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Dans ce tutoriel, vous avez effectué les tâches suivantes :  
  
-   création d'un nouveau projet [!INCLUDE[ssIS](../includes/ssis-md.md)] ;  
  
-   Configuration des gestionnaires de connexions pour que le package se connecte aux données sources et de destination.  
  
-   ajout d'un flux de données qui récupère les données à partir d'une source de fichier plat, effectue les transformations de recherche nécessaires sur les données et configure les données pour la destination.  
  
Votre package est maintenant terminé et prêt à être testé !
  
## <a name="check-the-package-components"></a>Vérifier les composants de package
  
Avant de tester le package, vous devez vérifier que le flux de contrôle et le flux de données dans le package de la leçon 1 contiennent les objets affichés dans les diagrammes suivants.  
  
**Flux de contrôle** 
  
![Flux de contrôle dans le package](../integration-services/media/task9lesson1control.gif "Flux de contrôle dans le package")  
  
**Flux de données**  
  
![Flux de données dans le package](../integration-services/media/task9lesson1data.gif "Flux de données dans le package")  
  
## <a name="run-the-lesson-1-package"></a>Exécuter le package de la leçon 1  
  
1.  Dans le menu **Déboguer**, sélectionnez **Démarrer le débogage**.  
  
    Le package s’exécute, ce qui se traduit par l’ajout de 1 097 lignes à la table de faits **NewFactCurrencyRate** dans **AdventureWorksDW2012**. Pour vérifier ce résultat, sélectionnez l’onglet **Flux de données**.
  
2.  Une fois l’exécution du package terminée, dans le menu **Déboguer**, sélectionnez **Arrêter le débogage**.  
  
## <a name="go-to-next-lesson"></a>Passer à la leçon suivante
[Leçon 2 : Ajouter un bouclage avec SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de projets et de packages](packages/run-integration-services-ssis-packages.md) 
  
  
  
