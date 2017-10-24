---
title: SET FMTONLY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FMTONLY_TSQL
- FMTONLY
- SET FMTONLY
- SET_FMTONLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server], only metadata returned
- SET FMTONLY statement
- FMTONLY option
ms.assetid: 02a1d9ac-2e58-433c-9a07-2c5a4a2214e1
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1cf925ce8ec9095acec90a34ed7d08f04826c2c1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-fmtonly-transact-sql"></a>SET FMTONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne uniquement des métadonnées au client. Peut être utilisé pour tester le format de la réponse sans avoir à exécuter la requête.  
  
> [!NOTE]  
>  N'utilisez pas cette fonctionnalité. Cette fonctionnalité a été remplacée par [sp_describe_first_result_set &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md), [sp_describe_undeclared_parameters &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md), [sys.dm_exec_describe_first_result_set &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md), et [sys.dm_exec_describe_first_result_set_for_object &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SET FMTONLY { ON | OFF }   
```  
  
## <a name="remarks"></a>Notes  
 Aucune ligne n'est traitée ou envoyée au client lorsque l'option SET FMTONLY est configurée avec la valeur ON dans la demande.  
  
 La définition de SET FMTONLY s'effectue au moment de l'exécution, et non durant l'analyse.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle public.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-view-the-column-header-information-for-a-query-without-actually-running-the-query"></a>R : permet d’afficher les informations d’en-tête de colonne pour une requête sans exécuter la requête.  
 L'exemple suivant affecte la valeur `SET FMTONLY` à `ON` et exécute une instruction `SELECT`. Suite à cette activation, l'instruction retourne uniquement des informations sur les colonnes ; elle ne retourne aucune ligne de données.  
  
```  
USE AdventureWorks2012;  
GO  
SET FMTONLY ON;  
GO  
SELECT *   
FROM HumanResources.Employee;  
GO  
SET FMTONLY OFF;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-view-the-column-header-information-for-a-query-without-actually-running-the-query"></a>B. Afficher les informations d’en-tête de colonne pour une requête sans exécuter la requête.  
 L’exemple suivant montre comment retourner uniquement les informations d’en-tête (métadonnées de) colonne pour une requête. Le traitement commence par FMTONLY désactivée (OFF) et modifie FMTONLY ON avant l’instruction SELECT. Cela entraîne l’instruction SELECT retourner uniquement les en-têtes de colonnes ; aucune ligne de données n’est retournées.  
  
```  
-- Uses AdventureWorks  
  
BEGIN  
    SET FMTONLY OFF;  
    SET DATEFORMAT mdy;  
    SET FMTONLY ON;  
    SELECT * FROM dbo.DimCustomer;  
    SET FMTONLY OFF;  
END  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  


