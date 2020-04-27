---
title: Tâche Réorganiser l’index (Plan de maintenance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.defrag.f1
helpviewer_keywords:
- Reorganize Index Task dialog box
ms.assetid: e9cbebbd-f36f-4176-9832-382a46ac946c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a0f354280da857be236049a564a77716e93cd351
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62807064"
---
# <a name="reorganize-index-task-maintenance-plan"></a>Tâche Réorganiser l'index (Plan de maintenance)
  Utilisez la boîte de dialogue **Tâche Réorganiser l’index** pour réordonner les pages d’index dans un ordre qui rend les recherches plus efficaces. Cette tâche utilise l'instruction `ALTER INDEX REORGANIZE` avec des bases de données [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
## <a name="options"></a>Options  
 **Connection**  
 Sélectionnez la connexion serveur à utiliser pour exécuter la tâche.  
  
 **Nouveau**  
 Crée une nouvelle connexion serveur à utiliser pour exécuter la tâche. La boîte de dialogue **Nouvelle connexion** est décrite ci-dessous.  
  
 **Bases de données**  
 Spécifie les bases de données faisant l'objet de cette tâche.  
  
-   **Toutes les bases de données**  
  
     Génère un plan de maintenance qui exécute des tâches de maintenance sur toutes les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , à l'exception de tempdb.  
  
-   **Toutes les bases de données système**  
  
     Génère un plan de maintenance qui exécute des tâches de maintenance sur chaque base de données système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , à l'exception de **tempdb**. Aucune tâche de maintenance n'est exécutée sur les bases de données créées par l'utilisateur.  
  
-   **Toutes les bases de données utilisateur**  
  
     Génère un plan de maintenance qui exécute des tâches de maintenance sur toutes les bases de données créées par l'utilisateur. Aucune tâche de maintenance n'est exécutée sur les bases de données système de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Ces bases de données**  
  
     Génère un plan de maintenance qui n'exécute les tâches de maintenance que sur les bases de données sélectionnées. Si vous choisissez cette option, sélectionnez au moins une base de données.  
  
 **Object**  
 Limite la grille de **Sélection** à l’affichage des tables et/ou des vues.  
  
 **Sélection**  
 Spécifie les tables ou les index faisant l'objet de cette tâche. Non disponible quand **Tables et vues** est sélectionné dans la zone **Objet** .  
  
 **Compacter les objets importants**  
 Annule l'allocation de l'espace pour les tables et les vues si possible. Cette option utilise `ALTER INDEX LOB_COMPACTION = ON`.  
  
 **Vue T-SQL**  
 Affiche les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] exécutées sur le serveur pour cette tâche, selon les options sélectionnées.  
  
> [!NOTE]  
>  Si le nombre d'objets impliqués est élevé, l'affichage des instructions peut prendre un temps considérable.  
  
## <a name="new-connection-dialog-box"></a>Boîte de dialogue Nouvelle connexion  
 **Nom de connexion**  
 Entrez un nom pour la nouvelle connexion.  
  
 **Sélectionnez ou entrez un nom de serveur.**  
 Sélectionnez un serveur auquel établir la connexion pour exécuter la tâche.  
  
 **Actualiser**  
 Actualise la liste des serveurs disponibles.  
  
 **Entrez des informations pour vous connecter au serveur**  
 Spécifiez le mode d'authentification sur le serveur.  
  
 **Utiliser la sécurité intégrée à Windows NT**  
 Permet de se connecter à une instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] avec l’authentification [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Utiliser un nom d'utilisateur et un mot de passe spécifiques**  
 Permet de se connecter à une instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] en utilisant l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette option n'est pas disponible.  
  
 **Nom d'utilisateur**  
 Fournit le nom d'utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à utiliser pour l'authentification. Cette option n'est pas disponible.  
  
 **Mot de passe**  
 Fournit un mot de passe à utiliser pour l'authentification. Cette option n'est pas disponible.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [DBCC INDEXDEFRAG &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-indexdefrag-transact-sql)  
  
  
