---
title: 'Étape 2 : Convertir le projet dans le modèle de déploiement de projet | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 80964293-f1f5-4da7-b1fb-00ab8c30c1c5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1ba6dcb7052fed3d209dd87f55789a99df24116c
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58385352"
---
# <a name="step-2-converting-the-project-to-the-project-deployment-model"></a>Étape 2 : Conversion du projet en modèle de déploiement de projet
  Dans cette tâche, vous allez utiliser l'Assistant Conversion de projet Integration Services pour convertir le projet en modèle de déploiement de projet.  
  
### <a name="converting-the-project-to-the-project-deployment-model"></a>Conversion du projet en modèle de déploiement de projet  
  
1.  Dans le menu Projet, cliquez sur Convertir en modèle de déploiement de projet.  
  
2.  Dans la page d'introduction de l'Assistant Conversion de projet Integration Services, passez en revue les étapes, puis cliquez sur Suivant.  
  
3.  Dans la page Sélectionner les packages, dans la liste Packages, décochez toutes les cases à l'exception de Lesson 6.dtsx, puis cliquez sur Suivant.  
  
4.  Dans la page Spécifier les propriétés du projet, cliquez sur Suivant.  
  
5.  Dans la page Mettre à jour la tâche d'exécution de package, cliquez sur Suivant.  
  
6.  Dans la page Sélectionner les configurations, assurez-vous que le package Lesson 6.dtsx est sélectionné dans la liste Configurations, puis cliquez sur Suivant.  
  
7.  Dans la page Créer des paramètres, assurez-vous que le package Lesson 6.dtsx est sélectionné et qu'Étendue est définie sur Package, dans la liste Propriétés de configuration, puis cliquez sur Suivant.  
  
8.  Dans la page Configurer les paramètres, vérifiez que les valeurs Nom et Valeur sont identiques à celles spécifiées dans la leçon 5 pour la variable et la valeur de configuration, puis cliquez sur Suivant.  
  
9. Dans la page Révision, dans le volet Résumé, notez que l'Assistant a utilisé les informations du fichier de configuration pour définir les propriétés à convertir.  
  
10. Cliquez sur Convertir.  
  
     Lorsque la conversion est terminée, un message avertit que les modifications ne sont pas enregistrées tant que le projet n'est pas enregistré dans Visual Studio. Cliquez sur OK dans la boîte de dialogue d'avertissement.  
  
11. Dans l'Assistant Conversion de projet Integration Services, cliquez sur Fermer.  
  
12. Dans SQL Server Data Tools, cliquez sur le menu Fichier, puis cliquez sur Enregistrer pour enregistrer le package converti.  
  
13. Cliquez sur l'onglet Paramètres et vérifiez que le package contient désormais un paramètre pour VarFolderName et que la valeur est le même chemin d'accès que celui spécifié pour le dossier New Sample Data du fichier de configuration de la leçon 5.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 3 : Test du Package de la leçon 6](lesson-6-3-testing-the-lesson-6-package.md)  
  
  
