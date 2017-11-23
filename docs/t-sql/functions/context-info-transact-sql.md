---
title: CONTEXT_INFO (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONTEXT_INFO_TSQL
- CONTEXT_INFO
dev_langs: TSQL
helpviewer_keywords:
- CONTEXT_INFO function
- Multiple Active Result Sets
- context information [SQL Server]
- MARS [SQL Server]
- session context information [SQL Server]
ms.assetid: 571320f5-7228-4b0e-9d01-ab732d2d1eab
caps.latest.revision: "19"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a647bc7ced2188a45183200f08400f5507f7b328
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="contextinfo--transact-sql"></a>CONTEXT_INFO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne le **context_info** valeur qui a été défini pour la session en cours ou un lot à l’aide de la [SET CONTEXT_INFO](../../t-sql/statements/set-context-info-transact-sql.md) instruction.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CONTEXT_INFO()  
```  
  
## <a name="return-value"></a>Valeur retournée
La valeur de **context_info**.
  
Si **context_info** n’était pas définie :
-   Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renvoie la valeur NULL.  
-   Dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)] retourne un GUID unique spécifique à la session.  
  
## <a name="remarks"></a>Notes  
MARS (Multiple active result sets) permet aux applications d'exécuter simultanément plusieurs traitements ou requêtes sur la même connexion. Lorsqu'un traitement d'une connexion MARS exécute la procédure SET CONTEXT_INFO, la fonction CONTEXT_INFO renvoie la nouvelle valeur de contexte lorsqu'elle est exécutée dans le même traitement que l'instruction SET. La fonction CONTEXT_INFO ne renvoie pas la nouvelle valeur lorsqu'elle est exécutée dans un ou plusieurs autres traitements sur la connexion, sauf s'ils ont démarré une fois que le traitement ayant exécuté l'instruction SET était terminé.
  
## <a name="permissions"></a>Permissions  
Ne nécessite aucune autorisation particulière. Les informations de contexte sont également stockées dans le **sys.dm_exec_requests**, **sys.dm_exec_sessions**, et **sys.sysprocesses** vues système, mais interroger directement les vues requiert des autorisations SELECT et VIEW SERVER STATE.
  
## <a name="examples"></a>Exemples  
L’exemple simple suivant définit les **context_info** valeur `0x1256698456`, puis utilise le `CONTEXT_INFO` fonction pour récupérer la valeur.
  
```sql
SET CONTEXT_INFO 0x1256698456;  
GO  
SELECT CONTEXT_INFO();  
GO  
```  
  
## <a name="see-also"></a>Voir aussi
[SET CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/statements/set-context-info-transact-sql.md)
  
  
