---
title: 'Étape 5 : Tester le package du tutoriel de la leçon 4 | Microsoft Docs'
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 5f18df92-0248-4858-836b-c8b02f0e0439
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 2725731d216b651d310b204f4cdf6b19612ae435
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68055811"
---
# <a name="lesson-4-5-test-the-lesson-4-package"></a>Leçon 4-5 : Tester le package de la leçon 4

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Au moment de l’exécution, le fichier endommagé **Currency_BAD.txt** ne parvient pas à générer une correspondance avec la transformation de recherche Currency Key. Du fait que vous avez configuré la sortie d’erreur de la transformation de recherche Currency Key en vue de réacheminer les lignes qui ont échoué vers une nouvelle destination de lignes échouées, le composant n’échoue pas et le package s’exécute correctement. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] écrit toutes les lignes qui ont échoué dans le fichier **ErrorOutput.txt**.  
  
Au cours de cette tâche, vous testez la configuration de sortie d’erreur révisée en exécutant le package. Une fois le package exécuté, vous visualisez le contenu du fichier **ErrorOutput.txt**.  
  
> [!NOTE]  
> Pour éviter l’accumulation de lignes d’erreur dans le fichier **ErrorOutput.txt**, supprimez manuellement le contenu du fichier entre chaque exécution du package.  
  
## <a name="check-the-package-layout"></a>Vérifier la disposition du package  
Avant de tester le package, vérifiez que le flux de contrôle et le flux de données dans le package de la leçon 4 sont similaires aux diagrammes suivants : 
  
**Flux de contrôle**  
  
![Flux de contrôle dans le package](../integration-services/media/task4lesson2control.gif "Flux de contrôle dans le package")  
  
**Flux de données**  
  
![Flux de données dans le package](../integration-services/media/task5lesson5data.gif "Flux de données dans le package")  
  
## <a name="run-the-lesson-4-tutorial-package"></a>Exécuter le package du tutoriel de la leçon 4  
  
1.  Dans le menu **Déboguer**, sélectionnez **Démarrer le débogage**.  
  
2.  Une fois l’exécution du package terminée, dans le menu **Déboguer**, sélectionnez **Arrêter le débogage**.  
  
## <a name="view-the-contents-of-the-erroroutputtxt-file"></a>Voir le contenu du fichier ErrorOutput.txt  
  
Dans le Bloc-notes ou un autre éditeur de texte, ouvrez le fichier **ErrorOutput.txt**. L'ordre par défaut des colonnes est le suivant : AverageRate, CurrencyID, CurrencyDate, EndOfDateRate, ErrorCode, ErrorColumn, ErrorDescription.  
 
Toutes les lignes du fichier contiennent la valeur CurrencyID non appariée « BAD », la valeur ErrorCode -1071607778, la valeur ErrorColumn 0 et la valeur ErrorDescription dévoilant le message « Aucune correspondance de ligne trouvée au cours de la recherche ». La valeur d’ErrorColumn est 0, car l’erreur n’est pas spécifique à une colonne, mais liée à l’échec de l’opération de recherche.
  
  
## <a name="next-lesson"></a>Leçon suivante
[Leçon 5 : Ajouter des configurations de package SSIS pour le modèle de déploiement de package](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
