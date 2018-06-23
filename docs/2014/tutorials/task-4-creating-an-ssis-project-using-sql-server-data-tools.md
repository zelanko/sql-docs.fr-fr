---
title: 'Tâche 4 : Création d’un projet SSIS à l’aide de SQL Server Data Tools | Documents Microsoft'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8603ea91-2ec4-40b6-8070-4f824332f5d3
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 03c0a6599990357a255fab3beeb434db3cb5d97d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141432"
---
# <a name="task-4-creating-an-ssis-project-using-sql-server-data-tools"></a>Tâche 4 (Facultatif) : Création d'un projet SSIS à l'aide de SQL Server Data Tools
  Dans cette tâche, vous créez un projet SSIS à l’aide de **SQL Server Data Tools** pour automatiser le nettoyage et la correspondance des données des fournisseurs.  
  
1.  Lancez **SQL Server Data Tools**. Cliquez sur Démarrer, pointez sur **tous les programmes**, développez **Microsoft SQL Server 2012**, puis cliquez sur **SQL Server Data Tools**.  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Développez **Business Intelligence** dans les **modèles installés** volet et sélectionnez **Integration Services**.  
  
     ![Visual Studio - boîte de dialogue Nouveau projet](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio - boîte de dialogue Nouveau projet")  
  
4.  Sélectionnez **projet Integration Services** dans les **liste des types de projets**.  
  
5.  Type **CleanseAndCurateSuppliers** pour **nom** et cliquez sur **OK**.  
  
6.  Dans **l’Explorateur de solutions** fenêtre, avec le bouton droit **Package.dtsx** et sélectionnez **renommer**. Si vous ne voyez pas **l’Explorateur de solutions** fenêtre, cliquez sur **vue** sur la barre de menus et cliquez sur **l’Explorateur de solutions**.  
  
     ![Package.dtsx - Menu renommer](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx - Menu renommer")  
  
7.  Type **CleanseAndCurate.dtsx** et appuyez sur **entrée**. Assurez-vous que le **extension** reste **.dtsx**.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 5 : Ajout d’une tâche de flux de données](task-5-adding-data-flow-task.md)  
  
  