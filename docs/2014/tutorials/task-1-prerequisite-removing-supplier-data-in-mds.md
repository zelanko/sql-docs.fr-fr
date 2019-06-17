---
title: 'Tâche 1 (prérequis) : Supprimer les données des fournisseurs dans MDS | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6f0a4287-7fd4-4f18-b7e4-a5191a9d4a3c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 84c0acceb4953b819cb5696c4ef90c39e4376846
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65481223"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a>Tâche 1 (prérequis) : Suppression de données de fournisseur dans MDS
  Dans cette tâche, vous allez supprimer les données des fournisseurs stockées dans MDS. Vous avez téléchargé les données manuellement à l’aide **complément MDS pour Excel** dans la leçon précédente. Le package SSIS que vous créez dans cette leçon téléchargera automatiquement les données dans MDS pour vous. Par conséquent, avant de tester le package SSIS, vous devez supprimer les données des fournisseurs dans MDS, ainsi que la hiérarchie dérivée, les entités Fournisseur et État, et créer l'entité Fournisseur sans données.  
  
1.  Lancez **Master Data Manager** en accédant à **http://localhost/MDS** ou le site Web et l’application que vous avez spécifié lorsque la configuration de MDS. Si vous avez conservé le **Master Data Manager** ouvrir, cliquez sur **SQL Server 2012 Master Data Services** en haut pour basculer vers le **page d’accueil**.  
  
2.  Cliquez sur **Administration système** dans le **tâches administratives** section.  
  
3.  Pointez la souris sur **gérer** sur le menu et cliquez sur **hiérarchies dérivées**. Vous devez supprimer la hiérarchie dérivée **SuppliersInState** avant de supprimer les entités dans le **fournisseurs** modèle.  
  
4.  Sélectionnez **SuppliersInState** à partir de la **hiérarchie dérivée** liste et cliquez sur **X (Delete)** dans la barre d’outils.  
  
5.  Cliquez sur **OK** pour confirmer la suppression.  
  
6.  Pointez la souris sur **gérer** sur le menu et cliquez sur **entités**.  
  
7.  Cliquez sur **fournisseur** et cliquez sur **supprimer (X)** dans la barre d’outils pour supprimer l’entité. Cliquez sur **OK** sur les boîtes de message.  
  
8.  Répétez l’étape précédente pour supprimer **état** entité.  
  
9. Ne fermez pas **Master Data Manager**.  
  
10. Basculez vers la fenêtre Excel qui a **Cleansed and Matched Suppliers.xls** le fichier est ouvert. Basculez vers le **Sheet1** onglet en bas.  
  
11. Sélectionnez uniquement le **première ligne avec les en-têtes**. Ne sélectionnez pas des autres lignes. Vous souhaitez créer les entités en fonction des colonnes Excel mais que vous ne souhaitez pas charger des données. Par conséquent, sélectionnez uniquement la première ligne avec les en-têtes.  
  
12. Cliquez sur **données maîtres** sur la barre de menus.  
  
13. Cliquez sur **créer une entité** à partir du ruban.  
  
14. Dans **gérer les connexions** boîte de dialogue, si vous ne voyez pas la connexion à **serveur local MDS** sous **connexions existantes**, procédez comme suit :  
  
    1.  Sélectionnez **créer une nouvelle connexion**, puis cliquez sur **New** bouton.  
  
    2.  Dans la boîte de dialogue Ajouter une nouvelle connexion, tapez **serveur Local MDS** pour **Description** et **http://localhost/MDS** pour **adresse du serveur MDS**, Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
15. Dans **gérer les connexions** boîte de dialogue, sélectionnez **serveur Local MDS** (http://localhost/MDS), cliquez sur **tester** pour tester la connexion. Cliquez sur **OK** dans le message de confirmation.  
  
16. Cliquez sur **Connect** pour établir une connexion au serveur MDS.  
  
17. Dans le **créer une entité** boîte de dialogue zone, procédez comme suit :  
  
    1.  Vérifiez que **plage** a la valeur **$1 : $1**.  
  
    2.  Sélectionnez **fournisseurs** pour **modèle**.  
  
    3.  Sélectionnez **VERSION_1** pour **Version**.  
  
    4.  Type **fournisseur** pour **nouveau nom d’entité**.  
  
    5.  Sélectionnez **SupplierID** pour **Code**.  
  
    6.  Sélectionnez **Supplier Name** pour **nom**.  
  
    7.  Cliquez sur **OK** pour créer l’entité et de fermer la boîte de dialogue.  
  
18. Fermer **Excel** et **n’enregistrez pas** le fichier.  
  
19. Dans **Master Data Manager**, actualisez le navigateur internet et vérifiez que **fournisseur** entité est affichée dans la liste.  
  
20. Basculez vers le **page d’accueil** en cliquant sur **SQL Server 2012 Master Data Services** en haut.  
  
21. Vérifiez que **fournisseurs** modèle est sélectionné pour **modèle** et **VERSION_1** est sélectionné pour **Version**.  
  
22. Cliquez sur **Explorateur**. Notez que le **fournisseur** entité avec tous les attributs est créée avec **aucune valeur**.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 2 &#40;facultatif&#41;: Création d’une vue d’abonnement MDS à l’aide de Master Data Manager](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  
