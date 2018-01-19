---
title: "Niveaux d’Isolation des transactions | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- locking [SQL Server], hints
- isolation levels [SQL Server], metadata access
- hints [SQL Server], locking
ms.assetid: 02bb71fa-1e92-4782-a9cf-6e256cc1f3ea
caps.latest.revision: "23"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 220cbbb856bc96aa4e44ea5a3d665fc9ce09da77
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="transaction-isolation-levels"></a>Niveaux d'isolement des transactions
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne garantit pas que les indicateurs de verrou sont respectés dans les requêtes ayant accès aux métadonnées à partir d'affichages catalogue, de vues de compatibilité, de vues de schémas d'informations et de fonctions intégrées générant des métadonnées.  
  
 En interne, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ne respecte que le niveau d'isolement READ COMMITTED pour l'accès aux métadonnées. Quand une transaction a un niveau d'isolement correspondant, par exemple, à SERIALIZABLE et qu'un accès aux métadonnées est tenté dans le cadre de cette transaction à partir de vues de catalogue ou de fonctions intégrées générant des métadonnées, les requêtes sont exécutées jusqu'à ce qu'elles soient achevées en tant que READ COMMITTED. Dans le cas d'un isolement d'instantané, l'accès aux métadonnées peut toutefois échouer à cause d'opérations DDL simultanées. Étant donné que les métadonnées sont dépourvues de version, l'accès aux éléments suivants peut échouer en cas d'isolement d'instantané :  
  
-   vues de catalogue ;  
  
-   vues de compatibilité ;  
  
-   Vues des schémas d'informations  
  
-   fonctions intégrées générant des métadonnées ;  
  
-   **sp_help** groupe de procédures stockées  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Procédures de catalogue natives Client  
  
-   vues et fonctions de gestion dynamique.  
  
 Pour plus d’informations sur les niveaux d’isolation, consultez [SET TRANSACTION ISOLATION LEVEL &#40; Transact-SQL &#41; ](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md).  
  
 Le tableau suivant comporte une synthèse d'accès aux métadonnées pour les différents niveaux d'isolement.  
  
|Niveau d'isolation|Pris en charge|Respect|  
|---------------------|---------------|-------------|  
|READ UNCOMMITTED|non|Non garanti|  
|READ COMMITTED|Oui|Oui|  
|REPEATABLE READ|non|non|  
|SNAPSHOT ISOLATION|non|non|  
|SERIALIZABLE|non|non|  
  
  
