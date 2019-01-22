---
title: 'Didacticiel : SQL Server Management Studio (SSMS) | Microsoft Docs'
ms.custom: ''
ms.date: 08/30/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.tutorialstart.ssms.f1
helpviewer_keywords:
- projects [SQL Server Management Studio], tutorials
- templates [SQL Server], SQL Server Management Studio
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- solutions [SQL Server Management Studio], tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: d2bade70-07cf-4d94-b5d2-88aecb538ed1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f8b1560ef694885ae0debbf06f2d61d23c5d0f66
ms.sourcegitcommit: 96032813f6bf1cba680b5e46d82ae1f0f2da3d11
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54299396"
---
# <a name="tutorials-for-sql-server-management-studio-ssms"></a>Tutoriels pour SQL Server Management Studio (SSMS)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

> [!div class="nextstepaction"]
> [Faites-nous part de vos commentaires sur la table des matières SQL Docs !](https://aka.ms/sqldocsurvey)

Le didacticiel SQL Server Management Studio (SSMS) vous présente l’environnement intégré pour la gestion de votre infrastructure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] présente une interface graphique pour configurer, surveiller et administrer les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il vous permet également de déployer, surveiller et mettre à niveau les composants de la couche Données utilisés par vos applications, comme les bases de données. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] fournit également des éditeurs de langage [!INCLUDE[tsql](../../includes/tsql-md.md)], MDX, DMX et XML pour modifier et déboguer des scripts.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  

Ces tutoriels vous aident à comprendre la présentation des informations dans SSMS et à tirer parti de ses fonctionnalités.
  
La meilleure façon de se familiariser avec SSMS est d’effectuer des exercices pratiques. Ces tutoriels vous permettent de vous familiariser avec les diverses fonctionnalités disponibles dans SSMS.  Ces tutoriels vous apprennent à gérer les composants de SSMS et à trouver les fonctionnalités utilisées régulièrement.  

Voici les sujets traités dans les tutoriels : 

  
- [Didacticiel : Se connecter à et interroger SQL Server avec SSMS](connect-query-sql-server.md)

    Dans ce tutoriel, vous allez apprendre à vous connecter à votre instance SQL Server. Vous allez également étudier quelques commandes T-SQL (Transact-SQL) de base pour créer, puis interroger une base de données. 

- [Didacticiel : Objets de script dans SSMS](scripting-ssms.md)

    Dans ce tutoriel, vous allez apprendre à générer le script de différents objets dans SSMS, dont les bases de données et les requêtes. 

- [Didacticiel : Utilisation de modèles dans SSMS](templates-ssms.md)
   
    Dans ce tutoriel, vous allez apprendre à utiliser les modèles prédéfinis dans SSMS. Les modèles sont une fonctionnalité peu connue qui stocke un nombre d’extraits de code Transact-SQL pour diverses tâches d’administration de base de données. 

- [Didacticiel : Configuration de SSMS](ssms-configuration.md)

    Dans ce tutoriel, vous apprenez les bases de la configuration de votre environnement SSMS, comme le changement de la disposition de l’environnement. Ce tutoriel explique également quels sont les différents composants SSMS. 
  

- [Didacticiel : Conseils et astuces supplémentaires pour utiliser SSMS](ssms-tricks.md)

    Dans ce tutoriel, vous allez découvrir d’autres conseils et astuces pour utiliser SSMS. Le tutoriel inclut les thèmes suivants :
    - Ajout et suppression de commentaires dans le texte
    - Mise en retrait du texte
    - Filtrage des objets dans l’Explorateur d’objets
    - Accès à votre journal des erreurs SQL Server
    - Recherche du nom de votre instance 
 
  
## <a name="requirements"></a>Spécifications  
Ce didacticiel est destiné aux administrateurs et aux développeurs de base de données expérimentés, qui ne connaissent pas [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], mais qui maîtrisent les concepts des base de données et de [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
Pour ce didacticiel, les éléments suivants doivent être installés :  

  -   Installez la dernière version de [SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md).  

La première section vous guide dans la création d’une base de données, mais les autres exemples de bases de données se trouvent ici : [Exemples de bases de données AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Les instructions de restauration des bases de données dans SSMS se trouvent ici : [Restauration d’une base de données](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 


  
## <a name="see-also"></a> Voir aussi  
[Didacticiels sur le moteur de base de données](../../relational-databases/database-engine-tutorials.md)          
  
  
  

