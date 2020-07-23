---
title: 'Étape 4 : Tester le package du tutoriel de la leçon 2 | Microsoft Docs'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 0e8c0a25-8f79-41df-8ed2-f82a74b129cd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 11d621289dbff6e6940df75e13f07af287c4e9ef
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922247"
---
# <a name="lesson-2-4-test-the-lesson-2-tutorial-package"></a>Leçon 2-4 : Tester le package du tutoriel de la leçon 2

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Une fois le conteneur de boucles Foreach et le gestionnaire de connexions de fichiers plats configurés, le package Lesson 2 peut parcourir les 14 fichiers plats dans le dossier Sample Data. Chaque fois qu’un nom de fichier correspond au critère spécifié, le conteneur de boucles Foreach remplace la variable définie par l’utilisateur par ce nom de fichier. Cette variable met à jour à son tour la propriété ConnectionString du gestionnaire de connexions de fichiers plats, qui se connecte à ce fichier plat. Le conteneur de boucles Foreach exécute alors la tâche de flux de données inchangée sur les données de ce fichier plat.  
  
> [!NOTE]  
> Si vous avez exécuté le package de la leçon 1, vous devez supprimer les enregistrements de la table dbo.NewFactCurrencyRate de la base de données AdventureWorksDW2012 avant d’exécuter le package à partir de cette leçon. La leçon 2 tente d’insérer des enregistrements déjà insérés dans la leçon 1, ce qui provoque une erreur.  
  
## <a name="check-the-package-layout"></a>Vérifier la disposition du package  
Avant de tester le package, vérifiez que le flux de contrôle et le flux de données dans le package de la leçon 2 contiennent les objets affichés dans les diagrammes suivants. Le flux de données de la leçon 2 est identique à celui de la leçon 1.  
  
**Flux de contrôle**  
  
![Flux de contrôle dans le package](../integration-services/media/task4lesson2control.gif "Flux de contrôle dans le package")  
  
**Flux de données**  
  
![Flux de données dans le package](../integration-services/media/task9lesson1data.gif "Flux de données dans le package")  
  
## <a name="test-the-lesson-2-tutorial-package"></a>Tester le package du tutoriel de la leçon 2  
  
1.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Lesson 2.dtsx**, puis sélectionnez **Exécuter le package**.  
  
    Le package s’exécute. Vous pouvez vérifier l’état de chaque boucle dans la fenêtre **Sortie** ou le consulter sous l’onglet **Progression**. Par exemple, vous pouvez voir que 1 097 lignes ont été ajoutées à la table de destination à partir du fichier Currency_VEB.txt.  
  
2.  Une fois l’exécution du package terminée, dans le menu **Déboguer**, sélectionnez **Arrêter le débogage**.  
  
## <a name="go-to-next-lesson"></a>Passer à la leçon suivante  
[Leçon 3 : Ajouter la journalisation avec SSIS](../integration-services/lesson-3-add-logging-with-ssis.md)  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de projets et de packages](../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  
  

