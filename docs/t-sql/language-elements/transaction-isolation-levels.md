---
title: Niveaux d’isolement | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], hints
- isolation levels [SQL Server], metadata access
- hints [SQL Server], locking
ms.assetid: 02bb71fa-1e92-4782-a9cf-6e256cc1f3ea
author: rothja
ms.author: jroth
ms.openlocfilehash: 28a8de0654fe6e083b52e83d85653a0d9856d351
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68072203"
---
# <a name="transaction-isolation-levels"></a>Niveaux d'isolement des transactions
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne garantit pas que les indicateurs de verrou sont respectés dans les requêtes ayant accès aux métadonnées à partir d'affichages catalogue, de vues de compatibilité, de vues de schémas d'informations et de fonctions intégrées générant des métadonnées.  
  
 En interne, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ne respecte que le niveau d'isolement READ COMMITTED pour l'accès aux métadonnées. Quand une transaction a un niveau d'isolement correspondant, par exemple, à SERIALIZABLE et qu'un accès aux métadonnées est tenté dans le cadre de cette transaction à partir de vues de catalogue ou de fonctions intégrées générant des métadonnées, les requêtes sont exécutées jusqu'à ce qu'elles soient achevées en tant que READ COMMITTED. Dans le cas d'un isolement d'instantané, l'accès aux métadonnées peut toutefois échouer à cause d'opérations DDL simultanées. Étant donné que les métadonnées sont dépourvues de version, l'accès aux éléments suivants peut échouer en cas d'isolement d'instantané :  
  
-   Affichages catalogue  
  
-   vues de compatibilité ;  
  
-   Vues des schémas d'informations  
  
-   fonctions intégrées générant des métadonnées ;  
  
-   Groupe **sp_help** de procédures stockées  
  
-   Procédures de catalogue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  
  
-   vues et fonctions de gestion dynamique.  
  
 Pour plus d’informations sur les niveaux d’isolement, consultez [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md).  
  
 Le tableau suivant comporte une synthèse d'accès aux métadonnées pour les différents niveaux d'isolement.  
  
|Niveau d'isolation|Prise en charge|Respect|  
|---------------------|---------------|-------------|  
|READ UNCOMMITTED|Non|Non garanti|  
|READ COMMITTED|Oui|Oui|  
|REPEATABLE READ|Non|Non|  
|SNAPSHOT ISOLATION|Non|Non|  
|SERIALIZABLE|Non|Non|  
  
  
