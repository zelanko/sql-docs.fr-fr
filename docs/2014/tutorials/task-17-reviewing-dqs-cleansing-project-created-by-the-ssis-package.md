---
title: 'Tâche 17 : Examiner de nettoyage DQS projet créé par le package SSIS | Documents Microsoft'
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
ms.topic: article
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4226fd9a8e8eb8aa2851eed8eb318b8535010c8a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143388"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a>Tâche 17 : Examiner le projet de nettoyage DQS créé par le package SSIS
  Dans cette tâche, vous allez ouvrir le projet DQS créé par le package SSIS dans le client DQS, vous allez examiner les résultats du processus de nettoyage, et vous allez éventuellement effectuer un nettoyage interactif, puis exporter les résultats.  
  
1.  Lancez **Data Quality Client**.  
  
2.  Cliquez sur **analyse de l’activité** dans les **Administration** volet.  
  
3.  Triez la liste selon **début** pour afficher le dernier enregistrement.  
  
4.  Notez que vous consultez un nom du projet dans le format suivant : **CleanseAndCurate.Cleanse Supplier Data.GUID**.  
  
     ![Projet de nettoyage DQS créé par le Package SSIS](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "projet de nettoyage DQS créé par le Package SSIS")  
  
5.  Notez que la valeur de la **est Active** champ est **Active**.  
  
6.  Cliquez sur **Profiler** onglet dans le volet inférieur pour afficher les statistiques du Générateur de profils pour l’activité de nettoyage effectué par le package SSIS.  
  
7.  Cliquez sur **fermer** pour fermer la **Administration** écran.  
  
8.  Dans la page principale de **Client DQS**, cliquez sur **ouvrir projet de qualité des données** dans les **projets de qualité des données** volet.  
  
9. Dans la liste des projets, sélectionnez le projet créé par le composant de nettoyage DQS SSIS. Le nom du projet doit être au format : **CleanseAndCurate.Cleanse Supplier Data.GUID (en rouge)**. Vous devrez peut-être trier la liste en fonction de **Date de création de** colonne et recherchez le dernier enregistrement.  
  
10. Cliquez sur **Suivant**.  
  
11. Le **gérer et afficher les résultats** page doit être familière, le nettoyage interactif que vous l’avez fait précédemment dans ce didacticiel.  
  
12. Examinez les résultats du nettoyage. Vous pouvez également effectuer le nettoyage interactif et exporter les résultats vers un fichier Excel ou une base de données, dans la page suivante.  
  
13. Cliquez sur **Suivant**. Dans ce **exporter** page, vous pouvez exporter les résultats vers un fichier excel, un fichier CSV, ou à une base de données SQL.  
  
14. Cliquez sur **Terminer** pour terminer l’activité.  
  
15. Dans la page principale de **Client DQS**, cliquez sur **analyse de l’activité** dans les **Administration** volet.  
  
16. Notez que la valeur de **IsActive** champ pour le projet est **terminé** maintenant.  
  
## <a name="next-step"></a>Étape suivante  
 [Conclusion](../../2014/tutorials/conclusion.md)  
  
  