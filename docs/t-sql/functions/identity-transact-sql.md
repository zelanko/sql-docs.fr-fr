---
title: '@@IDENTITY (Transact-SQL) | Documents Microsoft'
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@IDENTITY_TSQL'
- '@@IDENTITY'
dev_langs:
- TSQL
helpviewer_keywords:
- last-inserted identity values
- identity values [SQL Server], last-inserted
- '@@IDENTITY function'
ms.assetid: 912e4485-683c-41c2-97b3-8831c0289ee4
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 88cdaa1362e5d60b0f880c66c7fb7038ddb9f126
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="x40x40identity-transact-sql"></a>&#x40;&#x40; l’identité (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Fonction système qui retourne la dernière valeur d'identité insérée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
@@IDENTITY  
```  
  
## <a name="return-types"></a>Types de retour  
 **NUMERIC(38,0)**  
  
## <a name="remarks"></a>Notes  
 Instruction de la copie terminée après une insertion, SELECT INTO ou en bloc, @@IDENTITY contient la dernière valeur d’identité générée par l’instruction. Si l’instruction n’a affecté aucune table avec des colonnes d’identité, @@IDENTITY renvoie la valeur NULL. Si plusieurs lignes sont insérées, générant plusieurs valeurs d’identité, @@IDENTITY retourne la dernière valeur d’identité générée. Si l’instruction active un ou plusieurs déclencheurs qui effectuent des insertions qui génèrent des valeurs d’identité, l’appel@IDENTITY immédiatement après l’instruction renvoie la dernière valeur d’identité générée par les déclencheurs. Si un déclencheur est activé après une action d’insertion sur une table qui comporte une colonne d’identité, le déclencheur insère dans une autre table qui n’a pas une colonne d’identité, @@IDENTITY renvoie la valeur d’identité de la première insertion. Le @@IDENTITY ne revient pas à une valeur précédente si la copie de déclaration ou de bulk INSERT ou SELECT INTO échoue, ou si la transaction est restaurée.  
  
 Les instructions et les transactions en échec peuvent modifier l'identité actuelle d'une table et créer des trous dans les valeurs des colonnes d'identité. La valeur d'identité n'est jamais annulée, même si la transaction qui a essayé d'insérer la valeur dans la table n'est pas validée. Par exemple, si une instruction INSERT échoue à cause d'une violation d'identité IGNORE_DUP_KEY, la valeur d'identité actuelle de la table augmente quand même d'une unité.  
  
 @@IDENTITY, SCOPE_IDENTITY et IDENT_CURRENT sont des fonctions similaires car elles retournent toutes la dernière valeur insérée dans la colonne d’identité d’une table.  
  
 @@IDENTITY et SCOPE_IDENTITY retournent la dernière valeur d’identité générée dans une table dans la session active. Toutefois, SCOPE_IDENTITY renvoie la valeur uniquement dans la portée actuelle ; @@IDENTITY n’est pas limité à une étendue spécifique.  
  
 IDENT_CURRENT n'est pas limitée par l'étendue et par la session ; elle est limitée à une table spécifiée. IDENT_CURRENT retourne la valeur d'identité générée pour une table spécifique dans n'importe quelle session et dans n'importe quelle portée. Pour plus d’informations, consultez [IDENT_CURRENT &#40; Transact-SQL &#41; ](../../t-sql/functions/ident-current-transact-sql.md).  
  
 L’étendue de la @@IDENTITY fonction est une session en cours sur le serveur local sur lequel elle est exécutée. Cette fonction est inapplicable aux serveurs distants ou liés. Pour obtenir une valeur d'identité sur un autre serveur, exécutez une procédure stockée sur ce serveur distant ou lié puis faites en sorte que celle-ci, en cours d'exécution dans le contexte du serveur distant ou lié, collecte la valeur d'identité et la retourne à la connexion appelante sur le serveur local.  
  
 La réplication peut affecter le @@IDENTITY valeur, car il est utilisé dans les procédures stockées et les déclencheurs de réplication. @@IDENTITY n’est pas un indicateur fiable de l’identité créée par l’utilisateur la plus récente, si la colonne fait partie d’un article de réplication. Vous pouvez utiliser la syntaxe de la fonction SCOPE_IDENTITY() au lieu de @@IDENTITY. Pour plus d’informations, consultez [SCOPE_IDENTITY &#40; Transact-SQL &#41;](../../t-sql/functions/scope-identity-transact-sql.md)  
  
> [!NOTE]  
>  L’appel de procédure stockée ou [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction doit être réécrit pour utiliser le `SCOPE_IDENTITY()` (fonction), qui retourne l’identité la plus récente utilisée dans l’étendue de cette instruction utilisateur et non l’identité dans l’étendue du déclencheur imbriqué utilisé par réplication.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant insère une ligne dans une table dotée d'une colonne d'identité (`LocationID`) et utilise `@@IDENTITY` pour afficher la valeur d'identité utilisée dans la nouvelle ligne.  
  
```  
USE AdventureWorks2012;  
GO  
--Display the value of LocationID in the last row in the table.  
SELECT MAX(LocationID) FROM Production.Location;  
GO  
INSERT INTO Production.Location (Name, CostRate, Availability, ModifiedDate)  
VALUES ('Damaged Goods', 5, 2.5, GETDATE());  
GO  
SELECT @@IDENTITY AS 'Identity';  
GO  
--Display the value of LocationID of the newly inserted row.  
SELECT MAX(LocationID) FROM Production.Location;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions système &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [IDENT_CURRENT &#40;Transact-SQL&#41;](../../t-sql/functions/ident-current-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [SCOPE_IDENTITY &#40;Transact-SQL&#41;](../../t-sql/functions/scope-identity-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
  
  

