---
title: Sécurité dans DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 921927f5-1b1e-452a-a79e-c691829fd826
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ae5ff9bf9fe78ca7230865c6f3df5f2b1333f005
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65480857"
---
# <a name="dqs-security"></a>Sécurité DQS
  L'infrastructure de sécurité [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) est basée sur l'infrastructure de sécurité SQL Server. Un administrateur de base de données accorde à un utilisateur un jeu d'autorisations en associant l'utilisateur à un rôle DQS. Cette opération détermine les ressources DQS auxquelles l'utilisateur a accès ainsi que les activités fonctionnelles que l'utilisateur est autorisé à effectuer.  
  
## <a name="dqs-roles"></a>Rôles DQS  
 Il existe quatre rôles pour DQS. L'un d'eux est l'administrateur de base de données qui s'occupe principalement de l'installation du produit, de la maintenance de la base de données et de la gestion des utilisateurs. Ce rôle utilise principalement SQL Server Management Studio, plutôt que l'application [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Son rôle serveur est sysadmin.  
  
 Les trois autres rôles sont les travailleurs de l'information, les gestionnaires de données qui utilisent le produit directement en travaillant dans l'application [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Il s'agit des rôles suivants :  
  
-   L' **administrateur DQS** (rôle dqs_administrator) peut effectuer toutes les opérations dans l'étendue du produit. L'administrateur peut modifier et exécuter un projet, créer et modifier une base de connaissances, terminer une activité, arrêter un processus dans une activité et modifier les paramètres de configuration et de services de données de référence. L'administrateur DQS ne peut pas, toutefois, installer le serveur ni ajouter de nouveaux utilisateurs. L'administrateur de base de données doit effectuer ces opérations.  
  
-   L' **éditeur de base de connaissances DQS** (rôle dqs_kb_editor) peut effectuer toutes les activités DQS, sauf pour l'administration. L'éditeur de base de connaissances peut modifier et exécuter un projet, et créer et modifier une base de connaissances. Il peut voir les données d'analyse des activités, mais ne peut pas terminer ni arrêter une activité, ni remplir des fonctions d'administration.  
  
-   L' **opérateur de base de connaissances DQS** (rôle dqs_kb_operator) peut modifier et exécuter un projet. Il ne peut effectuer aucun type de gestion des connaissances ; il ne peut pas créer ni modifier une base de connaissances. Il peut voir les données d'analyse des activités, mais ne peut pas terminer une activité ni remplir des fonctions d'administration.  
  
## <a name="user-management"></a>User Management  
 L'administrateur de base de données (DBA) crée des utilisateurs DQS et les associe à des rôles DQS dans SQL Server Management Studio. Il gère leurs autorisations en ajoutant des connexions SQL en tant qu'utilisateurs de la base de données DQS_MAIN, puis en associant chaque utilisateur à un des rôles DQS. Chaque rôle reçoit des autorisations sur un ensemble de procédures stockées dans la base de données DQS_MAIN. Les trois rôles DQS ne sont pas disponibles pour les bases de données DQS_PROJECTS et DQS_STAGING_DATA.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Décrit comment créer un utilisateur et accorder des rôles DQS à l'aide de SQL Server Management Studio.|[Gérer des utilisateurs DQS dans SSMS](../../2014/data-quality-services/manage-dqs-users-in-ssms.md)|  
  
  
