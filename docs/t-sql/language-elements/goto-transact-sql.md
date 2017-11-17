---
title: GOTO (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GOTO
- GOTO_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- skipping statements
- Transact-SQL statements, skipping
- labels [SQL Server]
- statements [SQL Server], skipping
- GOTO statement
ms.assetid: 589b6f8e-dc80-416f-9e74-48bed5337f58
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4c5614843f961d1ff3188ba1f3caa589d77c4735
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="goto-transact-sql"></a>GOTO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Modifie le flux d'exécution vers une étiquette. Les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] faisant suite à une instruction GOTO sont ignorées et le traitement reprend à l'étiquette. Les instructions GOTO et les étiquettes peuvent être utilisées à n'importe quel endroit d'une procédure, d'un traitement d'instructions ou d'un bloc d'instructions. Les instructions GOTO peuvent être imbriquées.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Define the label:   
label:   
Alter the execution:  
GOTO label   
```  
  
## <a name="arguments"></a>Arguments  
 *étiquette*  
 Point après lequel le traitement reprend si une instruction GOTO pointe sur cette étiquette. Les étiquettes doivent respecter les règles pour [identificateurs](../../relational-databases/databases/database-identifiers.md). Une étiquette peut servir à insérer des commentaires et ce, qu'il existe ou non une instruction GOTO.  
  
## <a name="remarks"></a>Notes  
 Une instruction GOTO peut exister au sein d'instructions conditionnelles de contrôle de flux, de blocs d'instructions ou de procédures mais ne peut pas pointer sur une étiquette située en dehors du traitement d'instructions. Le branchement GOTO peut pointer sur une étiquette dont la définition se trouve avant ou après l'instruction GOTO.  
  
## <a name="permissions"></a>Permissions  
 Par défaut, tout utilisateur reconnu a l'autorisation d'utiliser l'instruction GOTO.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de `GOTO` comme mécanisme de branche.  
  
```  
DECLARE @Counter int;  
SET @Counter = 1;  
WHILE @Counter < 10  
BEGIN   
    SELECT @Counter  
    SET @Counter = @Counter + 1  
    IF @Counter = 4 GOTO Branch_One --Jumps to the first branch.  
    IF @Counter = 5 GOTO Branch_Two  --This will never execute.  
END  
Branch_One:  
    SELECT 'Jumping To Branch One.'  
    GOTO Branch_Three; --This will prevent Branch_Two from executing.  
Branch_Two:  
    SELECT 'Jumping To Branch Two.'  
Branch_Three:  
    SELECT 'Jumping To Branch Three.';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Langage de contrôle de flux &#40; Transact-SQL &#41;](~/t-sql/language-elements/control-of-flow.md)   
 [BEGIN... FIN &#40; Transact-SQL &#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [SAUT de &#40; Transact-SQL &#41;](../../t-sql/language-elements/break-transact-sql.md)   
 [Continuer &#40; Transact-SQL &#41;](../../t-sql/language-elements/continue-transact-sql.md)   
 [IF... AUTRE &#40; Transact-SQL &#41;](../../t-sql/language-elements/if-else-transact-sql.md)   
 [WAITFOR &#40; Transact-SQL &#41;](../../t-sql/language-elements/waitfor-transact-sql.md)   
 [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  
  
  

