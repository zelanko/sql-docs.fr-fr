---
title: 'Tâche 3 : création et exécution d’un projet de qualité des données pour la correspondance | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6260e911-ea8b-4c69-a39d-d1bccd565a32
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: c6953214bd5e5353643cb16b75ed51ac18783256
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78171768"
---
# <a name="task-3-creating-and-running-a-data-quality-project-for-matching"></a>Tâche 3 : Création et exécution d’un projet de qualité des données pour la mise en correspondance
  Dans cette tâche, vous allez créer un projet de qualité des données pour l'activité de correspondance, puis exécuter le processus de mise en correspondance sur les données des fournisseurs nettoyées pour supprimer les doublons.

1.  Sur la page principale du **client DQS**, cliquez sur **nouveau projet de qualité des données**.

2.  Tapez **Supprimer les doublons de fournisseur** du **nom du projet**.

3.  Sélectionnez **fournisseurs** dans la liste des bases de connaissances du champ **utiliser la base de connaissances** . Vous avez créé une stratégie de correspondance dans cette base de connaissances dans la leçon précédente.

4.  Sélectionnez **correspondance** dans la **liste des activités** dans le volet inférieur droit.

     ![Nouveau projet de qualité des données - Correspondance sélectionnée](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "Nouveau projet de qualité des données - Correspondance sélectionnée")

5.  Cliquez sur **Suivant**.

6.  Dans la page **Mapper** , sélectionnez **Fichier Excel** pour **Source de données**.

7.  Cliquez sur **Parcourir** et sélectionnez **cleaned Supplier List. xls**, qui est le fichier de sortie de l’activité de nettoyage.

8.  Mappez la colonne source **RéfFournisseur** au domaine de l' **ID** de fournisseur, à la colonne **nom du fournisseur** en domaine **nom du fournisseur** et à la colonne **ContactEmailAddress** sur contacter le domaine de **messagerie** .

9. Cliquez sur **suivant** pour basculer vers la page **correspondante** .

10. Cliquez sur **Démarrer** pour démarrer le processus de correspondance. Vous devez obtenir des résultats semblables à ceux de la tâche précédente, car vous avez utilisé le même fichier d'entrée pour définir la stratégie de correspondance.

11. Examinez tous les enregistrements correspondants et leur score de correspondance dans la zone de liste. Les résultats doivent correspondre à ceux que vous avez obtenus dans la tâche précédente. Reportez-vous aux étapes de la tâche précédente pour analyser les résultats de cette activité de correspondance.

12. Cliquez sur **suivant** pour passer à la page **Exporter** .

## <a name="next-step"></a>étape suivante
 [Tâche 4 : Exportation des résultats de l’activité de mise en correspondance dans un fichier Excel](../../2014/tutorials/task-4-exporting-the-results-from-matching-activity-to-an-excel-file.md)


