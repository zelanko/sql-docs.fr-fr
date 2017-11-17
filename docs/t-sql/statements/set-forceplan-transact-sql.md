---
title: SET FORCEPLAN (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_FORCEPLAN_TSQL
- SET FORCEPLAN
- FORCEPLAN
- FORCEPLAN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- joins [SQL Server], overriding query optimizer process
- FORCEPLAN option
- SET FORCEPLAN statement
- query optimizer [SQL Server], optimizing process
- overriding query optimizer process
ms.assetid: b6c0b08f-2060-4696-9e12-50cb7e674321
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: df0bb88faa940a54f3b3eb14c34998b1982879c6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-forceplan-transact-sql"></a>SET FORCEPLAN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Lorsque FORCEPLAN a pour valeur ON, l'optimiseur de requête [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] traite une jointure dans le même ordre que celui où les tables apparaissent dans la clause FROM d'une requête. Qui plus est, la définition de FORCEPLAN à ON force l'utilisation d'une jointure de boucles imbriquées sauf si d'autres types de jointures sont nécessaires pour construire un plan pour la requête ou si elles sont demandées avec des indicateurs de requête ou de jointure.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET FORCEPLAN { ON | OFF }  
```  
  
## <a name="remarks"></a>Notes  
 SET FORCEPLAN a priorité sur la logique utilisée par l'optimiseur pour traiter une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT. Les données renvoyées par l'instruction SELECT sont identiques, que cette option soit ou non utilisée. La seule différence est la façon dont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] traite les tables durant l'exécution de la requête.  
  
 Les indicateurs de l'optimiseur de requête peuvent également être utilisés dans les requêtes pour modifier la façon dont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] traite l'instruction SELECT.  
  
 L'option SET FORCEPLAN est appliquée lors de l'exécution et non pas au moment de l'analyse.  
  
## <a name="permissions"></a>Permissions  
 Les autorisations SET FORCEPLAN sont octroyées par défaut à tous les utilisateurs.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant effectue une jointure de quatre tables. L'option `SHOWPLAN_TEXT` est activée afin que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renvoie des informations indiquant comment la requête est traitée différemment après l'activation de `SET FORCE_PLAN`.  
  
```  
USE AdventureWorks2012;  
GO  
-- Make sure FORCEPLAN is set to OFF.  
SET SHOWPLAN_TEXT OFF;  
GO  
SET FORCEPLAN OFF;  
GO  
SET SHOWPLAN_TEXT ON;  
GO  
-- Example where the query plan is not forced.  
SELECT p.LastName, p.FirstName, v.Name  
FROM Person.Person AS p  
   INNER JOIN HumanResources.Employee AS e  
   ON e.BusinessEntityID = p.BusinessEntityID  
   INNER JOIN Purchasing.PurchaseOrderHeader AS poh  
   ON e.BusinessEntityID = poh.EmployeeID  
   INNER JOIN Purchasing.Vendor AS v  
   ON poh.VendorID = v.BusinessEntityID;  
GO  
-- SET FORCEPLAN to ON.  
SET SHOWPLAN_TEXT OFF;  
GO  
SET FORCEPLAN ON;  
GO  
SET SHOWPLAN_TEXT ON;  
GO  
-- Reexecute inner join to see the effect of SET FORCEPLAN ON.  
SELECT p.LastName, p.FirstName, v.Name  
FROM Person.Person AS p  
   INNER JOIN HumanResources.Employee AS e   
   ON e.BusinessEntityID = p.BusinessEntityID  
   INNER JOIN Purchasing.PurchaseOrderHeader AS poh  
   ON e.BusinessEntityID = poh.EmployeeID  
   INNER JOIN Purchasing.Vendor AS v  
   ON poh.VendorID = v.BusinessEntityID;  
GO  
SET SHOWPLAN_TEXT OFF;  
GO  
SET FORCEPLAN OFF;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET SHOWPLAN_ALL &#40; Transact-SQL &#41;](../../t-sql/statements/set-showplan-all-transact-sql.md)   
 [SET SHOWPLAN_TEXT &#40; Transact-SQL &#41;](../../t-sql/statements/set-showplan-text-transact-sql.md)  
  
  

