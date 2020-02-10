---
title: Bases de données système | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system databases [SQL Server]
- displaying system database data
- modifying system data
- viewing system database data
ms.assetid: 30468a7c-4225-4d35-aa4a-ffa7da4f1282
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 916fd6d996a1a5270173d290c61f262ddf3f797b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62871126"
---
# <a name="system-databases"></a>Bases de données système
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclut les bases de données système suivantes.  
  
|Base de données système|Description|  
|---------------------|-----------------|  
|[Base de données master](master-database.md)|Enregistre toutes les informations système relatives à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Base de données msdb](msdb-database.md)|Utilisée par l'Agent SQL Server pour planifier les alertes et les travaux.|  
|[Base de données model](model-database.md)|Fait office de modèle pour toutes les bases de données créées sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les modifications apportées à la base de données **model** , telles que la taille de la base de données, le classement, le mode de récupération et les autres options de base de données, s'appliquent aux bases de données créées par la suite.|  
|[Base de données Resource](resource-database.md)|Base de données en lecture seule contenant des objets système fournis avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les objets système sont conservés physiquement dans la base de données **Resource** , mais ils figurent logiquement dans le schéma **sys** de chaque base de données.|  
|[Base de données tempdb](tempdb-database.md)|Espace de travail destiné à accueillir les objets temporaires ou les ensembles de résultats intermédiaires.|  
  
## <a name="modifying-system-data"></a>modification de données système  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne permet pas aux utilisateurs de mettre directement à jour les informations contenues dans les objets système, tels que les tables système, les procédures stockées système et les vues de catalogue. En revanche, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] propose un jeu complet d'outils d'administration qui permettent aux utilisateurs d'administrer complètement leur système et de gérer tous les utilisateurs et objets d'une base de données. Ces options en question sont les suivantes :  
  
-   Utilitaires d'administration, tels que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   API SQL-SMO. Cet outil permet aux programmeurs d'inclure des fonctionnalités complètes visant à administrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans leurs applications.  
  
-   
  [!INCLUDE[tsql](../../includes/tsql-md.md)] . Ceux-ci peuvent utiliser des procédures stockées système et des instructions DDL [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 Ces outils prémunissent les applications contre les modifications des objets système. Par exemple, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est parfois amené à modifier les tables système dans les nouvelles versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de prendre en charge les nouvelles fonctionnalités ajoutées à cette version. Les applications qui lancent des instructions SELECT référençant directement les tables système dépendent souvent de l'ancien format des tables système. Il est possible que les sites ne soient pas en mesure de procéder à la mise à niveau vers une nouvelle version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tant qu'ils n'ont pas réécrit les applications de sélection dans les tables système. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] considère les procédures stockées système, DDL et SQL-SMO comme des interfaces publiées, et veille à en maintenir la compatibilité descendante.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge les déclencheurs définis sur les tables système, car ils peuvent perturber le bon fonctionnement du système.  
  
> [!NOTE]  
>  Les bases de données système ne peuvent pas résider dans les répertoires partagés UNC.  
  
## <a name="viewing-system-database-data"></a>affichage de données de bases de données système  
 Vous ne devez pas coder les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qui interrogent directement les tables système, sauf s'il s'agit de la seule méthode d'obtention des informations requises par l'application. Au lieu de cela, les applications doivent obtenir les informations de catalogue et du système par l'un des moyens suivants :  
  
-   Vues de catalogue système  
  
-   SQL-SMO  
  
-   Interface WMI (Windows Management Instrumentation)  
  
-   Fonctions de catalogue, méthodes, attributs ou propriétés de l'API de données utilisée dans l'application, notamment ADO, OLE DB ou ODBC.  
  
-   
  [!INCLUDE[tsql](../../includes/tsql-md.md)] Procédures stockées système et fonctions intégrées.  
  
## <a name="related-tasks"></a>Tâches associées  
 [Sauvegarde et restauration des bases de données système &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [Masquer les objets système dans l’Explorateur d’objets](../../ssms/object/object-explorer.md)  
  
## <a name="related-content"></a>Contenu associé  
 [Affichages catalogue &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)  
  
 [Bases de données](databases.md)  
  
  
