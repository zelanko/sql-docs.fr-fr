---
title: 'Tâche 2 (facultatif) : création d’une vue d’abonnement MDS à l’aide du Data Manager maître | Microsoft Docs'
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
ms.openlocfilehash: e6cbed42d059714dde1c82dbb50edf8ccc1dd65b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65484725"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>Tâche 2 (Facultatif) : Création d'une vue d'abonnement MDS à l'aide de Master Data Manager
  Dans cette tâche, vous allez créer une vue d’abonnement pour exposer l’entité **fournisseur** du modèle **fournisseurs** à d’autres applications. Vous n'allez pas utiliser cette vue dans cette version du didacticiel.  
  
1.  Basculez vers la page principale du **Data Manager maître** ([http://localhost/MDS](http://localhost/MDS)) en cliquant sur **SQL Server Master Data Services 2012** en haut.  
  
2.  Cliquez sur gestion de l' **intégration**.  
  
3.  Dans la barre de menus, cliquez sur **créer des vues** .  
  
     ![Bouton Ajouter une nouvelle vue d'abonnement](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "Bouton Ajouter une nouvelle vue d'abonnement")  
  
4.  Cliquez sur l’icône **+ (plus)** dans la barre d’outils pour créer une vue d’abonnement.  
  
5.  Dans le volet **créer une vue d’abonnement** , tapez **Suppliers** pour nom de la **vue d’abonnement**.  
  
6.  Sélectionnez **Suppliers** pour **Model**.  
  
7.  Sélectionnez **Version_1** pour **version**.  
  
8.  Sélectionnez **fournisseur** pour **entité**.  
  
9. Sélectionnez **les membres feuille** pour le **format**.  
  
     ![Bouton Enregistrer vue d'abonnement](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "Bouton Enregistrer vue d'abonnement")  
  
10. Cliquez sur **Enregistrer** dans la barre d’outils pour enregistrer la vue d’abonnement. Cette action crée une vue dans SQL Server **fournisseurs**nommés. Vous pouvez vérifier cela à l'aide de SQL Server Management Studio (SSMS).  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 3 &#40;&#41; facultative : examen des vues d’abonnement](task-3-optional-reviewing-the-subscription-views.md)  
  
  
