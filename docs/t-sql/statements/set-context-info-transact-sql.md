---
title: SET CONTEXT_INFO (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_CONTEXT_INFO_TSQL
- SET CONTEXT_INFO
dev_langs:
- TSQL
helpviewer_keywords:
- context information [SQL Server]
- CONTEXT_INFO option
- SET CONTEXT_INFO statement
ms.assetid: a0b7b9f3-dbda-4350-a274-bd9ecd5c0a74
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f74a45830a295467552c8fdc9f4781260339d9a6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-contextinfo-transact-sql"></a>SET CONTEXT_INFO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Associe jusqu'à 128 octets d'informations binaires à la session ou à la connexion actuelle.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET CONTEXT_INFO { binary_str | @binary_var }  
```  
  
## <a name="arguments"></a>Arguments  
 *binary_str*  
 Est un **binaire** constante ou une constante qui est implicitement convertible en **binaire**à associer à la session en cours ou la connexion.  
  
 **@***binary_var*  
 Est un **varbinary** ou **binaire** variable contenant une valeur de contexte à associer à la session en cours ou la connexion.  
  
## <a name="remarks"></a>Notes  
 La méthode privilégiée pour récupérer les informations de contexte pour la session actuelle consiste à utiliser la fonction CONTEXT_INFO. Les informations de contexte de session sont également stockées dans le **context_info** colonnes dans les vues système suivantes :  
  
-   **Sys.dm_exec_requests**  
  
-   **Sys.dm_exec_sessions**  
  
-   **Sys.sysprocesses**  
  
 SET CONTEXT_INFO ne peut pas être spécifié dans une fonction définie par l'utilisateur. Vous ne pouvez pas fournir une valeur NULL dans SET CONTEXT_INFO, car les vues contenant les valeurs n'autorisent pas ce type de valeurs.  
  
 SET CONTEXT_INFO n'accepte pas les expressions autres que les constantes ou les noms de variables. Pour définir les informations de contexte pour le résultat d’un appel de fonction, vous devez d’abord inclure le résultat de l’appel de fonction dans une **binaire** ou **varbinary** variable.  
  
 Lorsque vous spécifiez SET CONTEXT_INFO dans une procédure stockée ou un déclencheur, contrairement aux autres instructions SET, la nouvelle valeur définie pour les informations de contexte est conservée à l'issue de l'exécution de la procédure stockée ou du déclencheur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-setting-context-information-by-using-a-constant"></a>A. Définition des informations de contexte à l'aide d'une constante  
 L'exemple ci-dessous illustre `SET CONTEXT_INFO` par la définition de la valeur et l'affichage des résultats. Notez que l'interrogation de `sys.dm_exec_sessions` nécessite les autorisations SELECT et VIEW SERVER STATE, ce qui n'est pas le cas pour la fonction CONTEXT_INFO.  
  
```  
SET CONTEXT_INFO 0x01010101;  
GO  
SELECT context_info   
FROM sys.dm_exec_sessions  
WHERE session_id = @@SPID;  
GO  
```  
  
### <a name="b-setting-context-information-by-using-a-function"></a>B. Définition des informations de contexte à l'aide d'une fonction  
 L’exemple suivant illustre l’utilisation de la sortie d’une fonction pour définir la valeur de contexte, où la valeur de la fonction doit tout d’abord être placée dans un **binaire** variable.  
  
```  
DECLARE @BinVar varbinary(128);  
SET @BinVar = CAST(REPLICATE( 0x20, 128 ) AS varbinary(128) );  
SET CONTEXT_INFO @BinVar;  
  
SELECT CONTEXT_INFO() AS MyContextInfo;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [Sys.dm_exec_requests &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [Sys.dm_exec_sessions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/functions/context-info-transact-sql.md)  
  
  

