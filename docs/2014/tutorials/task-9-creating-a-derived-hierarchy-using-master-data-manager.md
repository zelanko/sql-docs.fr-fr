---
title: 'Tâche 9 : Création d’une hiérarchie dérivée à l’aide de Master Data Manager | Documents Microsoft'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 35584d33afac7a2a8f74abd013288a974cade512
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154729"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a>Tâche 9 : Création d'une hiérarchie dérivée à l'aide de Master Data Manager
  Dans cette tâche, vous allez créer une hiérarchie dérivée à l'aide de Master Data Manager. Cette hiérarchie dérivée est dérivée des relations d’attribut basé sur un domaine entre le **fournisseur** et **état** entités.  
  
1.  Basculez vers la page principale de **Master Data Manager** en cliquant sur **SQL Server 2012 Master Data Services** en haut de la page.  
  
2.  Cliquez sur **Administration système** dans les **tâches administratives** section.  
  
3.  Pointez la souris sur **gérer** dans la barre de menus, cliquez sur **hiérarchies dérivées**.  
  
     ![Menu gérer - hiérarchies dérivées sélectionnées](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "Menu gérer - hiérarchies dérivées sélectionnées")  
  
4.  Cliquez sur **ajouter une hiérarchie dérivée (+)** dans la barre d’outils.  
  
     ![Ajouter le bouton de la hiérarchie dérivée](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "ajouter le bouton de la hiérarchie dérivée")  
  
5.  Type **SuppliersInState** pour le **nom de hiérarchie dérivée**.  
  
6.  Cliquez sur **enregistrer** dans la barre d’outils.  
  
     ![Enregistrer dérivée hiérarchie bouton](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "enregistrer dérivée de bouton de la hiérarchie")  
  
7.  Faites glisser **fournisseur** de **niveaux disponibles : SuppliersInState** à **niveaux actuels : SuppliersInState**.  
  
     ![Entités et hiérarchies au niveau actuel disponibles](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "entités et hiérarchies au niveau actuel disponibles")  
  
8.  Faites glisser **état** de **niveaux disponibles : SuppliersInState** à **niveaux actuels : SuppliersInState**. L’écran doit avoir **niveaux actuels** comme indiqué dans l’image suivante.  
  
     ![Niveaux actuels et l’aperçu de la hiérarchie dérivée](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "niveaux actuels et l’aperçu de la hiérarchie dérivée")  
  
9. Dans le **aperçu** fenêtre, développez **NY {New York}** et vous devez voir un seul fournisseur dans cet état comme indiqué dans l’image précédente.  
  
10. Basculez vers la page principale de **Master Data Manager** en cliquant sur **SQL Server 2012 Master Data Services** en haut de la page.  
  
11. Cliquez sur **Explorateur**.  
  
12. Pointez la souris sur **hiérarchies** et cliquez sur **Derived : SuppliersInState**.  
  
     ![Hiérarchies - Derived : SuppliersInState Menu](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "hiérarchies - Derived : SuppliersInState Menu")  
  
13. Cliquez sur n’importe quel **état** nœud dans le **arborescence** et vous devez voir les fournisseurs dans cet état dans le volet droit.  
  
     ![Dérivée de la hiérarchie dans l’Explorateur de](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "dérivée de hiérarchie dans l’Explorateur")  
  
## <a name="next-step"></a>Étape suivante  
 [Leçon 5 : Automatisation du nettoyage et la mise en correspondance avec SSIS](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  