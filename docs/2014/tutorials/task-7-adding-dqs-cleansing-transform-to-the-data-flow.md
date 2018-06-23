---
title: 'Tâche 7 : Ajout d’une transformation au flux de données de nettoyage DQS | Documents Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b749c71-dfb6-493a-804f-600290d46eef
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 10b0fb12ace5a113bbde03cecf803a37b49b1974
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154069"
---
# <a name="task-7-adding-dqs-cleansing-transform-to-the-data-flow"></a>Tâche 7 : Ajout d'une transformation de nettoyage DQS au flux de données
  Dans cette tâche, vous allez ajouter la transformation de nettoyage DQS au flux de données pour nettoyer les données des fournisseurs d'entrée à l'aide de DQS. Consultez **[transformation de nettoyage DQS](http://msdn.microsoft.com/library/ee677619.aspx)** pour plus d’informations sur la transformation.  
  
1.  Avec le bouton droit **nettoyage DQS** dans les **de flux de données** onglet, puis cliquez sur **renommer**. Type **nettoyer les données des fournisseurs**, puis appuyez sur **entrée**.  
  
2.  Sélectionnez **lire les données de fournisseur à partir d’un fichier Excel**; faites glisser le connecteur bleu sur **nettoyer les données des fournisseurs**. Les composants sont maintenant connectés.  
  
     ![Lire les données des fournisseurs -> Nettoyer les données des fournisseurs](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "lire les données des fournisseurs -> Nettoyer les données des fournisseurs")  
  
3.  Double-cliquez sur **nettoyer les données des fournisseurs**.  
  
4.  Dans le **éditeur de Transformation de nettoyage DQS**, cliquez sur **nouveau** à côté du **liste déroulante de gestionnaire de connexions de qualité des données**.  
  
5.  Dans le **Gestionnaire de connexions de nettoyage DQS** boîte de dialogue, tapez **(local)** ou **période** (.) pour se connecter au serveur local. Cette leçon suppose que vous avez installé DQS sur un serveur local.  
  
6.  Cliquez sur **tester la connexion** pour tester la connexion au serveur DQS.  
  
7.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
8.  Sélectionnez **fournisseurs** pour le **Base de connaissances de qualité des données**.  
  
     ![Éditeur de Transformation - Ko de fournisseurs de nettoyage DQS](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "éditeur de Transformation - Ko de fournisseurs de nettoyage DQS")  
  
9. Basculez vers le **mappage** onglet en haut.  
  
10. À partir de **colonnes d’entrée disponibles**, sélectionnez **Supplier Name**, **ContactEmailAddress**, **adresse ligne**, **Ville**, **État**, **pays**, et **Code postal** en activant les cases à cocher.  
  
     ![Éditeur de Transformation - mappages de nettoyage DQS](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "éditeur de Transformation - mappages de nettoyage DQS")  
  
11. Dans le volet inférieur, mappez ces colonnes à l’aide des listes déroulantes dans le **domaine** colonne :  
  
    |colonne|Domaine|  
    |------------|------------|  
    |Nom du fournisseur|Nom du fournisseur|  
    |ContactEmailAddress|Messagerie de contact|  
    |Adresse|Adresse|  
    |Ville|Ville|  
    |État|État|  
    |Pays|Pays|  
    |Code postal|Code postal|  
  
12. Cliquez sur **OK** pour fermer la **éditeur de Transformation de nettoyage DQS** boîte de dialogue.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 8 : Ajout de la transformation de fractionnement conditionnel pour fractionner la sortie du nettoyage](../../2014/tutorials/task-8-adding-conditional-split-transform-to-split-cleansing-output.md)  
  
  