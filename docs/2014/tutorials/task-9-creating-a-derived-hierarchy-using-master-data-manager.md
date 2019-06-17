---
title: 'Tâche 9 : Création d’une hiérarchie dérivée à l’aide de Master Data Manager | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7cb2f12115e3fe743c49c2f7e69f765da4501ba2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65489553"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a>Tâche 9 : Création d’une hiérarchie dérivée à l’aide de Master Data Manager
  Dans cette tâche, vous allez créer une hiérarchie dérivée à l'aide de Master Data Manager. Cette hiérarchie dérivée est dérivée des relations d’attributs basés sur un domaine entre la **fournisseur** et **état** entités.  
  
1.  Basculez vers la page principale de **Master Data Manager** en cliquant sur **SQL Server 2012 Master Data Services** en haut de la page.  
  
2.  Cliquez sur **Administration système** dans le **tâches administratives** section.  
  
3.  Pointez la souris sur **gérer** dans la barre de menus, cliquez sur **hiérarchies dérivées**.  
  
     ![Menu gérer - hiérarchies dérivées sélectionnées](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "Menu gérer - hiérarchies dérivées sélectionnées")  
  
4.  Cliquez sur **ajouter une hiérarchie dérivée (+)** dans la barre d’outils.  
  
     ![Ajouter le bouton de la hiérarchie dérivée](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "ajouter le bouton de la hiérarchie dérivée")  
  
5.  Type **SuppliersInState** pour le **nom de hiérarchie dérivée**.  
  
6.  Cliquez sur **enregistrer** dans la barre d’outils.  
  
     ![Enregistrer la hiérarchie bouton dérivée](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "enregistrer la bouton de la hiérarchie dérivée")  
  
7.  Faites glisser **fournisseur** de **niveaux disponibles : SuppliersInState** à **niveaux actuels : SuppliersInState**.  
  
     ![Entités et hiérarchies pour le niveau actuel disponibles](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "entités et hiérarchies pour le niveau actuel disponibles")  
  
8.  Faites glisser **état** de **niveaux disponibles : SuppliersInState** à **niveaux actuels : SuppliersInState**. L’écran doit avoir **niveaux actuels** comme indiqué dans l’image suivante.  
  
     ![Niveaux actuels et aperçu de hiérarchie dérivée](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "niveaux actuels et aperçu de hiérarchie dérivée")  
  
9. Dans le **aperçu** fenêtre, développez **NY {New York}** et vous devriez voir un seul fournisseur dans cet état comme indiqué dans l’image précédente.  
  
10. Basculez vers la page principale de **Master Data Manager** en cliquant sur **SQL Server 2012 Master Data Services** en haut de la page.  
  
11. Cliquez sur **Explorateur**.  
  
12. Pointez la souris sur **hiérarchies** et cliquez sur **Derived : SuppliersInState**.  
  
     ![Hiérarchies - dérivées : SuppliersInState Menu](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "hiérarchies - dérivées : SuppliersInState Menu")  
  
13. Cliquez sur n’importe quel **état** nœud dans le **arborescence** et vous devez voir les fournisseurs dans cet état dans le volet droit.  
  
     ![Dérivée de hiérarchie dans l’Explorateur](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "dérivée de hiérarchie dans l’Explorateur")  
  
## <a name="next-step"></a>Étape suivante  
 [Leçon 5 : Automatisation du nettoyage et la mise en correspondance avec SSIS](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  
