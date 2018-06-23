---
title: 'Leçon 9 : générer et exécuter l’application | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f52d3f3a-0b09-4b34-9112-0b3655271587
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: fdb619e98fe28742ac6b96acc6419513addfae25
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041313"
---
# <a name="lesson-9-build-and-run-the-application"></a>Lesson 9: Build and Run the Application
  Après avoir créé un filtre de données pour la table de données, l'étape suivante consiste à générer et à exécuter l'application de site Web.  
  
### <a name="to-build-and-run-the-application"></a>Pour générer et exécuter l'application  
  
1.  Appuyez sur **CTRL+F5** pour exécuter la page Default.aspx sans débogage, ou appuyez sur F5 pour exécuter la page avec débogage.  
  
     Dans le cadre du processus de génération, le rapport est compilé et toutes les erreurs trouvées (comme une erreur de syntaxe dans une expression utilisée dans le rapport) sont ajoutées à la **Liste des tâches** située au bas de la fenêtre de Visual Studio.  
  
     La page Web apparaît dans le navigateur. Le contrôle ReportViewer affiche le rapport. Vous pouvez utiliser la barre d'outils pour parcourir le rapport, effectuer un zoom et exporter le rapport vers Excel.  
  
2.  Pointez la souris sur l'une des lignes sous la colonne **Nom** . Le curseur de la souris affiche le symbole de main.  
  
3.  Cliquez sur une valeur dans la colonne **Nom** . Le rapport enfant s'affiche avec les données filtrées correspondantes.  
  
4.  Cliquez sur l'icône **Revenir au rapport parent**, dans la barre d'outils de **ReportViewer** pour revenir au rapport **Parent** .  
  
     ![SSRS permet d’accéder à l’aide de ReportViewer](../../2014/tutorials/media/ssrs-drillthrough-report.png "ssrs permet d’accéder à l’aide de ReportViewer")  
  
5.  Fermez le navigateur.  
  
  