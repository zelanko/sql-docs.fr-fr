---
title: 'Tâche 2 : test et publication de la stratégie de correspondance | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: e1ffb6d7-fbc5-4695-b538-cc2302d1a17d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: a9957625e09bde8bb733eca6e564dfdcfbb0bd98
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65484730"
---
# <a name="task-2-testing-and-publishing-the-matching-policy"></a>Tâche 2 : Test et publication de la stratégie de correspondance
  Au cours de cette tâche, vous allez tester et publier la stratégie de suppression de la correspondance **Supprimer les fournisseurs en double** .  
  
1.  Dans la page **résultats de correspondance** , cliquez sur **Démarrer** pour tester l’ensemble de la stratégie. Dans ce cas, vous disposez d'une seule règle dans la stratégie, par conséquent, les résultats du test de la règle et du test de la stratégie devraient être identiques.  
  
2.  Examinez tous les enregistrements correspondants et leur score de correspondance dans la zone de liste. Un enregistrement associé à une icône **verte** est un doublon de l’enregistrement pivot qui le précède. Voici quelques exemples :  
  
    1.  L’enregistrement avec l' **ID d’enregistrement : 1000005** correspond à l’enregistrement avec l' **ID d’enregistrement : 1000004** avec le **score : 100%** , car les deux enregistrements ont les mêmes valeurs pour **SupplierID (condition préalable)**, **nom du fournisseur**et **colonnes ContactEmailAddress**. DQS choisit de façon aléatoire un enregistrement comme enregistrement pivot pour un cluster.  
  
    2.  L’enregistrement **1000023** est une correspondance de l’enregistrement **1000022** avec le score de correspondance : 93%, car les deux enregistrements ont les mêmes valeurs pour **SupplierID (condition préalable)** et les colonnes de **nom de fournisseur** , mais des valeurs différentes pour la colonne **ContactEmailAddress** .  
  
    3.  Faites défiler la liste vers le bas pour voir deux enregistrements avec les ID d’enregistrements : **1000051** et **1000052**. L’enregistrement **1000052** est considéré comme une correspondance avec le score de correspondance **91%** , car les deux enregistrements ont les mêmes valeurs pour les colonnes **RéfFournisseur** et **ContactEmailAddress** , mais des valeurs différentes pour la colonne **nom du fournisseur** .  
  
     ![Définition de la stratégie - Résultats de la stratégie](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-01.jpg "Définition de la stratégie - Résultats de la stratégie")  
  
3.  Cliquez avec le bouton droit sur un enregistrement correspondant (avec une icône verte), puis cliquez sur **afficher les détails** pour afficher plus de détails sur la correspondance telle que la contribution de chaque champ score au score de correspondance global.  
  
     ![Boîte de dialogue Détails du score de correspondance](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-02.jpg "Boîte de dialogue Détails du score de correspondance")  
  
4.  Cliquez sur **Fermer** pour fermer la boîte de dialogue **Détails du score de correspondance** .  
  
5.  Cliquez sur l’onglet **résultats de correspondance** au bas de la page. Cet onglet fournit des informations telles que le nombre d'enregistrements avec correspondance, le nombre d'enregistrements sans correspondance, le nombre de clusters avec des enregistrements correspondants, la taille moyenne des clusters, la taille minimale, et la taille maximale des clusters. Pour plus d’informations, consultez [créer une stratégie de correspondance](https://msdn.microsoft.com/library/hh270290.aspx) . Vous ne pouvez pas exporter les résultats de cette activité. Vous vous contentez ici de définir une stratégie de correspondance en utilisant l'échantillon de données pour tester les règles et la stratégie.  
  
     ![Onglet Résultats de correspondance](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-03.jpg "Onglet Résultats de correspondance")  
  
6.  Cliquez sur **Terminer** pour terminer la création de la stratégie de correspondance.  
  
    > [!NOTE]  
    >  Vous avez simplement défini la stratégie de correspondance, par conséquent vous ne pouvez pas exporter les résultats dans un fichier de sortie. Fondamentalement vous avez utilisé un fichier d'entrée échantillon, vous avez créé des règles, et vous avez testé les règles et la stratégie sur les exemples de données dans le but de définir la stratégie.  
  
7.  Dans la boîte de dialogue SQL Server Data Quality Services, cliquez sur **publier** , puis sur **OK** dans la boîte de message. À présent, la stratégie de correspondance que vous avez définie est publiée dans la base de connaissances **fournisseurs** . Vous pouvez utiliser la base de connaissances pour exécuter le processus de correspondance dans un fichier d'entrée afin d'identifier et supprimer les doublons.  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 3 : Création et exécution d'un projet de qualité des données pour la mise en correspondance](../../2014/tutorials/task-3-creating-and-running-a-data-quality-project-for-matching.md)  
  
  
