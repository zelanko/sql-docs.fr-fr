---
title: 'Tâche 10 : ajout d’une transformation de groupe approximatif pour identifier les doublons | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 90b2b323-babd-464a-8914-9dc5e66aca74
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e7091c4dbb8244476357afba18e973535def8baa
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064813"
---
# <a name="task-10-adding-fuzzy-group-transform-to-identify-duplicates"></a>Tâche 10 : Ajout d’une transformation de regroupement probable pour identifier des doublons
  Dans cette tâche, vous allez ajouter une transformation de regroupement probable au flux de données. La transformation de regroupement probable aide à identifier les doublons dans les données sources. Pour plus d’informations, consultez [transformation de regroupement approximatif](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md) .  
  
1.  Glissez-déplacez la transformation de **groupe approximatif** dans d' **autres transformations** de la **boîte à outils SSIS** vers l’onglet de **Workflow** sous **combiner les enregistrements corrects et corrigés**.  
  
2.  Cliquez avec le bouton droit sur transformation de **groupe approximatif** dans l’onglet **Flow Data** , puis cliquez sur **Renommer**. Tapez **regrouper les fournisseurs avec des ID correspondants** et appuyez sur **entrée**.  
  
3.  Connexion **combiner des enregistrements corrects et corrigés** pour **regrouper les fournisseurs avec des ID correspondants** à l’aide du connecteur bleu.  
  
     ![Connexion aux fournisseurs du groupe avec ID correspondants](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "Connexion aux fournisseurs du groupe avec ID correspondants")  
  
4.  Double-cliquez sur **regrouper les fournisseurs avec des ID correspondants**.  
  
5.  Dans l **'éditeur de transformation de groupe approximatif**, cliquez sur **nouveau** en regard de **OLE DB liste déroulante gestionnaire de connexions** pour lancer la boîte de dialogue **configurer le gestionnaire de connexions OLE DB** .  
  
6.  Dans la boîte de dialogue, cliquez sur **nouveau** pour lancer la boîte de dialogue **Gestionnaire de connexions** .  
  
7.  Tapez **(local)** ou **point** (.) pour le nom du serveur.  
  
8.  Sélectionnez **MDS** pour **le champ sélectionner ou entrer un nom de base de données** . Vous allez utiliser la base de données MDS comme stockage temporaire pour la **transformation de groupe approximatif**. La transformation de **regroupement approximatif** nécessite une connexion à une instance de SQL Server pour créer les tables temporaires SQL Server dont l’algorithme de transformation a besoin pour effectuer son travail. Vous pouvez créer une base de données ou utiliser une base de données existante à cet effet.  
  
9. Cliquez sur **tester la connexion** pour tester la connexion, puis cliquez sur **OK** dans la boîte de message.  
  
10. Dans la boîte de dialogue **Gestionnaire de connexions** , cliquez sur **OK**.  
  
11. Sélectionnez **(local). MDS** (ou **localhost. MDS**) dans la **liste des connexions de données** , puis cliquez sur **OK**.  
  
12. Dans l **'éditeur de transformation de regroupement probable**, vérifiez que **(local). MDS** ou **localhost. MDS** est sélectionné pour le **Gestionnaire de connexions OLE DB**.  
  
13. Basculez vers l’onglet **colonnes** .  
  
14. Sélectionnez (case à cocher) **SupplierID_Output** dans la liste des **colonnes d’entrée disponibles**. Pour configurer la transformation, sélectionnez les colonnes d'entrée à utiliser lors de l'identification des doublons. Pour faire simple, utilisez uniquement SupplierID dans cette étape.  
  
     ![Éditeur de transformation de regroupement probable](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "Éditeur de transformation de regroupement probable")  
  
15. Cliquez sur **OK** pour fermer l **'éditeur de transformation de groupe approximatif**.  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 11 : Ajout d’une transformation de fractionnement conditionnel pour filtrer les doublons](../../2014/tutorials/task-11-adding-conditional-split-transform-to-filter-duplicates.md)  
  
  
