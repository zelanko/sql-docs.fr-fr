---
title: 'Tutoriel : Écriture d’instructions Transact-SQL | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL statements, tutorials
- Transact-SQL tutorials
- tutorials [Transact-SQL]
ms.assetid: 2addc9be-67d0-423d-a457-192fe9d7d058
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ac190d6099bca1a38ca2f286e6ce048fe5322e2a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054536"
---
# <a name="tutorial-writing-transact-sql-statements"></a>Didacticiel : écriture d'instructions Transact-SQL
  Bienvenue dans le didacticiel d'écriture d'instructions [!INCLUDE[tsql](../includes/tsql-md.md)] . Ce didacticiel s'adresse aux utilisateurs qui débutent dans l'écriture d'instructions SQL. Il permet aux nouveaux utilisateurs de débuter en passant en revue certaines instructions de base destinées à créer des tables et à insérer des données. Ce didacticiel utilise [!INCLUDE[tsql](../includes/tsql-md.md)], l'implémentation [!INCLUDE[msCoName](../includes/msconame-md.md)] de la norme SQL. Ce didacticiel constitue une brève introduction au langage [!INCLUDE[tsql](../includes/tsql-md.md)] mais ne remplace pas un cours de formation sur [!INCLUDE[tsql](../includes/tsql-md.md)] . Les instructions de ce didacticiel sont volontairement simples et n'ont pas pour objectif de traduire la complexité propre à une base de données de production type.  
  
> [!NOTE]  
>  Les utilisateurs de bases de données inexpérimentés préfèrent travailler avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en utilisant [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] au lieu d'écrire des instructions [!INCLUDE[tsql](../includes/tsql-md.md)].  
  
## <a name="finding-more-information"></a>Sources d'informations complémentaires  
 Pour plus d’informations sur une instruction particulière, recherchez le nom de l’instruction dans la documentation en ligne de SQL Server ou utilisez le Sommaire pour parcourir les 1 800 éléments de langage répertoriés par ordre alphabétique sous [Référence Transact-SQL &#40;moteur de base de données&#41;](/sql/t-sql/language-reference). Une autre stratégie efficace permettant de rechercher des informations consiste à rechercher des mots clés liés à la rubrique qui vous intéresse. Par exemple, si vous souhaitez savoir comment retourner un élément d’une date (le mois, par exemple), recherchez **dates [SQL Server]** dans l’index, puis sélectionnez **dateparts**. Vous accédez ainsi à la rubrique [DATEPART &#40;Transact-SQL&#41;](/sql/t-sql/functions/datepart-transact-sql). À titre d’autre exemple, pour savoir comment utiliser des chaînes, recherchez **fonctions de chaîne**. Vous accédez ainsi à la rubrique [Fonctions de chaîne &#40;Transact-SQL&#41;](/sql/t-sql/functions/string-functions-transact-sql).  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Ce didacticiel vous explique comment créer un base de données, une table dans la base de données, insérer des données dans la table, mettre à jour les données, lire les données, les supprimer et supprimer la table. Vous allez créer des vues et des procédures stockées, puis configurer un utilisateur pour la base de données et les données.  
  
 Ce didacticiel est divisé en trois leçons :  
  
 [Leçon 1 : Création des objets de base de données](lesson-1-creating-database-objects.md)  
 Dans cette leçon, vous allez créer une base de données, créer une table dans la base de données, insérer des données dans la table, mettre à jour et lire les données.  
  
 [Leçon 2 : Configuration des autorisations sur des objets de base de données](lesson-2-configuring-permissions-on-database-objects.md)  
 Dans cette leçon, vous allez créer une connexion et un utilisateur. Vous allez également créer une vue et une procédure stockée, puis octroyer à l'utilisateur l'autorisation sur la procédure stockée.  
  
 [Leçon 3 : Suppression des objets de base de données](lesson-3-1-deleting-database-objects.md)  
 Dans cette leçon, vous allez supprimer l'accès aux données, supprimer des données d'une table, supprimer la table, puis supprimer la base de données.  
  
## <a name="requirements"></a>Spécifications  
 Pour suivre ce didacticiel jusqu'à la fin, il n'est pas nécessaire de connaître le langage SQL mais vous devez avoir une connaissance de base des concepts propres aux bases de données, tels que les tables. Au cours de ce didacticiel, vous allez créer une base de données et créer un utilisateur Windows. Ces tâches demandent un niveau élevé d'autorisations, c'est pourquoi vous devez vous connecter à l'ordinateur en tant qu'administrateur.  
  
 Les programmes suivants doivent être installés sur votre système :  
  
-   Toute édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou Management Studio Express.  
  
-   Internet Explorer 6 ou version ultérieure.  
  
> [!NOTE]  
>  Lorsque vous passez en revue les didacticiels, nous vous recommandons d’ajouter les boutons **suivant** et **précédent** dans la barre d’outils de la visionneuse de documents.  
  
  
