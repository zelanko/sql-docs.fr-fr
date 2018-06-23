---
title: 'Tâche 2 : Test et publication de la stratégie de correspondance | Documents Microsoft'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1ffb6d7-fbc5-4695-b538-cc2302d1a17d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8f67535e5ad4969983b06fcb710c1dfce1d97cb4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142838"
---
# <a name="task-2-testing-and-publishing-the-matching-policy"></a>Tâche 2 : Test et publication de la stratégie de correspondance
  Dans cette tâche, vous testez et publiez le **supprimer les fournisseurs en double** stratégie de correspondance.  
  
1.  Dans le **résultats de correspondance** , cliquez sur **Démarrer** pour tester la stratégie entière. Dans ce cas, vous disposez d'une seule règle dans la stratégie, par conséquent, les résultats du test de la règle et du test de la stratégie devraient être identiques.  
  
2.  Examinez tous les enregistrements correspondants et leur score de correspondance dans la zone de liste. Un enregistrement qui a un **vert** icône associé est un doublon de l’enregistrement pivot qui le précède. Voici deux exemples :  
  
    1.  L’enregistrement avec **ID d’enregistrement : 1000005** est une correspondance de l’enregistrement avec **Id d’enregistrement : 1000004** avec **Score : 100 %** , car les deux enregistrements ont les mêmes valeurs pour **SupplierID (condition préalable)**, **Supplier Name**, et **les colonnes ContactEmailAddress**. DQS choisit de façon aléatoire un enregistrement comme enregistrement pivot pour un cluster.  
  
    2.  L’enregistrement **1000023** est une correspondance de l’enregistrement **1000022** avec le score de correspondance : 93 % car les deux enregistrements ont les mêmes valeurs pour **SupplierID (condition préalable)** et  **Nom du fournisseur** colonnes, mais des valeurs différentes pour le **ContactEmailAddress** colonne.  
  
    3.  Faites défiler vers le bas de la liste pour afficher les deux enregistrements avec les ID : **1000051** et **1000052**. Enregistrement **1000052** est considéré comme une correspondance avec un score **91 %** , car les deux enregistrements ont les mêmes valeurs pour le **SupplierID** et  **ContactEmailAddress** colonnes, mais des valeurs différentes pour le **Supplier Name** colonne.  
  
     ![Définition de stratégie - résultats de la stratégie](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-01.jpg "définition de stratégie - résultats de la stratégie")  
  
3.  Avec le bouton droit sur un enregistrement avec correspondance (avec une icône verte) et cliquez sur **afficher les détails** pour plus d’informations sur la correspondance telles que la contribution de chaque score de champ au score de correspondance global.  
  
     ![Score de correspondance de la boîte de dialogue Détails](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-02.jpg "Score de correspondance de la boîte de dialogue Détails")  
  
4.  Cliquez sur **fermer** pour fermer la **détails du Score de correspondance** boîte de dialogue.  
  
5.  Cliquez sur **résultats de correspondance** onglet en bas de la page. Cet onglet fournit des informations telles que le nombre d'enregistrements avec correspondance, le nombre d'enregistrements sans correspondance, le nombre de clusters avec des enregistrements correspondants, la taille moyenne des clusters, la taille minimale, et la taille maximale des clusters. Consultez [créer une stratégie de correspondance](http://msdn.microsoft.com/library/hh270290.aspx) pour plus d’informations. Vous ne pouvez pas exporter les résultats de cette activité. Vous vous contentez ici de définir une stratégie de correspondance en utilisant l'échantillon de données pour tester les règles et la stratégie.  
  
     ![Onglet des résultats de correspondance](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-03.jpg "onglet des résultats de correspondance")  
  
6.  Cliquez sur **Terminer** pour terminer la création de la stratégie de correspondance.  
  
    > [!NOTE]  
    >  Vous avez simplement défini la stratégie de correspondance, par conséquent vous ne pouvez pas exporter les résultats dans un fichier de sortie. Fondamentalement vous avez utilisé un fichier d'entrée échantillon, vous avez créé des règles, et vous avez testé les règles et la stratégie sur les exemples de données dans le but de définir la stratégie.  
  
7.  Dans la boîte de dialogue SQL Server Data Quality Services, cliquez sur **publier** et cliquez sur **OK** sur la boîte de message. À présent, vous avez défini la stratégie de correspondance est publiée dans le **fournisseurs** Base de connaissances. Vous pouvez utiliser la base de connaissances pour exécuter le processus de correspondance dans un fichier d'entrée afin d'identifier et supprimer les doublons.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 3 : Création et exécution d’un projet de qualité des données pour la correspondance](../../2014/tutorials/task-3-creating-and-running-a-data-quality-project-for-matching.md)  
  
  