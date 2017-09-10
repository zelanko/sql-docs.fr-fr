---
title: '@@TOTAL_ERRORS (Transact-SQL) | Documents Microsoft'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@TOTAL_ERRORS'
- '@@TOTAL_ERRORS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@TOTAL_ERRORS function'
- total errors [SQL Server]
- errors [SQL Server], read/write
- number of disk read/write errors
- disks [SQL Server], errors
- write errors [SQL Server]
- read/write errors
ms.assetid: 09e62428-ee0e-4ef5-b969-da9d255f1199
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 83d639209d35d6516bd9348f40f4eddfd30ddff5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="totalerrors-transact-sql"></a>@@TOTAL_ERRORS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le nombre d’erreurs d’écriture sur disque rencontrées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] depuis [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dernier démarrage.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
@@TOTAL_ERRORS  
```  
  
## <a name="return-types"></a>Types de retour  
 **entier**  
  
## <a name="remarks"></a>Notes  
 Cette fonction ne comptabilise pas toutes les erreurs d'écriture rencontrées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les erreurs d'écriture récupérables et occasionnelles sont gérées par le serveur lui-même et ne sont pas considérées comme des erreurs. Pour afficher un rapport contenant plusieurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des statistiques, notamment le nombre total d’erreurs, exécutez **sp_monitor**.  
  
## <a name="examples"></a>Exemples  
 Cet exemple affiche le nombre d'erreurs rencontrées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à la date et à l'heure du jour.  
  
```  
SELECT @@TOTAL_ERRORS AS 'Errors', GETDATE() AS 'As of';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Errors      As of                   
----------- ----------------------  
0           3/28/2003 12:32:11 PM   
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_monitor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Fonctions statistiques système &#40; Transact-SQL &#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
