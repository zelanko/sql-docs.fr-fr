---
title: 'Tâche 2 (Facultatif) : Création d’une vue d’abonnement MDS à l’aide de Master Data Manager ( Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: cc923792adc3fefb5ebaab9e225169648394c71f
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484709"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>Tâche 2 (facultatif) : Création d’une vue d’abonnement MDS à l’aide de Master Data Manager
  Dans cette tâche, vous créez une vue d’abonnement pour exposer **l’entité fournisseur** dans le modèle **Fournisseurs** à d’autres applications. Vous n'allez pas utiliser cette vue dans cette version du didacticiel.  
  
1.  Passez à la page principale`http://localhost/MDS`de Master Data **Manager** ( ) en cliquant sur **SQL Server 2012 Master Data Services** en haut.  
  
2.  Cliquez sur **La gestion de l’intégration**.  
  
3.  Cliquez **sur Créer des vues** sur la barre de menu.  
  
     ![Bouton Ajouter une nouvelle vue d'abonnement](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "Bouton Ajouter une nouvelle vue d'abonnement")  
  
4.  Cliquez **sur l’icône (Plus)** sur la barre d’outils pour créer une vue d’abonnement.  
  
5.  Dans le volet **Create Subscription View,** tapez le nom de vue **fournisseurs** **d’abonnement.**  
  
6.  Sélectionnez **les fournisseurs** pour **le modèle**.  
  
7.  Sélectionnez **VERSION_1** pour **la version**.  
  
8.  Sélectionnez **Fournisseur** pour **l’entité**.  
  
9. Sélectionnez les **membres Leaf** pour **Format**.  
  
     ![Bouton Enregistrer vue d'abonnement](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "Bouton Enregistrer vue d'abonnement")  
  
10. Cliquez **sur Enregistrer** sur la barre d’outils pour enregistrer la vue d’abonnement. Cette action crée une vue dans SQL Server nommé **Fournisseurs**. Vous pouvez vérifier cela à l'aide de SQL Server Management Studio (SSMS).  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 3 &#40;&#41; facultatif : Examen des vues d’abonnement](task-3-optional-reviewing-the-subscription-views.md)  
  
  
