---
title: 'Tâche 1 (Préalable) : Suppression des données des fournisseurs dans le SMD Microsoft Docs'
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
ms.openlocfilehash: 0290f033be47bec61e9ccce8465892d8cc98608c
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484629"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a>Tâche 1 (prérequis) : Suppression de données de fournisseur dans MDS
  Dans cette tâche, vous allez supprimer les données des fournisseurs stockées dans MDS. Vous avez téléchargé les données manuellement à l’aide **de MDS Excel Add-in** dans la leçon précédente. Le paquet SSIS que vous créez dans cette leçon téléchargera automatiquement les données sur MDS pour vous. Par conséquent, avant de tester le package SSIS, vous devez supprimer les données des fournisseurs dans MDS, ainsi que la hiérarchie dérivée, les entités Fournisseur et État, et créer l'entité Fournisseur sans données.  
  
1.  Lancez **Master Data** Manager `http://localhost/MDS` en naviguant vers ou sur le site Web et l’application que vous avez spécifiée lors de la configuration du MDS. Si vous maintenez le **Master Data Manager** ouvert, cliquez sur **SQL Server 2012 Master Data Services** en haut pour passer à la page **d’accueil**.  
  
2.  Cliquez sur **l’administration du système** dans la section **Tâches administratives.**  
  
3.  Planer la souris sur **Gérer** sur le menu et cliquez sur **Hiérarchies dérivées**. Vous devez supprimer la hiérarchie dérivée **SuppliersInState** avant de supprimer les entités du modèle **Fournisseurs.**  
  
4.  Sélectionnez **FournisseursInState** de la liste **de hiérarchie dérivée** et cliquez sur le bouton **X (Supprimer)** sur la barre d’outils.  
  
5.  Cliquez **sur OK** pour confirmer la suppression.  
  
6.  Planer la souris sur **Gérer** sur le menu et cliquez sur **entités**.  
  
7.  Cliquez sur **Fournisseur** et cliquez sur Supprimer (X) le bouton **Supprimer (X)** sur la barre d’outils pour supprimer l’entité. Cliquez **sur OK** sur les boîtes de messages.  
  
8.  Répétez l’étape précédente pour supprimer **l’entité d’État.**  
  
9. Ne fermez pas **Master Data Manager**.  
  
10. Passez à la fenêtre Excel qui a nettoyé et assorti le fichier **Suppliers.xls** ouvert. Passez à l’onglet **Feuille1** en bas.  
  
11. Sélectionnez seulement la **première rangée avec des en-têtes**. Ne sélectionnez pas d’autre rangée. Vous souhaitez créer les entités basées sur les colonnes Excel mais ne souhaitez pas télécharger de données. Par conséquent, sélectionnez uniquement la première ligne avec les en-têtes.  
  
12. Cliquez sur **Master Data** sur la barre du menu.  
  
13. Cliquez sur **Créer l’entité** à partir du ruban.  
  
14. Dans la boîte de dialogue **Manage Connections,** si vous ne voyez pas la connexion au **serveur MDS local** dans les **connexions existantes,** faites ce qui suit :  
  
    1.  Sélectionnez **Créer une nouvelle connexion**et cliquez sur **nouveau** bouton.  
  
    2.  Dans la boîte de dialogue Add New Connection, tapez **local MDS Server** pour **la description** et **http:\//localhost/MDS** pour **l’adresse du serveur MDS**, et cliquez **sur OK** pour fermer la boîte de dialogue.  
  
15. Dans la boîte de dialogue **Manage Connections,** sélectionnez **Local MDS Server** (),`http://localhost/MDS`cliquez sur **Test** pour tester la connexion. Cliquez sur **OK** dans le message de confirmation.  
  
16. Cliquez **sur Connectez-vous** pour établir une connexion au serveur MDS.  
  
17. Dans la boîte de dialogue **Create Entity,** faites ce qui suit :  
  
    1.  Confirmez que **la portée** est réglée à **1 $ : 1**$ .  
  
    2.  Sélectionnez **les fournisseurs** pour **le modèle**.  
  
    3.  Sélectionnez **VERSION_1** pour **la version**.  
  
    4.  **Fournisseur de** type pour le nouveau **nom d’entité**.  
  
    5.  Sélectionnez **SupplierID** pour **code**.  
  
    6.  Sélectionnez **nom du fournisseur** pour le **nom**.  
  
    7.  Cliquez **sur OK** pour créer l’entité et fermer la boîte de dialogue.  
  
18. Fermez **Excel** et **n’enregistrez pas** le fichier.  
  
19. Dans **Master Data Manager**, actualisez le navigateur Internet et confirmez que **l’entité fournisseur** est affichée dans la liste.  
  
20. Passez à la **page d’accueil** en cliquant sur **SQL Server 2012 Master Data Services** en haut.  
  
21. Confirmez que le modèle **Fournisseurs** est sélectionné pour **le modèle** et **VERSION_1** est sélectionné pour la **version**.  
  
22. Cliquez sur **Explorateur**. Notez que l’entité **fournisseur** avec tous les attributs est créé **sans valeurs**.  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 2 &#40;&#41; facultatif : Création d’une vue d’abonnement MDS à l’aide de Master Data Manager](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  
