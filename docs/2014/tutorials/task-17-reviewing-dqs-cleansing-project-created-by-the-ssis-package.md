---
title: 'Tâche 17 : Examen de nettoyage DQS projet créé par le package SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 4653ce040e19b82b9e70daa7ebfc02047d71b194
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56024440"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a>Tâche 17 : Examiner le projet de nettoyage DQS créé par le package SSIS
  Dans cette tâche, vous allez ouvrir le projet DQS créé par le package SSIS dans le client DQS, vous allez examiner les résultats du processus de nettoyage, et vous allez éventuellement effectuer un nettoyage interactif, puis exporter les résultats.  
  
1.  Lancez **Data Quality Client**.  
  
2.  Cliquez sur **analyse des activités** dans le **Administration** volet.  
  
3.  Trier la liste selon **l’heure de début de l’activité** pour afficher le dernier enregistrement.  
  
4.  Notez que le nom du projet s'affiche au format suivant : **CleanseAndCurate.Cleanse Supplier Data.GUID**.  
  
     ![Projet de nettoyage DQS créé par le Package SSIS](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "projet de nettoyage DQS créé par le Package SSIS")  
  
5.  Notez que la valeur dans le **est Active** champ est **Active**.  
  
6.  Cliquez sur **Profiler** onglet dans le volet inférieur pour afficher les statistiques du Générateur de profils pour l’activité de nettoyage effectué le package SSIS.  
  
7.  Cliquez sur **fermer** pour fermer la **Administration** écran.  
  
8.  Dans la page principale de **Client DQS**, cliquez sur **ouvrir projet de qualité des données** dans le **projets de qualité des données** volet.  
  
9. Dans la liste des projets, sélectionnez le projet créé par le composant de nettoyage DQS SSIS. Le nom du projet doit être au format :  **CleanseAndCurate.Cleanse Supplier Data.GUID (en rouge)**. Vous devrez peut-être trier la liste selon **Date de création de** colonne et recherchez le dernier enregistrement.  
  
10. Cliquer sur **Suivant**.  
  
11. Le **gérer et afficher les résultats** page doit vous être familière à partir du nettoyage interactif que vous l’avez fait précédemment dans ce didacticiel.  
  
12. Examinez les résultats du nettoyage. Vous pouvez également effectuer le nettoyage interactif et exporter les résultats vers un fichier Excel ou une base de données, dans la page suivante.  
  
13. Cliquer sur **Suivant**. Dans ce **exporter** page, vous pouvez exporter les résultats vers un fichier excel, fichier CSV, ou à une base de données SQL.  
  
14. Cliquez sur **Terminer** pour terminer l’activité.  
  
15. Dans la page principale de **Client DQS**, cliquez sur **analyse des activités** dans le **Administration** volet.  
  
16. Notez que la valeur de **IsActive** champ pour le projet est **terminé** maintenant.  
  
## <a name="next-step"></a>Étape suivante  
 [Conclusion](../../2014/tutorials/conclusion.md)  
  
  
