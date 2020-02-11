---
title: 'Tâche 6 : importation de valeurs à partir du projet nettoyer la liste des fournisseurs | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fec0deef-a729-4ff1-b709-72d2b3f407ac
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: f6b90a36238cd4a02e86d49125ee662f07d32882
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489097"
---
# <a name="task-6-importing-values-from-the-cleanse-supplier-list-project"></a>Tâche 6 : Importation de valeurs depuis le projet de nettoyage de la liste des fournisseurs
  Dans cette tâche, vous allez importer les connaissances de qualité des données collectées pendant le processus de nettoyage. Pour plus d’informations, consultez [importation de valeurs de projet de nettoyage dans un domaine](https://msdn.microsoft.com/library/hh479581.aspx) . Vous exportez également la base de connaissances dans un fichier DQS avant de publier la base de connaissances **fournisseurs** mise à jour.  
  
1.  Dans la page principale du **client DQS**, cliquez sur la **flèche droite** en regard de **fournisseurs** sous **bases de connaissances récentes** , puis cliquez sur **gestion de domaine**.  
  
2.  Cliquez sur **adresse de messagerie du contact** dans la liste des domaines et basculez vers l’onglet valeurs du **domaine** dans le volet droit.  
  
3.  Cliquez sur la **flèche vers le bas** en regard de l’icône **importer des valeurs** dans la barre d’outils, puis cliquez sur Importer les **valeurs du projet**.  
  
     ![Bouton à la barre d'outils Importer des valeurs de projet](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-01.jpg "Bouton à la barre d'outils Importer des valeurs de projet")  
  
4.  Dans la boîte de dialogue **Importer les valeurs du projet** , sélectionnez le projet nettoyer la liste des **fournisseurs** , puis cliquez sur **OK**.  
  
5.  Notez que toutes les adresses électroniques sont importées avec les deux corrections effectuées lors du nettoyage interactif. Faites défiler la liste pour afficher les deux corrections.  
  
    |Valeur|Corriger vers|  
    |-----------|----------------|  
    |bobby0@adventure-work.com|bobby0@adventure-works.com|  
    |tad0@adventure-work.com|tad0@adventure-works.com|  
  
6.  Répétez l’étape précédente pour importer des valeurs de projet pour le domaine **Country** et Notez qu’une nouvelle entrée est ajoutée pour corriger l' **État des États-Unis** à **États-Unis** (avec').  
  
    |Valeur|Corriger vers|  
    |-----------|----------------|  
    |United State|États-Unis|  
  
7.  Pour afficher les anciennes valeurs de domaine, désactivez la case à cocher **afficher uniquement les nouvelles** .  
  
8.  Répétez l’étape précédente pour importer des valeurs de projet pour le domaine **nom du fournisseur** . Par défaut, après l'importation, vous verrez seulement les nouvelles valeurs. Pour afficher toutes les valeurs, désactivez la case à cocher **afficher uniquement les nouvelles** . Vous avez enrichi la base de connaissances **fournisseurs** avec ce que vous avez appris de l’activité de nettoyage. Plus la base de connaissances sera consolidée, meilleurs seront les résultats du nettoyage.  
  
    > [!NOTE]  
    >  Il n'est pas possible d'importer des valeurs pour un domaine composite.  
  
9. Cliquez sur Exporter l’icône de **base de connaissances** dans la barre d’outils, puis cliquez sur Exporter la base de **connaissances**.  
  
     ![Menu Exporter la base de connaissances](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-02.jpg "Menu Exporter la base de connaissances")  
  
10. Accédez au dossier du didacticiel, tapez **Suppliers. DQS** comme **nom de fichier**, puis cliquez sur **Enregistrer**. Vous pouvez utiliser ce fichier DQS pour créer une nouvelle base de connaissances.  
  
11. Cliquez sur **OK** pour fermer la boîte de message **Exporter la base de connaissances-fournisseurs** .  
  
12. Cliquez sur **Terminer** pour terminer l’activité.  
  
13. Cliquez sur **Publier**.  
  
14. Cliquez sur **OK** dans le message de confirmation.  
  
## <a name="next-step"></a>étape suivante  
 [Leçon 3 : Faire correspondre les données pour supprimer les doublons de la liste des fournisseurs](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)  
  
  
