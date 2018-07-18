---
title: 'Tâche 6 : Ajout de Source Excel au flux de données | Microsoft Docs'
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
ms.topic: conceptual
ms.assetid: 0209055e-cb6b-4a07-909e-836596727a2c
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2ce6d1ec5ab2fc9c57bd56e12b56b13231e74606
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279995"
---
# <a name="task-6-adding-excel-source-to-the-data-flow"></a>Tâche 6 : Ajout d'une source Excel au flux de données
  Dans cette tâche, vous allez ajouter une source Excel au flux de données pour lire les données des fournisseurs à partir du fichier Excel source. La source Excel extrait des données depuis des feuilles de calcul ou des plages dans des classeurs Microsoft Excel. Consultez la rubrique [Source Excel](http://msdn.microsoft.com/library/ms141683.aspx) pour plus de détails.  
  
1.  Faites glisser la **Source Excel** depuis **Autres sources** dans **Boîte à outils SSIS** vers l'onglet **Flux de données** .  
  
2.  Cliquez avec le bouton droit sur **Source Excel** dans l'onglet **Flux de données** , puis cliquez sur **Renommer**.  
  
3.  Entrez **Lire les données des fournisseurs à partir d'un fichier Excel** et appuyez sur **ENTRÉE**.  
  
4.  Double-cliquez sur **Lire les données des fournisseurs à partir d'un fichier Excel** pour ouvrir la boîte de dialogue **Éditeur de source Excel** .  
  
5.  Dans la boîte de dialogue **Éditeur de source Excel** , cliquez sur **Nouveau** pour créer une connexion à Excel.  
  
6.  Dans la boîte de dialogue **Gestionnaire de connexions Excel** , cliquez sur **Parcourir**, puis recherchez le fichier **Suppliers.xls** dans le dossier **EIM Tutorial** . Vérifiez que **Microsoft Excel 97-2003** est sélectionné dans la zone **Version Excel** , puis cliquez sur **OK**.  
  
     ![Boîte de dialogue du Gestionnaire de connexions Excel](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "boîte de dialogue du Gestionnaire de connexions Excel")  
  
7.  Dans la boîte de dialogue **Éditeur de source Excel** , sélectionnez **IncomingSuppliers$** dans la zone de liste **Nom de la feuille Excel** .  
  
     ![Nom de feuille Excel - fournisseurs entrants $](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "nom de feuille Excel - fournisseurs entrants $")  
  
8.  Cliquez sur **Aperçu** pour afficher un aperçu des données dans le fichier Excel.  
  
9. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
10. Faites glisser la transformation **Nettoyage DQS** dans **Autres transformations** dans la **Boîte à outils SSIS** vers l'onglet **Flux de données** sous **Lire les données des fournisseurs à partir d'un fichier Excel**. La transformation de nettoyage DQS utilise Data Quality Services (DQS) pour corriger les données en appliquant des règles approuvées dans la base de connaissances. Cette transformation, au moment de l'exécution, crée un projet de nettoyage DQS sur le serveur DQS. Consultez la rubrique [Transformation de nettoyage DQS](http://msdn.microsoft.com/library/ee677619.aspx) pour plus de détails.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 7 : Ajout d’une transformation de nettoyage DQS au flux de données](../integration-services/data-flow/data-flow.md)  
  
  
