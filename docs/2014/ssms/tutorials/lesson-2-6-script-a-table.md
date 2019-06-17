---
title: Générer un script pour une table | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ea88d736-849e-4368-b55d-06aeee097bf3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 22fae65a5e62be579f751dd3d6d3d0c9a73e7409
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63316398"
---
# <a name="script-a-table"></a>Générer un script pour une table
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] peut créer des scripts pour sélectionner, insérer, mettre à jour et supprimer des tables et également pour créer, modifier, supprimer ou exécuter des procédures stockées.  
  
 Vous pouvez parfois avoir besoin d'utiliser un script avec plusieurs options permettant, par exemple, de supprimer et de créer une procédure ou bien de créer une table puis de la modifier. Pour créer des scripts combinés, enregistrez le premier script dans une fenêtre de l’Éditeur de requête et le second dans le Presse-papiers afin de le copier dans la fenêtre après le premier script.  
  
## <a name="creating-an-update-script"></a>Création d'un script de mise à jour  
  
#### <a name="to-create-the-insert-script-for-a-table"></a>Pour créer le script d'insertion pour une table  
  
1.  Dans l’Explorateur d’objets, développez votre serveur, puis **Bases de données**, [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]et enfin, **Tables**, cliquez avec le bouton droit sur **HumanResources.Employee**, puis pointez sur **Générer un script de la table en tant que**.  
  
2.  Le menu contextuel propose sept options de script : **CRÉER à**, **DROP pour**, **DROP et CREATE dans**, **Sélectionnez cette option pour**, **insérer à**, **mise à jour de**, et **DELETE To**. Pointez sur **UPDATE To**, puis cliquez sur **Nouvelle fenêtre d’éditeur de requête**.  
  
3.  Une nouvelle fenêtre de l'Éditeur de requête s'ouvre et présente la connexion établie ainsi que l'instruction de mise à jour dans sa totalité.  
  
     Cet exercice montre comment la fonction de création de script peut faire plus que simplement automatiser la création d'une table ou d'une procédure stockée au moyen d'un script. Cette nouvelle fonctionnalité peut vous aider à ajouter rapidement des scripts de manipulation de données à votre projet et à exécuter facilement des procédures stockées au moyen d'un script. Cela peut représenter un gain de temps considérable pour les tables et les procédures qui comptent une quantité importante de champs.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Résumé : Écriture d’instructions Transact-SQL](../../tutorials/summary-writing-transact-sql.md)  
  
  
