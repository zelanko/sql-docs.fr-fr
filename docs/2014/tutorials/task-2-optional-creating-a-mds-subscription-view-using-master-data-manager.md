---
title: 'Tâche 2 (facultatif) : Création d’une vue d’abonnement MDS à l’aide de Master Data Manager | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b1245beb168f2781e5acca344eb412bde104e4c9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37284245"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>Tâche 2 (Facultatif) : Création d'une vue d'abonnement MDS à l'aide de Master Data Manager
  Dans cette tâche, vous créez une vue d’abonnement pour exposer le **fournisseur** entité dans le **fournisseurs** modèle pour d’autres applications. Vous n'allez pas utiliser cette vue dans cette version du didacticiel.  
  
1.  Basculez vers la page principale de **Master Data Manager** ([http://localhost/MDS](http://localhost/MDS)) en cliquant sur **SQL Server 2012 Master Data Services** en haut.  
  
2.  Cliquez sur **gestion de l’intégration**.  
  
3.  Cliquez sur **créer des vues** sur la barre de menus.  
  
     ![Ajoutez un nouveau bouton de vue d’abonnement](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "ajouter un nouveau bouton de vue d’abonnement")  
  
4.  Cliquez sur **+ (Plus)** icône sur la barre d’outils pour créer une vue d’abonnement.  
  
5.  Dans le **créer une vue d’abonnement** volet, tapez **fournisseurs** pour **nom de la vue abonnement**.  
  
6.  Sélectionnez **fournisseurs** pour **modèle**.  
  
7.  Sélectionnez **VERSION_1** pour **Version**.  
  
8.  Sélectionnez **fournisseur** pour **entité**.  
  
9. Sélectionnez **des membres feuille** pour **Format**.  
  
     ![Bouton de vue d’abonnement enregistrer](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "abonnement vue bouton Enregistrer")  
  
10. Cliquez sur **enregistrer** sur la barre d’outils pour enregistrer la vue d’abonnement. Cette action crée une vue dans SQL Server nommée **fournisseurs**. Vous pouvez vérifier cela à l'aide de SQL Server Management Studio (SSMS).  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 3 &#40;facultatif&#41;: examiner les vues d’abonnement](task-3-optional-reviewing-the-subscription-views.md)  
  
  
