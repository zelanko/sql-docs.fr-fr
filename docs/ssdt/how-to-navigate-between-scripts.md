---
title: 'Procédure : naviguer entre des scripts | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.editor.howto.navigate
ms.assetid: 8664bde5-86ff-4e8b-b5a6-af003316f6ad
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b06fbf69aa5a9d1c9354907f953d0fa98e8f9d40
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085671"
---
# <a name="how-to-navigate-between-scripts"></a>Procédure : naviguer entre des scripts
L'Éditeur Transact\-SQL pour le développement hors connexion fournit deux outils de navigation utiles qui sont familiers aux utilisateurs de Visual Studio : Atteindre la définition et Rechercher toutes les références. Vous pouvez, par exemple, cliquer avec le bouton droit sur un nom de la table et utiliser « Rechercher toutes les références » pour répertorier toutes les références à la table dans le projet. Vous pouvez double-cliquer sur le résultat d'une recherche pour accéder à un fichier de code spécifique. Dans ce fichier, vous pouvez recliquer avec le bouton droit sur le nom de la table et utiliser « Atteindre la définition » pour revenir à la définition de la table.  
  
> [!WARNING]  
> Les procédures suivantes utilisent les entités créées dans les procédures précédentes des sections [Développement de base de données connectée](../ssdt/connected-database-development.md) et [Développement de base de données hors connexion orientée projet](../ssdt/project-oriented-offline-database-development.md).  
  
### <a name="to-navigate-between-scripts"></a>Pour naviguer entre des scripts  
  
1.  Dans l'**Explorateur de solutions**, développez le dossier **Fonctions** et double-cliquez sur le fichier **GetProductsBySupplier.sql**.  
  
2.  Cliquez avec le bouton droit `Products` sur cette ligne de code et sélectionnez **Atteindre la définition**.  
  
    ```  
    SELECT * from Products p  
    ```  
  
3.  Le fichier Products.sql s'ouvre automatiquement et affiche l'emplacement de la définition de type `Products`.  
  
4.  Revenez au fichier GetProductsBySupplier.sql. Cette fois-ci, sélectionnez **Rechercher toutes les références** dans le menu contextuel pour `Products`. Dans le volet **Résultats de la recherche de symbole**, vous verrez une liste des emplacements où la table `Products` est référencée. Double-cliquez sur l'un des résultats de la recherche pour accéder à l'emplacement de la référence.  
  
