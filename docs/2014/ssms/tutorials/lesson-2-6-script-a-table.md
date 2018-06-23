---
title: Générer un script pour une table | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea88d736-849e-4368-b55d-06aeee097bf3
caps.latest.revision: 29
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 4f7605be808552de655ed89155f7956efb86cb75
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153371"
---
# <a name="script-a-table"></a>Générer un script pour une table
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] peut créer des scripts pour sélectionner, insérer, mettre à jour et supprimer des tables et également pour créer, modifier, supprimer ou exécuter des procédures stockées.  
  
 Vous pouvez parfois avoir besoin d'utiliser un script avec plusieurs options permettant, par exemple, de supprimer et de créer une procédure ou bien de créer une table puis de la modifier. Pour créer des scripts combinés, enregistrez le premier script dans une fenêtre de l’Éditeur de requête et le second dans le Presse-papiers afin de le copier dans la fenêtre après le premier script.  
  
## <a name="creating-an-update-script"></a>Création d'un script de mise à jour  
  
#### <a name="to-create-the-insert-script-for-a-table"></a>Pour créer le script d'insertion pour une table  
  
1.  Dans l’Explorateur d’objets, développez votre serveur, puis **Bases de données**, [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] et enfin, **Tables**, cliquez avec le bouton droit sur **HumanResources.Employee**, puis pointez sur **Générer un script de la table en tant que**.  
  
2.  Le menu contextuel propose sept options de script : **CREATE To**, **DROP To**, **DROP and CREATE To**, **SELECT To**, **INSERT To**, **UPDATE To**et **DELETE To**. Pointez sur **UPDATE To**, puis cliquez sur **Nouvelle fenêtre d’éditeur de requête**.  
  
3.  Une nouvelle fenêtre de l'Éditeur de requête s'ouvre et présente la connexion établie ainsi que l'instruction de mise à jour dans sa totalité.  
  
     Cet exercice montre comment la fonction de création de script peut faire plus que simplement automatiser la création d'une table ou d'une procédure stockée au moyen d'un script. Cette nouvelle fonctionnalité peut vous aider à ajouter rapidement des scripts de manipulation de données à votre projet et à exécuter facilement des procédures stockées au moyen d'un script. Cela peut représenter un gain de temps considérable pour les tables et les procédures qui comptent une quantité importante de champs.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Résumé : Écriture Transact-SQL](../../tutorials/summary-writing-transact-sql.md)  
  
  