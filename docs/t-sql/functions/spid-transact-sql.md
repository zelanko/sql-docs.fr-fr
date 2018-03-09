---
title: '@@SPID (Transact-SQL) | Documents Microsoft'
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@SPID'
- '@@SPID_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@SPID function'
- session_id
- server process IDs [SQL Server]
- IDs [SQL Server], user processes
- SPID
- session IDs [SQL Server]
- process ID of current user process
ms.assetid: df955d32-8194-438e-abee-387eebebcbb7
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f5d6ae023f4d736dc195034eeef0073845d7e2d5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40spid-transact-sql"></a>& #x 40 ; & #x 40 ; SPID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie l'ID de session du processus utilisateur actuel.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
@@SPID  
```  
  
## <a name="return-types"></a>Types de retour  
 **smallint**  
  
## <a name="remarks"></a>Notes  
 @@SPID peut être utilisé pour identifier le processus utilisateur en cours dans la sortie de **sp_who**.  
  
## <a name="examples"></a>Exemples  
 Cet exemple renvoie l'identificateur de session, le nom de connexion et le nom de l'utilisateur pour le processus utilisateur actuel.  
  
```  
SELECT @@SPID AS 'ID', SYSTEM_USER AS 'Login Name', USER AS 'User Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
ID     Login Name                     User Name                       
------ ------------------------------ ------------------------------  
54     SEATTLE\joanna                 dbo                             
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Cet exemple retourne le [!INCLUDE[ssDW](../../includes/ssdw-md.md)] ID de session, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contrôler l’ID de session de nœud, nom de connexion et nom d’utilisateur pour le processus utilisateur actuel.  
  
```  
SELECT SESSION_ID() AS ID, @@SPID AS 'Control ID', SYSTEM_USER AS 'Login Name', USER AS 'User Name';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de configuration](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [sp_lock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sp_who](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
  
  

