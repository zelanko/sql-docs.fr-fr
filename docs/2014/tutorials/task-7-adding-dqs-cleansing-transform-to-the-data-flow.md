---
title: 'Tâche 7 : ajout d’une transformation de nettoyage DQS au Data Flow | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 0b749c71-dfb6-493a-804f-600290d46eef
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 209659609c2cf19196cc35050fb32e39e079d1c7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65488941"
---
# <a name="task-7-adding-dqs-cleansing-transform-to-the-data-flow"></a>Tâche 7 : Ajout d’une transformation de nettoyage DQS au flux de données
  Dans cette tâche, vous allez ajouter la transformation de nettoyage DQS au flux de données pour nettoyer les données des fournisseurs d'entrée à l'aide de DQS. Pour plus d’informations sur la transformation, consultez **[transformation de nettoyage DQS](https://msdn.microsoft.com/library/ee677619.aspx)** .  
  
1.  Cliquez avec le bouton droit sur **nettoyage DQS** sous l’onglet **Flow Data** , puis cliquez sur **Renommer**. Tapez **nettoyer les données des fournisseurs**, puis appuyez sur **entrée**.  
  
2.  Sélectionnez **lire les données des fournisseurs à partir d’un fichier Excel**. Faites glisser le connecteur bleu pour **nettoyer les données des fournisseurs**. Les composants sont maintenant connectés.  
  
     ![Lire les données du fournisseur-> nettoyer les données des fournisseurs](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "Lire les données des fournisseurs -> Nettoyer les données des fournisseurs")  
  
3.  Double-cliquez sur **nettoyer les données des fournisseurs**.  
  
4.  Dans l **'éditeur de transformation de nettoyage DQS**, cliquez sur **nouveau** en regard de la **liste déroulante gestionnaire de connexions de qualité des données**.  
  
5.  Dans la boîte de dialogue **Gestionnaire de connexions de nettoyage DQS** , tapez **(local)** ou **point** (.) pour vous connecter au serveur local. Cette leçon suppose que vous avez installé DQS sur un serveur local.  
  
6.  Cliquez sur **tester la connexion** pour tester la connexion au serveur DQS.  
  
7.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
8.  Sélectionnez **fournisseurs** pour la **base de connaissances de qualité des données**.  
  
     ![Éditeur de transformation de nettoyage DQS - Base de connaissances des fournisseurs](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "Éditeur de transformation de nettoyage DQS - Base de connaissances des fournisseurs")  
  
9. Basculez vers l’onglet **mappage** en haut.  
  
10. Dans **colonnes d’entrée disponibles**, **Sélectionnez nom du fournisseur**, **ContactEmailAddress**, **adresse**, **ville**, **État**, **pays**et **Code postal** en activant les cases à cocher.  
  
     ![Éditeur de transformation de nettoyage DQS - Mappages](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "Éditeur de transformation de nettoyage DQS - Mappages")  
  
11. Dans le volet inférieur, mappez ces colonnes à l’aide des listes déroulantes de la colonne **domaine** :  
  
    |Colonne|Domain|  
    |------------|------------|  
    |Nom du fournisseur|Nom du fournisseur|  
    |ContactEmailAddress|E-mail du contact|  
    |Adresse|Adresse|  
    |City|City|  
    |State|State|  
    |Country|Country|  
    |Code postal|Zip|  
  
12. Cliquez sur **OK** pour fermer la boîte de dialogue **éditeur de transformation de nettoyage DQS** .  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 8 : Ajout de la transformation de fractionnement conditionnel pour fractionner la sortie du nettoyage](../../2014/tutorials/task-8-adding-conditional-split-transform-to-split-cleansing-output.md)  
  
  
