---
title: "Générer un script pour une table | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea88d736-849e-4368-b55d-06aeee097bf3
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 5db067d5a2fe5bbf9953484c9a999ed7b1fcddae
ms.openlocfilehash: 422a81da1656b9b5c72fdcf1e71979ff0c8c058f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/31/2017

---
# <a name="lesson-2-6---script-a-table"></a>Leçon 2-6 - Générer un script pour une table
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] peut créer des scripts pour sélectionner, insérer, mettre à jour et supprimer des tables et également pour créer, modifier, supprimer ou exécuter des procédures stockées.  
  
Vous pouvez parfois avoir besoin d'utiliser un script avec plusieurs options permettant, par exemple, de supprimer et de créer une procédure ou bien de créer une table puis de la modifier. Pour créer des scripts combinés, enregistrez le premier script dans une fenêtre de l’Éditeur de requête et le second dans le Presse-papiers afin de le copier dans la fenêtre après le premier script.  
  
 
1.  Dans l’Explorateur d’objets, développez votre serveur, puis **Bases de données**, [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]et enfin, **Tables**, cliquez avec le bouton droit sur **HumanResources.Employee**, puis pointez sur **Générer un script de la table en tant que**.  
  
2.  Le menu contextuel propose sept options de script : **CREATE To**, **DROP To**, **DROP and CREATE To**, **SELECT To**, **INSERT To**, **UPDATE To**et **DELETE To**. Pointez sur **UPDATE To**, puis cliquez sur **Nouvelle fenêtre d’éditeur de requête**.  
  
3.  Une nouvelle fenêtre de l'Éditeur de requête s'ouvre et présente la connexion établie ainsi que l'instruction de mise à jour dans sa totalité.  
  
    Cet exercice montre comment la fonction de création de script peut faire plus que simplement automatiser la création d'une table ou d'une procédure stockée au moyen d'un script. Cette nouvelle fonctionnalité peut vous aider à ajouter rapidement des scripts de manipulation de données à votre projet et à exécuter facilement des procédures stockées au moyen d'un script. Cela peut représenter un gain de temps considérable pour les tables et les procédures qui comptent une quantité importante de champs.  
  
 
  
  
  

