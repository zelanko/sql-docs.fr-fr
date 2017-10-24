---
title: DBCC USEROPTIONS (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC USEROPTIONS
- DBCC_USEROPTIONS_TSQL
- USEROPTIONS_TSQL
- USEROPTIONS
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC USEROPTIONS statement
- active SET options
- SET statement, active SET options
ms.assetid: 565ab112-7af1-4c18-a579-07cdb332f539
caps.latest.revision: 41
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a94a29317bef21f784d2b0b927577627434ce7d9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-useroptions-transact-sql"></a>DBCC USEROPTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Renvoie les options SET qui sont actives (définies) pour la connexion courante.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DBCC USEROPTIONS  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Arguments  
NO_INFOMSGS  
Supprime tous les messages d'information dont les niveaux de gravité sont compris entre 0 et 10.
  
## <a name="result-sets"></a>Jeux de résultats  
DBCC USEROPTIONS renvoie une colonne pour le nom de l'option SET et une colonne pour la valeur de l'option (les valeurs et entrées peuvent varier) :

```sql

Set Option                   Value`  
---------------------------- ---------------------------`  
textsize                     64512 
language                     us_english 
dateformat                   mdy  
datefirst                    7 
lock_timeout                 -1 
quoted_identifier            SET 
arithabort                   SET 
ansi_null_dflt_on            SET 
ansi_warnings                SET 
ansi_padding                 SET 
ansi_nulls                   SET 
concat_null_yields_null      SET 
isolation level              read committed  
(13 row(s) affected) 
DBCC execution completed. If DBCC printed error messages, contact your system administrator.
 ```  
  
## <a name="remarks"></a>Notes  
DBCC USEROPTIONS signale un niveau d'isolation 'read committed snapshot' lorsque l'option de base de données READ_COMMITTED_SNAPSHOT a la valeur ON et que le niveau d'isolation des transactions a la valeur 'read committed'. Le niveau d'isolation réel est lecture validée.
  
## <a name="permissions"></a>Permissions  
Nécessite l'appartenance au rôle **public** .
  
## <a name="examples"></a>Exemples  
Cet exemple renvoie les options SET actives pour la connexion courante.
  
```sql  
DBCC USEROPTIONS;  
```  
  
## <a name="see-also"></a>Voir aussi  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
[SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)
  
  

