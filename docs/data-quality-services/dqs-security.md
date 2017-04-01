---
title: "S&#233;curit&#233; relative au magasin d&#39;objets blob distants (DQS) | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2012"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 921927f5-1b1e-452a-a79e-c691829fd826
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# S&#233;curit&#233; relative au magasin d&#39;objets blob distants (DQS)
  L'infrastructure de sécurité [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) est basée sur l'infrastructure de sécurité SQL Server. Un administrateur de base de données accorde à un utilisateur un jeu d'autorisations en associant l'utilisateur à un rôle DQS. Cette opération détermine les ressources DQS auxquelles l'utilisateur a accès ainsi que les activités fonctionnelles que l'utilisateur est autorisé à effectuer.  
  
## Rôles DQS  
 Il existe quatre rôles pour DQS. L'un d'eux est l'administrateur de base de données qui s'occupe principalement de l'installation du produit, de la maintenance de la base de données et de la gestion des utilisateurs. Ce rôle utilise principalement SQL Server Management Studio, plutôt que l'application [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Son rôle serveur est sysadmin.  
  
 Les trois autres rôles sont les travailleurs de l'information, les gestionnaires de données qui utilisent le produit directement en travaillant dans l'application [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Il s'agit des rôles suivants :  
  
-   Le **administrateur DQS** (rôle dqs_administrator) permettre effectuer toutes les opérations dans la portée du produit. L'administrateur peut modifier et exécuter un projet, créer et modifier une base de connaissances, terminer une activité, arrêter un processus dans une activité et modifier les paramètres de configuration et de services de données de référence. L'administrateur DQS ne peut pas, toutefois, installer le serveur ni ajouter de nouveaux utilisateurs. L'administrateur de base de données doit effectuer ces opérations.  
  
-   Le **éditeur de base de connaissances DQS** (rôle dqs_kb_editor) peut effectuer toutes les activités DQS, sauf pour l’administration. L'éditeur de base de connaissances peut modifier et exécuter un projet, et créer et modifier une base de connaissances. Il peut voir les données d'analyse des activités, mais ne peut pas terminer ni arrêter une activité, ni remplir des fonctions d'administration.  
  
-   Le **DQS Ko opérateur** (rôle dqs_kb_operator) peut modifier et exécuter un projet. Il ne peut effectuer aucun type de gestion des connaissances ; il ne peut pas créer ni modifier une base de connaissances. Il peut voir les données d'analyse des activités, mais ne peut pas terminer une activité ni remplir des fonctions d'administration.  
  
## Gestion des utilisateurs  
 L'administrateur de base de données (DBA) crée des utilisateurs DQS et les associe à des rôles DQS dans SQL Server Management Studio. Il gère leurs autorisations en ajoutant des connexions SQL en tant qu'utilisateurs de la base de données DQS_MAIN, puis en associant chaque utilisateur à un des rôles DQS. Chaque rôle reçoit des autorisations sur un ensemble de procédures stockées dans la base de données DQS_MAIN. Les trois rôles DQS ne sont pas disponibles pour les bases de données DQS_PROJECTS et DQS_STAGING_DATA.  
  
## Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Décrit comment créer un utilisateur et accorder des rôles DQS à l'aide de SQL Server Management Studio.|[Gérer des utilisateurs DQS dans SSMS](../Topic/Manage%20DQS%20Users%20in%20SSMS.md)|  
  
  