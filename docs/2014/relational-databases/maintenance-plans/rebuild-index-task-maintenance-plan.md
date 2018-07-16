---
title: Tâche Reconstruire l’index (Plan de maintenance) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reindex.f1
- reindex
helpviewer_keywords:
- Rebuild Index Task dialog box
ms.assetid: 33e2940b-139f-4563-b0cb-5683f08bd879
caps.latest.revision: 41
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 603f79bcbbe2ec42b05de28b3685c71f6cca9c69
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37268975"
---
# <a name="rebuild-index-task-maintenance-plan"></a>Tâche Reconstruire l'index (Plan de maintenance)
  Utilisez la boîte de dialogue **Tâche Reconstruire l’index** pour recréer les index des tables de la base de données en définissant un nouveau facteur de remplissage. Le facteur de remplissage détermine la quantité d'espace disponible sur chaque page de l'index pour permettre l'extension ultérieure de l'index. Au fur et à mesure que des données sont ajoutées à la table, l'espace libre se remplit parce que le facteur de remplissage n'est pas conservé. Réorganiser les pages d'index et les données permet de recouvrer de l'espace libre.  
  
 La **Tâche Reconstruire l'index** utilise l'instruction ALTER INDEX.  
  
## <a name="options"></a>Options  
 **Connexion**  
 Sélectionnez la connexion serveur à utiliser pour exécuter la tâche.  
  
 **Nouveau**  
 Crée une nouvelle connexion serveur à utiliser pour exécuter la tâche. La boîte de dialogue **Nouvelle connexion** est décrite ci-dessous.  
  
 **Bases de données**  
 Spécifie les bases de données faisant l'objet de cette tâche.  
  
-   **Toutes les bases de données**  
  
     Génère un plan de maintenance qui exécute des tâches de maintenance sur toutes les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , à l'exception de tempdb.  
  
-   **Toutes les bases de données système**  
  
     Génère un plan de maintenance qui exécute des tâches de maintenance sur chaque base de données système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , à l'exception de tempdb. Aucune tâche de maintenance n'est exécutée sur les bases de données créées par l'utilisateur.  
  
-   **Toutes les bases de données utilisateur**  
  
     Génère un plan de maintenance qui exécute des tâches de maintenance sur toutes les bases de données créées par l'utilisateur. Aucune tâche de maintenance n'est exécutée sur les bases de données système de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Ces bases de données**  
  
     Génère un plan de maintenance qui n'exécute les tâches de maintenance que sur les bases de données sélectionnées. Si vous choisissez cette option, sélectionnez au moins une base de données.  
  
    > [!NOTE]  
    >  Les plans de maintenance sont exécutés uniquement sur des bases de données définies au niveau de compatibilité 80 ou plus. Les bases de données définies au niveau de compatibilité 70 ou moins ne sont pas affichées.  
  
 **Objet**  
 Limite la grille de **Sélection** à l’affichage des tables et/ou des vues.  
  
 **Sélection**  
 Spécifie les tables ou les index faisant l'objet de cette tâche. Non disponible quand **Tables et vues** est sélectionné dans la zone Objet.  
  
 **Réorganiser les pages avec la quantité d’espace libre par défaut**  
 Permet de supprimer les index sur les tables de la base de données et de les recréer avec le facteur de remplissage spécifié lors de la création des index.  
  
 **Modifier l’espace disponible par pourcentage de page de**  
 Provoque la suppression des index des tables de la base de données et leur recréation avec un nouveau facteur de remplissage calculé automatiquement, la quantité d'espace libre spécifiée étant réservée dans les pages d'index. Plus le pourcentage est élevé, plus il y a d'espace libre réservé dans les pages d'index et plus l'index croît. Les valeurs valides sont comprises entre 0 et 100.  
  
 **Trier les résultats dans tempdb**  
 Utilisez la `SORT_IN_TEMPDB`option qui détermine où les résultats de tri intermédiaires générés pendant la création d’index, sont temporairement stockés. Si aucune opération de tri n’est requise ou si le tri peut être effectué dans la mémoire, l’option `SORT_IN_TEMPDB`est ignorée.  
  
 **Conserver l’index en ligne lors de la réindexation**  
 Utilisez l'option `ONLINE` qui permet aux utilisateurs d'accéder à la table sous-jacente ou aux données d'index cluster, ainsi qu'à tous les index non-cluster associés au cours des opérations d'index.  
  
> [!NOTE]  
>  Les opérations d'index en ligne ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **Vue T-SQL**  
 Affiche les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] exécutées sur le serveur pour cette tâche, selon les options sélectionnées.  
  
> [!NOTE]  
>  Si le nombre d'objets impliqués est élevé, l'affichage des instructions peut prendre un temps considérable.  
  
## <a name="new-connection-dialog-box"></a>Boîte de dialogue Nouvelle connexion  
 **Nom de la connexion**  
 Entrez un nom pour la nouvelle connexion.  
  
 **Sélectionnez ou entrez un nom de serveur.**  
 Sélectionnez un serveur auquel établir la connexion pour exécuter la tâche.  
  
 **Actualiser**  
 Actualise la liste des serveurs disponibles.  
  
 **Entrez des informations pour vous connecter au serveur**  
 Spécifiez le mode d'authentification sur le serveur.  
  
 **Utiliser la sécurité intégrée à Windows NT**  
 Se connecte à une instance de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] à l'aide de l'authentification Windows.  
  
 **Utiliser un nom d'utilisateur et un mot de passe spécifiques**  
 Se connecte à une instance de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cette option n'est pas disponible.  
  
 **Nom d'utilisateur**  
 Fournit le nom d'utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à utiliser pour l'authentification. Cette option n'est pas disponible.  
  
 **Mot de passe**  
 Fournit un mot de passe à utiliser pour l'authentification. Cette option n'est pas disponible.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)   
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [Option SORT_IN_TEMPDB pour les index](../indexes/indexes.md)   
 [Instructions pour les opérations d'index en ligne](../indexes/guidelines-for-online-index-operations.md)   
 [Fonctionnement des opérations d'index en ligne](../indexes/how-online-index-operations-work.md)   
 [Exécuter des opérations en ligne sur les index](../indexes/perform-index-operations-online.md)  
  
  
