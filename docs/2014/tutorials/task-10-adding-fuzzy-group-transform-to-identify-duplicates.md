---
title: 'Tâche 10 : Ajout d’une transformation de regroupement probable pour identifier les doublons | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 90b2b323-babd-464a-8914-9dc5e66aca74
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 48e233c6f2c7a55bf2420825b9fb3064db6e89e1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65481253"
---
# <a name="task-10-adding-fuzzy-group-transform-to-identify-duplicates"></a>Tâche 10 : Ajout d’une transformation de regroupement probable pour identifier des doublons
  Dans cette tâche, vous allez ajouter une transformation de regroupement probable au flux de données. La transformation de regroupement probable aide à identifier les doublons dans les données sources. Consultez [Transformation de regroupement approximatif](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md) pour plus d’informations.  
  
1.  Glisser-déplacer **regroupement probable** transformer dans **autres transformations** sur le **boîte à outils SSIS** à la **de flux de données** onglet sous  **Combiner des enregistrements corrects et corrigés**.  
  
2.  Avec le bouton droit **regroupement probable** transformer dans le **de flux de données** onglet, puis cliquez sur **renommer**. Type **regrouper les fournisseurs avec des ID correspondants** et appuyez sur **entrée**.  
  
3.  Se connecter **combiner des enregistrements corrects et corrigés** à **regrouper les fournisseurs avec des ID correspondants** à l’aide du connecteur bleu.  
  
     ![Connexion à regrouper les fournisseurs avec des ID correspondants](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "connexion à regrouper les fournisseurs avec des ID correspondants")  
  
4.  Double-cliquez sur **regrouper les fournisseurs avec des ID correspondants**.  
  
5.  Dans le **éditeur de Transformation de regroupement probable**, cliquez sur **New** regard **liste déroulante de gestionnaire de connexions OLE DB** pour lancer **configurer connexions OLE DB Gestionnaire** boîte de dialogue.  
  
6.  Dans la boîte de dialogue, cliquez sur **New** pour lancer **Gestionnaire de connexions** boîte de dialogue.  
  
7.  Type **(local)** ou **période** (.) pour le nom du serveur.  
  
8.  Sélectionnez **MDS** pour **sélectionner ou entrer un nom de base de données** champ. Vous allez utiliser la base de données MDS comme mémoire temporaire pour le **transformation de regroupement probable**. Le **regroupement probable** transformation requiert une connexion à une instance de SQL Server pour créer les tables temporaires de SQL Server dont l’algorithme de transformation a besoin pour effectuer son travail. Vous pouvez créer une base de données ou utiliser une base de données existante à cet effet.  
  
9. Cliquez sur **tester la connexion** pour tester la connexion et cliquez sur **OK** sur la boîte de message.  
  
10. Dans le **Gestionnaire de connexions** boîte de dialogue, cliquez sur **OK**.  
  
11. Sélectionnez **(local). MDS** (ou **localhost. MDS**) à partir de la **liste de connexions de données** et cliquez sur **OK**.  
  
12. Dans le **éditeur de Transformation de regroupement probable**, vérifiez que **(local). MDS** ou **localhost. MDS** est sélectionné pour le **Gestionnaire de connexions OLE DB**.  
  
13. Basculez vers le **colonnes** onglet.  
  
14. Sélectionnez (case à cocher) **SupplierID_Output** dans la liste des **colonnes d’entrée disponibles**. Pour configurer la transformation, sélectionnez les colonnes d'entrée à utiliser lors de l'identification des doublons. Pour faire simple, utilisez uniquement SupplierID dans cette étape.  
  
     ![Éditeur de Transformation de regroupement probable](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "éditeur de Transformation de regroupement probable")  
  
15. Cliquez sur **OK** pour fermer la **éditeur de Transformation de regroupement probable**.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 11 : Ajouter la transformation de fractionnement conditionnel pour filtrer les doublons](../../2014/tutorials/task-11-adding-conditional-split-transform-to-filter-duplicates.md)  
  
  
