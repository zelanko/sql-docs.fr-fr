---
title: SET PARSEONLY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PARSEONLY_TSQL
- SET_PARSEONLY_TSQL
- PARSEONLY
- SET PARSEONLY
dev_langs: TSQL
helpviewer_keywords:
- parsing [SQL Server], SET PARSEONLY statement
- checking syntax
- PARSEONLY option
- syntax [SQL Server], verifying
- verifying syntax
- SET PARSEONLY statement
ms.assetid: 514ab042-c53e-4d96-be71-fb08fcc6ef3c
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 107a70e458201f43d29b5a32885acce9a789acca
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="set-parseonly-transact-sql"></a>SET PARSEONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Examine la syntaxe de chaque instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] et renvoie tout message d'erreur éventuel sans compiler ni exécuter cette dernière.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET PARSEONLY { ON | OFF }  
```  
  
## <a name="remarks"></a>Notes  
 Si SET PARSEONLY est défini sur ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se contente d'analyser l'instruction. Si SET PARSEONLY est défini sur OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compile et exécute l'instruction.  
  
 L'option SET PARSEONLY est définie au moment de l'analyse, et non pas lors de l'exécution.  
  
 N'utilisez pas PARSEONLY dans une procédure stockée ou un déclencheur. SET PARSEONLY renvoie des décalages si l'option OFFSETS est activée (ON) et qu'aucune erreur ne se produit.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET OFFSETS &#40; Transact-SQL &#41;](../../t-sql/statements/set-offsets-transact-sql.md)  
  
  
