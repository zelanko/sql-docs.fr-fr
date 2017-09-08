---
title: "DÉFINITION de la langue (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 06/05/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_LANGUAGE_TSQL
- SET LANGUAGE
dev_langs:
- TSQL
helpviewer_keywords:
- LANGUAGE option
- languages [SQL Server], setting language
- SET LANGUAGE statement
- options [SQL Server], date
- default languages
ms.assetid: 0ec0e5cf-e115-4be9-a0db-e65837d6fa45
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f334049b696685b366c36484857d1340853a4b15
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-language-transact-sql"></a>SET LANGUAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Spécifie la langue de l'environnement pour la session. La langue de session détermine la **datetime** formats et les messages système.  
  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET LANGUAGE { [ N ] 'language' | @language_var }   
```  
  
## <a name="arguments"></a>Arguments  
 [**N**]**'***langage***'** | **@***var_langue*  
 Est le nom de la langue, tel que stocké dans [sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md). Cet argument peut être au format Unicode ou DBCS converti en Unicode. Pour spécifier une langue au format Unicode, utilisez **N'***langage***'**. S’il est spécifié en tant que variable, la variable doit être **sysname**.  
  
## <a name="remarks"></a>Notes  
 La définition de SET LANGUAGE s'effectue lors de l'exécution, et non durant l'analyse.  
  
 SET LANGUAGE définit implicitement le paramètre de [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant affecte la valeur `Italian` à la langue par défaut, affiche le nom du mois, puis resélectionne la valeur `us_english` et affiche à nouveau le nom du mois.  
  
```  
DECLARE @Today DATETIME;  
SET @Today = '12/5/2007';  
  
SET LANGUAGE Italian;  
SELECT DATENAME(month, @Today) AS 'Month Name';  
  
SET LANGUAGE us_english;  
SELECT DATENAME(month, @Today) AS 'Month Name' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)   
 [sp_helplanguage &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)   
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
