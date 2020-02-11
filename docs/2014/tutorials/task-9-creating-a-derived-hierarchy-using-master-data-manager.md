---
title: 'Tâche 9 : création d’une hiérarchie dérivée à l’aide de la Data Manager Master | Microsoft Docs'
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489553"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a>Tâche 9 : Création d'une hiérarchie dérivée à l'aide de Master Data Manager
  Dans cette tâche, vous allez créer une hiérarchie dérivée à l'aide de Master Data Manager. Cette hiérarchie dérivée est dérivée des relations d’attributs basés sur un domaine entre les entités **fournisseur** et **État** .  
  
1.  Basculez vers la page principale du **Data Manager maître** en cliquant sur **SQL Server Master Data Services 2012** en haut de la page.  
  
2.  Cliquez sur **administration de système** dans la section **tâches administratives** .  
  
3.  Pointez la souris sur **gérer** dans la barre de menus, puis cliquez sur **hiérarchies dérivées**.  
  
     ![Menu Gérer - Hiérarchies dérivées sélectionnées](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "Menu Gérer - Hiérarchies dérivées sélectionnées")  
  
4.  Cliquez sur le bouton **Ajouter une hiérarchie dérivée (+)** dans la barre d’outils.  
  
     ![Bouton Ajouter une hiérarchie dérivée](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "Bouton Ajouter une hiérarchie dérivée")  
  
5.  Tapez **SuppliersInState** pour le **nom de la hiérarchie dérivée**.  
  
6.  Cliquez sur le bouton **Enregistrer** dans la barre d’outils.  
  
     ![Bouton Enregistrer une hiérarchie dérivée](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "Bouton Enregistrer une hiérarchie dérivée")  
  
7.  Faites glisser **fournisseur** des **niveaux disponibles : SuppliersInState** à **niveaux actuels : SuppliersInState**.  
  
     ![Entités et hiérarchies disponibles au niveau actuel](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "Entités et hiérarchies disponibles au niveau actuel")  
  
8.  Faites glisser **État** de **niveaux disponibles : SuppliersInState** à **niveaux actuels : SuppliersInState**. L’écran doit avoir les **niveaux actuels** , comme indiqué dans l’image suivante.  
  
     ![Niveaux actuels et aperçu de hiérarchie dérivée](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "Niveaux actuels et aperçu de hiérarchie dérivée")  
  
9. Dans la fenêtre d' **Aperçu** , développez **NY {New York}** et vous devriez voir un fournisseur dans cet État, comme indiqué dans l’image précédente.  
  
10. Basculez vers la page principale du **Data Manager maître** en cliquant sur **SQL Server Master Data Services 2012** en haut de la page.  
  
11. Cliquez sur **Explorateur**.  
  
12. Pointez la souris sur **hiérarchies** , puis cliquez sur **dérivé : SuppliersInState**.  
  
     ![Hiérarchies - Menu Derived:SuppliersInState](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "Hiérarchies - Menu Derived:SuppliersInState")  
  
13. Cliquez sur n’importe quel nœud d' **État** dans l' **arborescence** pour afficher les fournisseurs dans cet État dans le volet droit.  
  
     ![Hiérarchie dérivée dans l'Explorateur](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "Hiérarchie dérivée dans l'Explorateur")  
  
## <a name="next-step"></a>étape suivante  
 [Leçon 5 : Automatisation du nettoyage et de la mise en correspondance avec SSIS](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  
