---
title: 'Tâche 17 : Examiner de nettoyage DQS projet créé par le package SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 63d715ae86464a3d9411296fe8ffdfab155bab38
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308839"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a>Tâche 17 : Examiner le projet de nettoyage DQS créé par le package SSIS
  Dans cette tâche, vous allez ouvrir le projet DQS créé par le package SSIS dans le client DQS, vous allez examiner les résultats du processus de nettoyage, et vous allez éventuellement effectuer un nettoyage interactif, puis exporter les résultats.  
  
1.  Lancez **Data Quality Client**.  
  
2.  Cliquez sur **analyse des activités** dans le **Administration** volet.  
  
3.  Trier la liste selon **l’heure de début de l’activité** pour afficher le dernier enregistrement.  
  
4.  Notez que vous voyez un nom du projet dans le format suivant : **CleanseAndCurate.Cleanse Supplier Data.GUID**.  
  
     ![Projet de nettoyage DQS créé par le Package SSIS](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "projet de nettoyage DQS créé par le Package SSIS")  
  
5.  Notez que la valeur dans le **est Active** champ est **Active**.  
  
6.  Cliquez sur **Profiler** onglet dans le volet inférieur pour afficher les statistiques du Générateur de profils pour l’activité de nettoyage effectué le package SSIS.  
  
7.  Cliquez sur **fermer** pour fermer la **Administration** écran.  
  
8.  Dans la page principale de **Client DQS**, cliquez sur **ouvrir projet de qualité des données** dans le **projets de qualité des données** volet.  
  
9. Dans la liste des projets, sélectionnez le projet créé par le composant de nettoyage DQS SSIS. Le nom du projet doit être au format : **CleanseAndCurate.Cleanse Supplier Data.GUID (en rouge)**. Vous devrez peut-être trier la liste selon **Date de création de** colonne et recherchez le dernier enregistrement.  
  
10. Cliquez sur **Suivant**.  
  
11. Le **gérer et afficher les résultats** page doit vous être familière à partir du nettoyage interactif que vous l’avez fait précédemment dans ce didacticiel.  
  
12. Examinez les résultats du nettoyage. Vous pouvez également effectuer le nettoyage interactif et exporter les résultats vers un fichier Excel ou une base de données, dans la page suivante.  
  
13. Cliquez sur **Suivant**. Dans ce **exporter** page, vous pouvez exporter les résultats vers un fichier excel, fichier CSV, ou à une base de données SQL.  
  
14. Cliquez sur **Terminer** pour terminer l’activité.  
  
15. Dans la page principale de **Client DQS**, cliquez sur **analyse des activités** dans le **Administration** volet.  
  
16. Notez que la valeur de **IsActive** champ pour le projet est **terminé** maintenant.  
  
## <a name="next-step"></a>Étape suivante  
 [Conclusion](../../2014/tutorials/conclusion.md)  
  
  
