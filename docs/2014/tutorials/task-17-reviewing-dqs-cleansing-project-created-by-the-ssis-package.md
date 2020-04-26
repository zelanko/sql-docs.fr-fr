---
title: 'Tâche 17 : examen du projet de nettoyage DQS créé par le package SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 285eae7ea20d5919fa73bd0d514c755fe73d9de0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65484715"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a>Tâche 17 : Examen du projet de nettoyage DQS créé par le package SSIS
  Dans cette tâche, vous allez ouvrir le projet DQS créé par le package SSIS dans le client DQS, vous allez examiner les résultats du processus de nettoyage, et vous allez éventuellement effectuer un nettoyage interactif, puis exporter les résultats.  
  
1.  Lancez **Data Quality client**.  
  
2.  Cliquez sur **analyse des activités** dans le volet **administration** .  
  
3.  Triez la liste en fonction de l' **heure de début** de l’activité pour afficher le dernier enregistrement.  
  
4.  Notez que vous voyez un nom du projet au format suivant : **CleanseAndCurate. Clean do Supplier Data. Guid**.  
  
     ![Projet de nettoyage DQS créé par le package SSIS](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "Projet de nettoyage DQS créé par le package SSIS")  
  
5.  Notez que la valeur du champ **est active** est **active**.  
  
6.  Cliquez sur l’onglet **Générateur de profils** dans le volet inférieur pour afficher les statistiques du profileur pour l’activité de nettoyage effectuée par le package SSIS.  
  
7.  Cliquez sur **Fermer** pour fermer l’écran **administration** .  
  
8.  Dans la page principale du **client DQS**, cliquez sur **ouvrir le projet de qualité des données** dans le volet projets de qualité des **données** .  
  
9. Dans la liste des projets, sélectionnez le projet créé par le composant de nettoyage DQS SSIS. Le nom du projet doit être au format : **CleanseAndCurate. Clean do Supplier Data. Guid (en couleur rouge)**. Vous devrez peut-être trier la liste en fonction de la colonne **Date de création** et rechercher le dernier enregistrement.  
  
10. Cliquez sur **Suivant**.  
  
11. La page **gérer et afficher les résultats** doit vous être familière du nettoyage interactif que vous avez fait précédemment dans ce didacticiel.  
  
12. Examinez les résultats du nettoyage. Vous pouvez également effectuer le nettoyage interactif et exporter les résultats vers un fichier Excel ou une base de données, dans la page suivante.  
  
13. Cliquez sur **Suivant**. Dans cette page **Exporter** , vous pouvez exporter les résultats vers un fichier Excel, un fichier CSV ou une base de données SQL.  
  
14. Cliquez sur **Terminer** pour terminer l’activité.  
  
15. Dans la page principale du **client DQS**, cliquez sur **analyse des activités** dans le volet **administration** .  
  
16. Notez que la valeur du champ **IsActive** pour le projet est maintenant **terminée** .  
  
## <a name="next-step"></a>étape suivante  
 [Conclusion](../../2014/tutorials/conclusion.md)  
  
  
