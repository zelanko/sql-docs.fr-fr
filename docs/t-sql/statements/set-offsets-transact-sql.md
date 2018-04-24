---
title: SET OFFSETS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SET_OFFSETS_TSQL
- OFFSETS_TSQL
- SET OFFSETS
- OFFSETS
dev_langs:
- TSQL
helpviewer_keywords:
- position relative to start of statement [SQL Server]
- OFFSETS option
- offsets [SQL Server]
- SET OFFSETS statement
ms.assetid: c7bcc697-0930-4630-acae-d8ccbfa4414c
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ffbfd6bcc9a94fc44e8353c7483f8d77486c9301
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="set-offsets-transact-sql"></a>SET OFFSETS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Renvoie le décalage (position par rapport au début d'une instruction) de mots clés spécifiés dans des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] destinées aux applications DB-Library.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
 
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET OFFSETS keyword_list { ON | OFF }  
```  
  
## <a name="arguments"></a>Arguments  
 *keyword_list*  
 Liste de constructions [!INCLUDE[tsql](../../includes/tsql-md.md)] séparées par des virgules, notamment SELECT, FROM, ORDER, TABLE, PROCEDURE, STATEMENT, PARAM et EXECUTE.  
  
## <a name="remarks"></a>Notes   
 L'option SET OFFSETS est utilisée uniquement dans une application DB-Library (bibliothèque de bases de données).  
  
 Elle est définie au moment de l'analyse, et non pas lors de l'exécution. Par conséquent, si l'instruction SET est présente dans la procédure stockée ou le traitement, elle devient effective, que l'exécution du code ait réellement atteint ou non ce point ; l'instruction SET devient effective avant l'exécution de toute autre instruction. Par exemple, même si l'instruction SET se trouve dans un bloc d'instructions IF...ELSE qui n'est jamais atteint lors de l'exécution, elle prend quand même effet parce que le bloc d'instructions IF...ELSE est analysé.  
  
 Si l'option SET OFFSETS est définie dans une procédure stockée, sa valeur est rétablie une fois que le contrôle est renvoyé par la procédure stockée. Par conséquent, une instruction dynamique SQL SET OFFSETS n'a aucun effet sur les instructions exécutées après celle-ci.  
  
 SET PARSEONLY renvoie des décalages si l'option OFFSETS est activée (ON) et qu'aucune erreur ne se produit.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="see-also"></a> Voir aussi  
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET PARSEONLY &#40;Transact-SQL&#41;](../../t-sql/statements/set-parseonly-transact-sql.md)  
  
  
