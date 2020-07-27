---
title: Afficher et enregistrer des plans d’exécution | Microsoft Docs
description: Découvrez comment afficher des plans d’exécution et les enregistrer dans un fichier au format XML en utilisant SQL Server Management Studio.
ms.custom: ''
ms.date: 08/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan results
- execution plans [SQL Server]
- queries [SQL Server], tuning
- execution plans [SQL Server], how-to topics
- SQL Server Management Studio [SQL Server], execution plans
- tuning queries [SQL Server]
ms.assetid: bcd6f094-c613-4835-ae19-4caaadb4bb17
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 19c0cee8d1ff56167032f7a0ff918b3adee24056
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86457291"
---
# <a name="display-and-save-execution-plans"></a>Afficher et enregistrer des plans d'exécution
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
Cette section explique comment afficher des plans d'exécution et les enregistrer dans un fichier au format XML en utilisant Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
Les plans d’exécution affichent graphiquement les méthodes de récupération des données choisies par l’Optimiseur de requête de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les plans d’exécution représentent le coût d’exécution de requêtes et d’instructions spécifiques dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par des icônes plutôt que par la représentation tabulaire résultant des instructions [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md) ou [SET SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md). Cette approche graphique se révèle utile pour la compréhension des caractéristiques de performances d'une requête.  

Bien que l’Optimiseur de requête de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne génère qu’un seul plan d’exécution, il existe le concept de plan d’exécution **estimé** et de plan d’exécution **réel**.
-  Un [plan d’exécution estimé](../../relational-databases/performance/display-the-estimated-execution-plan.md) retourne le plan d’exécution produit par l’Optimiseur de requête au moment de la compilation. Le fait de produire le plan d’exécution estimé n’exécute pas réellement la requête ou le lot, et par conséquent ne contient aucune information d’exécution, comme des avertissements d’exécution ou des métriques d’utilisation des ressources réelles. 
-  Un [plan d’exécution réel](../../relational-databases/performance/display-an-actual-execution-plan.md) retourne le plan d’exécution produit par l’Optimiseur de requête, et une fois que les requêtes ou les lots ont été exécutés. Cela inclut les informations d’exécution concernant les métriques d’utilisation des ressources et les avertissements d’exécution.  

Pour plus d’informations sur les plans d’exécution de requête, consultez le [Guide d’architecture de traitement des requêtes](../../relational-databases/query-processing-architecture-guide.md).
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Afficher le plan d’exécution estimé](../../relational-databases/performance/display-the-estimated-execution-plan.md)  
  
-   [Afficher un plan d'exécution réel](../../relational-databases/performance/display-an-actual-execution-plan.md)  
  
-   [Enregistrer un plan d’exécution au format XML](../../relational-databases/performance/save-an-execution-plan-in-xml-format.md)  
  
  
