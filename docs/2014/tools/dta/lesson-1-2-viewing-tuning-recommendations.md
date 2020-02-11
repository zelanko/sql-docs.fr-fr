---
title: Affichage des recommandations de paramétrage | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: e4e690c9-434f-4b01-b4de-0b905323ddd6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fe8d52d898db35698155518646f074e7167687a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66110180"
---
# <a name="viewing-tuning-recommendations"></a>Affichage des recommandations pour le paramétrage
  Cette tâche est basée sur la session de paramétrage que vous avez créée dans [Paramétrage d’une charge de travail](lesson-1-1-tuning-a-workload.md). Une fois que vous avez [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] réglé la base de données à l' [!INCLUDE[tsql](../../includes/tsql-md.md)] aide du [!INCLUDE[ssDE](../../includes/ssde-md.md)] script MyScript. SQL, l’Assistant Paramétrage du affiche ses résultats sous l’onglet **recommandations** . La tâche suivante présente l’onglet **recommandations** de l' [!INCLUDE[ssDE](../../includes/ssde-md.md)] interface graphique utilisateur de l’Assistant Paramétrage du et vous guide pour explorer les informations qu’elle fournit sur les résultats de la session de paramétrage.  
  
### <a name="view-tuning-recommendations"></a>Afficher les recommandations de paramétrage  
  
1.  Démarrez l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Consultez [Lancement de l’Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/database-engine-tuning-advisor.md). Assurez-vous de vous connecter à la même instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que celle utilisée au cours de l’exercice [Paramétrage d’une charge de travail](lesson-1-1-tuning-a-workload.md).  
  
2.  Double-cliquez sur **MySession** dans le volet **Moniteur de session** . [!INCLUDE[ssDE](../../includes/ssde-md.md)]L’Assistant Paramétrage du charge les informations de session de votre session de **** paramétrage précédente et affiche [!INCLUDE[ssDE](../../includes/ssde-md.md)] l’onglet recommandations. Notez que l’Assistant Paramétrage du n’a pas effectué de **recommandations de partition** , car vous avez accepté toutes les valeurs par défaut de l’option de paramétrage et **aucune partition** n’a été sélectionnée sous l’onglet **options de paramétrage** .  
  
3.  Sous l’onglet **Recommandations** , utilisez la barre de défilement en bas de la page à onglet pour afficher toutes les colonnes **Recommandations d’index** . Chaque ligne représente un objet de base de données (index ou vues indexées) que l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] recommande de supprimer ou de créer. Faites défiler l’écran vers la colonne la plus à droite et sélectionnez une **Définition**. [!INCLUDE[ssDE](../../includes/ssde-md.md)]L’Assistant Paramétrage affiche une fenêtre d' **aperçu de script SQL** dans [!INCLUDE[tsql](../../includes/tsql-md.md)] laquelle vous pouvez afficher le script qui crée ou supprime l’objet de base de données sur cette ligne. Cliquez sur **Terminer** pour fermer la fenêtre de prévisualisation.  
  
     Si vous avez du mal à trouver une **Définition** contenant un lien, décochez la case **Afficher les objets existants** en bas de la page à onglet pour diminuer le nombre de lignes affichées. Quand vous décochez cette case, l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] affiche uniquement les objets pour lesquels il a émis une recommandation. Cochez la case **Afficher les objets existants** pour visualiser tous les objets de base de données existant dans la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Utilisez la barre de défilement à droite de la page à onglet pour visualiser tous les objets.  
  
4.  Cliquez avec le bouton droit dans la grille du volet **Recommandations d’index** . Le menu contextuel qui s'affiche permet de sélectionner et de désélectionner des recommandations. Il permet également de modifier la police du texte de la grille.  
  
5.  Dans le menu **Actions** , cliquez sur **Enregistrer les recommandations** pour enregistrer toutes les recommandations dans un seul script [!INCLUDE[tsql](../../includes/tsql-md.md)] . Nommez le script `MySessionRecommendations.sql`.  
  
     Ouvrez le script MySessionRecommendations.sql dans l'Éditeur de requête de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour en afficher le contenu. Vous pouvez appliquer ces recommandations à la base de données exemple [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] en exécutant le script dans l'Éditeur de requête, mais ne le faites pas. Fermez le script dans l'Éditeur de requête sans l'exécuter.  
  
     L’autre méthode pour appliquer les recommandations consiste à cliquer sur **Appliquer les recommandations** dans le menu **Actions** de l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , mais n’appliquez pas ces recommandations maintenant.  
  
6.  Si plusieurs recommandations sont fournies sous l’onglet **Recommandations** , supprimez certaines lignes contenant des objets de base de données dans la grille **Recommandations d’index** .  
  
7.  Dans le menu **Actions** , cliquez sur **Évaluer les recommandations**. 
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] L'Assistant Paramétrage du moteur de base de données crée une nouvelle session de paramétrage qui permet d'évaluer un sous-ensemble des recommandations d'origine de la session MySession.  
  
8.  Tapez `EvaluateMySession` le nom de votre nouvelle **session**, puis cliquez sur le bouton **Démarrer l’analyse** dans la barre d’outils. Vous pouvez répéter les étapes 2 et 3 pour cette nouvelle session de paramétrage afin d'en visualiser les recommandations.  
  
## <a name="summary"></a>Résumé  
 Vous avez affiché le contenu de l’onglet **Recommandations** pour la session de paramétrage MySession et vous avez évalué un sous-ensemble de ces recommandations pour la nouvelle session de paramétrage EvaluateMySession.  
  
 L'évaluation d'un sous-ensemble de recommandations de paramétrage peut s'avérer nécessaire si vous pensez devoir modifier des options de paramétrage après l'exécution d'une session. Cela peut être le cas, par exemple, si vous configurez l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour qu’il tienne compte des vues indexées quand vous spécifiez des options de paramétrage pour une session, mais décidez après la génération des recommandations de réutiliser les vues indexées. Vous pouvez ensuite utiliser l’option **évaluer les recommandations** du menu **actions** pour que [!INCLUDE[ssDE](../../includes/ssde-md.md)] l’Assistant Paramétrage du réévalue la session sans tenir compte des vues indexées. Quand vous utilisez l’option **Évaluer les recommandations** , les recommandations générées sont appliquées hypothétiquement à la structure de création physique courante pour parvenir à la structure de création physique de la deuxième session de paramétrage.  
  
 Il est possible de visualiser davantage d’informations sur les résultats du paramétrage sous l’onglet **Rapports** , décrit dans la tâche suivante de la présente leçon.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Affichage des rapports de paramétrage](lesson-1-3-viewing-tuning-reports.md)  
  
  
