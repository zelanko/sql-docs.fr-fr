---
title: Tâche Vérifier l’intégrité de la base de données (Plan de maintenance) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.maintplanproperties.integrity.f1
- sql12.swb.maint.integrity.f1
helpviewer_keywords:
- Check Database Integrity Task dialog box
ms.assetid: 3534494a-5dfe-4738-b49a-e7fabd731c47
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f786755a3b7ed5d991b4cf0e32c067e355c111ae
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85024750"
---
# <a name="check-database-integrity-task-maintenance-plan"></a>Tâche Vérifier l'intégrité de la base de données (Plan de maintenance)
  Utilisez la boîte de dialogue **Tâche Vérifier l’intégrité de la base de données** pour vérifier l’intégrité d’allocation et de structure des tables utilisateur et système et des index de la base de données, en exécutant l’instruction `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] . L'exécution de `DBCC` garantit que tous les problèmes d'intégrité de la base de données seront rapportés, ce qui permet de les signaler plus tard à l'administrateur système ou au propriétaire de la base de données.  
  
## <a name="options"></a>Options  
 **Connection**  
 Sélectionnez la connexion serveur à utiliser pour exécuter la tâche.  
  
 **Nouveau**  
 Crée une nouvelle connexion serveur à utiliser pour exécuter la tâche. La boîte de dialogue **Nouvelle connexion** est décrite ci-dessous.  
  
 **Bases de données**  
 Spécifie les bases de données faisant l'objet de cette tâche.  
  
-   **Toutes les bases de données**  
  
     Génère un plan de maintenance qui exécute les tâches de maintenance sur toutes les bases de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à l’exception de **tempdb**.  
  
-   **Toutes les bases de données système**  
  
     Génère un plan de maintenance qui exécute des tâches de maintenance sur chaque base de données système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , à l'exception de **tempdb**. Aucune tâche de maintenance n'est exécutée sur les bases de données créées par l'utilisateur.  
  
-   **Toutes les bases de données utilisateur**  
  
     Génère un plan de maintenance qui exécute des tâches de maintenance sur toutes les bases de données créées par l'utilisateur. Aucune tâche de maintenance n'est exécutée sur les bases de données système de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Ces bases de données**  
  
     Génère un plan de maintenance qui n'exécute les tâches de maintenance que sur les bases de données sélectionnées. Si vous choisissez cette option, sélectionnez au moins une base de données.  
  
    > [!NOTE]  
    >  Les plans de maintenance sont exécutés uniquement sur des bases de données définies au niveau de compatibilité 80 ou plus. Les bases de données définies au niveau de compatibilité 70 ou moins ne sont pas affichées.  
  
 **Inclure les index**  
 Vérifie l'intégrité de toutes les pages d'index ainsi que des pages de données des tables.  
  
 **Vue T-SQL**  
 Affiche les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] exécutées sur le serveur pour cette tâche, selon les options sélectionnées.  
  
> [!NOTE]  
>  Si le nombre d'objets impliqués est élevé, l'affichage des instructions peut prendre un temps considérable.  
  
## <a name="new-connection-dialog-box"></a>Boîte de dialogue Nouvelle connexion  
 **Nom de connexion**  
 Entrez un nom pour la nouvelle connexion.  
  
 **Sélectionnez ou entrez un nom de serveur.**  
 Sélectionnez un serveur auquel établir la connexion pour exécuter la tâche.  
  
 **Actualisation**  
 Actualise la liste des serveurs disponibles.  
  
 **Entrez des informations pour vous connecter au serveur**  
 Spécifiez le mode d'authentification sur le serveur.  
  
 **Utiliser la sécurité intégrée à Windows NT**  
 Connectez-vous à une instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] avec l’authentification Windows.  
  
 **Utiliser un nom d'utilisateur et un mot de passe spécifiques**  
 Connectez-vous à une instance du à l’aide de l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentification. Cette option n'est pas disponible.  
  
 **Nom d'utilisateur**  
 Fournit le nom d'utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à utiliser pour l'authentification. Cette option n'est pas disponible.  
  
 **Mot de passe**  
 Fournit un mot de passe à utiliser pour l'authentification. Cette option n'est pas disponible.  
  
## <a name="see-also"></a>Voir aussi  
 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
