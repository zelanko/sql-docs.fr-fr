---
title: 'Étape 2 : Convertir le projet en modèle de déploiement de projet | Microsoft Docs'
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 80964293-f1f5-4da7-b1fb-00ab8c30c1c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b75a67a24ac8ca522bddcac8f614d69f7b602dd0
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922373"
---
# <a name="lesson-6-2-convert-the-project-to-the-project-deployment-model"></a>Leçon 6-2 : Convertir le projet en modèle de déploiement de projet

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Dans cette tâche, vous utilisez l’Assistant Conversion de projet Integration Services pour convertir le projet en modèle de déploiement de projet.  
  
1.  Dans le menu **Projet**, sélectionnez **Convertir en modèle de déploiement de projet**.  
  
2.  Dans la page **Introduction** de l’**Assistant Conversion de projet Integration Services**, passez en revue les étapes, puis sélectionnez **Suivant**.  
  
3.  Dans la page **Sélectionner les packages**, dans la liste **Packages**, décochez toutes les cases à l’exception de **Lesson 6.dtsx**, puis sélectionnez **Suivant**.  
  
4.  Dans la page **Spécifier les propriétés du projet**, sélectionnez **Suivant**.  
  
5.  Dans la page **Mettre à jour la tâche d’exécution de package**, sélectionnez **Suivant**.  
  
6.  Dans la page **Sélectionner les configurations**, assurez-vous que le package **Lesson 6.dtsx** est sélectionné dans la liste **Configurations**, puis sélectionnez **Suivant**.  
  
7.  Dans la page **Créer des paramètres**, vérifiez que le package **Lesson 6.dtsx** est sélectionné.  Vérifiez que la valeur pour **Étendue** est **Package** dans la liste **Propriétés de configuration**, puis sélectionnez **Suivant**.  
  
8.  Dans la page **Configurer les paramètres**, vérifiez que les valeurs **Nom** et **Valeur** sont identiques à celles spécifiées dans la leçon 5 pour la variable et la valeur de configuration, puis sélectionnez **Suivant**.  
  
9. Dans la page **Révision**, dans le volet **Résumé**, notez que l’Assistant a utilisé les informations du fichier de configuration pour définir les **propriétés** converties.  
  
10. Sélectionnez **Convertir**.  
  
    Une fois la conversion terminée, vous voyez un message d’avertissement indiquant que les modifications ne sont pas enregistrées tant que vous n’avez pas enregistré le projet. Sélectionnez **OK** pour fermer la boîte de dialogue d’avertissement.  
  
11. Dans l’**Assistant Conversion de projet Integration Services**, sélectionnez **Fermer**.  
  
12. Dans **SQL Server Data Tools**, sélectionnez le menu **Fichier**, puis **Enregistrer** pour enregistrer le package converti.  
  
13. Sélectionnez l’onglet **Paramètres** et vérifiez que le package contient désormais un paramètre pour **VarFolderName**. Cette valeur de paramètre correspond au chemin spécifié pour le dossier **New Sample Data** dans le fichier de configuration de la leçon 5.  
  
## <a name="go-to-next-task"></a>Passer à la tâche suivante
[Étape 3 : Tester le package de la leçon 6](../integration-services/lesson-6-3-testing-the-lesson-6-package.md)  
  
  
  
