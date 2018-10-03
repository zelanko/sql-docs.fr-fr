---
title: 'Tâche 6 : Importation de valeurs depuis le projet de nettoyage fournisseurs liste | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: fec0deef-a729-4ff1-b709-72d2b3f407ac
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d0eff880132e33cd8d73e7a1faa6dc6649b2caa2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137639"
---
# <a name="task-6-importing-values-from-the-cleanse-supplier-list-project"></a>Tâche 6 : Importation de valeurs depuis le projet de nettoyage de la liste des fournisseurs
  Dans cette tâche, vous allez importer les connaissances de qualité des données collectées pendant le processus de nettoyage. Consultez [l’importation des valeurs de projet de nettoyage dans un domaine](http://msdn.microsoft.com/library/hh479581.aspx) rubrique pour plus d’informations. Vous également exporter la base de connaissances dans un fichier DQS avant de publier la mise à jour **fournisseurs** base de connaissances.  
  
1.  Dans la page principale de **Client DQS**, cliquez sur **flèche droite** regard **fournisseurs** sous **base de connaissances récentes** et cliquez sur **Gestion des domaines**.  
  
2.  Cliquez sur **adresse E-mail de Contact** dans la liste des domaines, puis basculer vers le **les valeurs du domaine** onglet dans le volet droit.  
  
3.  Cliquez sur **flèche vers le bas** à côté du **importer des valeurs** icône sur la barre d’outils et cliquez sur **importer des valeurs de projet**.  
  
     ![Bouton de barre d’outils de valeurs de projet d’importation](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-01.jpg "importer de bouton de barre d’outils de valeurs de projet")  
  
4.  Dans le **importer des valeurs de projet** boîte de dialogue, sélectionnez le **nettoyer la liste des fournisseurs** projet, puis cliquez sur **OK**.  
  
5.  Notez que toutes les adresses électroniques sont importées avec les deux corrections effectuées lors du nettoyage interactif. Faites défiler la liste pour afficher les deux corrections.  
  
    |Valeur|Corriger vers|  
    |-----------|----------------|  
    |bobby0@adventure-work.com|bobby0@adventure-works.com|  
    |tad0@adventure-work.com|tad0@adventure-works.com|  
  
6.  Répétez l’étape précédente de l’importation des valeurs de projet pour le **pays** domaine et notez qu’une nouvelle entrée est ajoutée pour corriger **United State** à **United States** (avec ' s').  
  
    |Valeur|Corriger vers|  
    |-----------|----------------|  
    |United State|United States|  
  
7.  Pour voir les anciennes valeurs de domaine, désactivez **afficher seulement les nouvelles** case à cocher.  
  
8.  Répétez l’étape précédente de l’importation des valeurs de projet pour le **Supplier Name** domaine. Par défaut, après l'importation, vous verrez seulement les nouvelles valeurs. Pour voir toutes les valeurs, désactivez **afficher seulement les nouvelles** case à cocher. Vous avez enrichi la **fournisseurs** base de connaissances avec ce que vous avez appris à partir de l’activité de nettoyage. Plus la base de connaissances sera consolidée, meilleurs seront les résultats du nettoyage.  
  
    > [!NOTE]  
    >  Il n'est pas possible d'importer des valeurs pour un domaine composite.  
  
9. Cliquez sur **exporter la Base de connaissances** icône dans la barre d’outils puis cliquez sur **exporter la Base de connaissances**.  
  
     ![Exporter la Base de connaissances Menu](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-02.jpg "exporter le Menu de la Base de connaissances")  
  
10. Accédez au dossier Tutorial, type **Suppliers.dqs** pour le **nom de fichier**, puis cliquez sur **enregistrer**. Vous pouvez utiliser ce fichier DQS pour créer une nouvelle base de connaissances.  
  
11. Cliquez sur **OK** pour fermer la **exporter la Base de connaissances – fournisseurs** boîte de message.  
  
12. Cliquez sur **Terminer** pour terminer l’activité.  
  
13. Cliquez sur **Publier**.  
  
14. Cliquez sur **OK** dans le message de confirmation.  
  
## <a name="next-step"></a>Étape suivante  
 [Leçon 3 : Faire correspondre les données pour supprimer les doublons de la liste des fournisseurs](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)  
  
  
