---
title: 'Tâche 3 : Création et exécution d’un projet de qualité des données pour la correspondance | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6260e911-ea8b-4c69-a39d-d1bccd565a32
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cf5fc254aff0398b40605fdc6c568d9dc01b3a60
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37216269"
---
# <a name="task-3-creating-and-running-a-data-quality-project-for-matching"></a>Tâche 3 : Création et exécution d'un projet de qualité des données pour la mise en correspondance
  Dans cette tâche, vous allez créer un projet de qualité des données pour l'activité de correspondance, puis exécuter le processus de mise en correspondance sur les données des fournisseurs nettoyées pour supprimer les doublons.  
  
1.  Dans la page principale de **Client DQS**, cliquez sur **nouveau projet de qualité des données**.  
  
2.  Type **supprimer les doublons des fournisseurs** à partir de la **nom du projet**.  
  
3.  Sélectionnez **fournisseurs** dans la liste des bases de connaissances pour la **Base de connaissances utilisation** champ. Vous avez créé une stratégie de correspondance dans cette base de connaissances dans la leçon précédente.  
  
4.  Sélectionnez **correspondance** à partir de la **liste des activités** à partir du volet en bas à droite.  
  
     ![Nouveau projet de qualité des données - correspondance sélectionnée](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "nouveau projet de qualité des données - correspondance sélectionnée")  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans la page **Mapper** , sélectionnez **Fichier Excel** pour **Source de données**.  
  
7.  Cliquez sur **Parcourir** et sélectionnez **Cleansed Supplier List.xls**, qui est le fichier de sortie à partir de l’activité de nettoyage.  
  
8.  Carte **SupplierID** colonne source vers le **ID du fournisseur** domaine, **Supplier Name** colonne à **Supplier Name** domaine et **ContactEmailAddress** colonne à **adresse E-mail de Contact** domaine.  
  
9. Cliquez sur **suivant** pour basculer vers le **correspondance** page.  
  
10. Cliquez sur **Démarrer** pour démarrer le processus de correspondance. Vous devez obtenir des résultats semblables à ceux de la tâche précédente, car vous avez utilisé le même fichier d'entrée pour définir la stratégie de correspondance.  
  
11. Examinez tous les enregistrements correspondants et leur score de correspondance dans la zone de liste. Les résultats doivent correspondre à ceux que vous avez obtenus dans la tâche précédente. Reportez-vous aux étapes de la tâche précédente pour analyser les résultats de cette activité de correspondance.  
  
12. Cliquez sur **suivant** pour basculer vers le **exporter** page.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 4 : Exportation des résultats de l’activité de mise en correspondance dans un fichier Excel](../../2014/tutorials/task-4-exporting-the-results-from-matching-activity-to-an-excel-file.md)  
  
  
