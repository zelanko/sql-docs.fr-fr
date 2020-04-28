---
title: 'Tâche 1 (condition préalable) : suppression des données des fournisseurs dans MDS | Microsoft Docs'
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81484629"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a>Tâche 1 (prérequis) : Suppression de données de fournisseur dans MDS
  Dans cette tâche, vous allez supprimer les données des fournisseurs stockées dans MDS. Vous avez chargé les données manuellement à l’aide du **complément MDS pour Excel** dans la leçon précédente. Le package SSIS que vous créez dans cette leçon charge automatiquement les données dans MDS pour vous. Par conséquent, avant de tester le package SSIS, vous devez supprimer les données des fournisseurs dans MDS, ainsi que la hiérarchie dérivée, les entités Fournisseur et État, et créer l'entité Fournisseur sans données.  
  
1.  Lancez le **Data Manager maître** en accédant `http://localhost/MDS` à ou au site Web et à l’application que vous avez spécifiés lors de la configuration de MDS. Si vous avez conservé le **Data Manager maître** ouvert, cliquez sur **SQL Server Master Data Services 2012** en haut pour basculer vers la **page d’hébergement**.  
  
2.  Cliquez sur **administration de système** dans la section **tâches administratives** .  
  
3.  Pointez la souris sur **gérer** dans le menu et cliquez sur **hiérarchies dérivées**. Vous devez supprimer la hiérarchie dérivée **SuppliersInState** avant de supprimer les entités dans le modèle **Suppliers** .  
  
4.  Sélectionnez **SuppliersInState** dans la liste **hiérarchie dérivée** , puis cliquez sur le bouton **X (supprimer)** dans la barre d’outils.  
  
5.  Cliquez sur **OK** pour confirmer la suppression.  
  
6.  Pointez la souris sur **gérer** dans le menu et cliquez sur **entités**.  
  
7.  Cliquez sur **fournisseur** , puis sur le bouton **Supprimer (X)** de la barre d’outils pour supprimer l’entité. Cliquez sur **OK** dans les boîtes de message.  
  
8.  Répétez l’étape précédente pour supprimer l’entité **État** .  
  
9. Ne fermez pas le **Data Manager maître**.  
  
10. Basculez vers la fenêtre Excel dans laquelle le fichier **Suppliers. xls nettoyé et mis en correspondance** est ouvert. Basculez vers l’onglet **Feuil1** en bas.  
  
11. Sélectionnez uniquement la **première ligne avec des en-têtes**. Ne sélectionnez aucune autre ligne. Vous souhaitez créer les entités en fonction des colonnes Excel, mais vous ne souhaitez pas télécharger de données. Par conséquent, sélectionnez uniquement la première ligne avec les en-têtes.  
  
12. Dans la barre de menus, cliquez sur **données** de référence.  
  
13. Cliquez sur **créer une entité** dans le ruban.  
  
14. Dans la boîte de dialogue **gérer les connexions** , si vous ne voyez pas la connexion au **serveur MDS local** sous **connexions existantes**, procédez comme suit :  
  
    1.  Sélectionnez **créer une nouvelle connexion**, puis cliquez sur le bouton **nouveau** .  
  
    2.  Dans la boîte de dialogue Ajouter une nouvelle connexion, tapez **serveur MDS local** pour **Description** et **\/http:/localhost/MDS** pour **adresse du serveur MDS**, puis cliquez sur **OK** pour fermer la boîte de dialogue.  
  
15. Dans la boîte de dialogue **gérer les connexions** , sélectionnez **serveur MDS local** (`http://localhost/MDS`), puis cliquez sur **tester** pour tester la connexion. Cliquez sur **OK** dans le message de confirmation.  
  
16. Cliquez sur **connexion** pour établir une connexion au serveur MDS.  
  
17. Dans la boîte de dialogue **créer une entité** , procédez comme suit :  
  
    1.  Confirmez que la **plage** est définie sur **$1 : $1**.  
  
    2.  Sélectionnez **Suppliers** pour **Model**.  
  
    3.  Sélectionnez **Version_1** pour **version**.  
  
    4.  Tapez **Supplier** pour **nouveau nom d’entité**.  
  
    5.  Sélectionnez **RéfFournisseur** comme **code**.  
  
    6.  Sélectionnez **nom du fournisseur** pour **nom**.  
  
    7.  Cliquez sur **OK** pour créer l’entité et fermer la boîte de dialogue.  
  
18. Fermez **Excel** et **n’enregistrez pas** le fichier.  
  
19. Dans **Data Manager maître**, actualisez le navigateur Internet et confirmez que l’entité **fournisseur** est affichée dans la liste.  
  
20. Basculez vers la **page d’hébergement** en cliquant sur **SQL Server 2012 Master Data Services** en haut.  
  
21. Vérifiez que l’option **Supplier** Model est sélectionnée pour **model** et que **Version_1** est sélectionné pour **version**.  
  
22. Cliquez sur **Explorateur**. Notez que l’entité **Supplier** avec tous les attributs est créée sans **valeur**.  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 2 &#40;&#41; facultative : création d’une vue d’abonnement MDS à l’aide du Data Manager maître](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  
