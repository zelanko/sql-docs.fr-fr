---
title: 'Leçon 6 : ajouter un contrôle ReportViewer à l’application | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 51b08dce6f232bb08fd1d5f41bc1976aaa410331
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043302"
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a>Leçon 6 : Ajouter un contrôle ReportViewer à l'application
  Après avoir conçu le rapport enfant à l'aide de l'Assistant Rapport, l'étape suivante consiste à ajouter un contrôle ReportViewer à l'application de site Web.  
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a>Pour ajouter un contrôle ReportViewer à l'application  
  
1.  Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur **Default.aspx**, puis sélectionnez **Concepteur de vues**.  
  
2.  Dans le groupe **Extensions AJAX** de la fenêtre **Boîte à outils** , faites glisser un contrôle **ScriptManager** vers l'aire de conception.  
  
3.  Depuis le groupe **Création de rapports** , faites glisser un contrôle **ReportViewer** vers l'aire de conception sous le contrôle **ScriptManager** .  
  
4.  Ouvrez la fenêtre **Tâches ReportViewer** en cliquant sur la flèche située dans le coin supérieur droit du contrôle **ReportViewer** .  
  
5.  Dans la zone **Choisir un rapport** , sélectionnez le rapport parent que vous avez créé.  
  
     Lorsque vous sélectionnez un rapport, les instances de sources de données utilisées dans le rapport sont créées automatiquement. Le code est généré pour instancier chaque objet DataTable (et son conteneur [DataSet](http://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) ). Un contrôle [ObjectDataSource](http://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx) est ajouté à l'aire de conception, correspondant à chaque source de données utilisée dans le rapport. Ce contrôle de source de données est configuré automatiquement.  
  
     Si vous utilisez Microsoft Visual Studio 2012, assurez-vous que le contrôle ObjectDataSource est lié à DataSet1 qui est le nom complet de l'espace de noms de projet, vérifiez si le nom complet est indiqué dans la zone de liste déroulante **Choisir un objet métier** (par exemple, Projectnamespace.DataSet1TableAdapters.ProductTableAdapter). Pour accéder à la zone de liste, cliquez avec le bouton droit sur ObjectDataSource, puis sélectionnez **Configurer la source de données**.  
  
6.  Dans le menu Générer, cliquez sur Générer le site Web.  
  
     Le rapport est compilé et toutes les erreurs, comme une erreur de syntaxe dans une expression de rapport, apparaissent dans la zone **Liste d'erreurs** . Cliquez sur **Liste d'erreurs** en bas de la fenêtre de Visual Studio pour afficher la zone **Liste d'erreurs** .  
  
## <a name="next-task"></a>Tâche suivante  
 Vous venez d'ajouter un contrôle ReportViewer dans l'application de site Web. Vous allez à présent ajouter une action d'extraction dans le rapport parent.  
  
  