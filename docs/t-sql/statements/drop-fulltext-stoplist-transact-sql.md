---
title: DROP FULLTEXT STOPLIST (Transact-SQL) | Documents Microsoft
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
- DROP_FULLTEXT_STOPLIST_TSQL
- DROP FULLTEXT STOPLIST
dev_langs: TSQL
helpviewer_keywords:
- DROP FULLTEXT STOPLIST statement
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 3ee2a2bb-1dfb-4e7c-90e9-9d917cd84a15
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bf761059b932045cffe635fb169684718e612402
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="drop-fulltext-stoplist-transact-sql"></a>DROP FULLTEXT STOPLIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Supprime une liste de mots vides de texte intégral dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
> [!IMPORTANT]  
>  CREATE FULLTEXT STOPLIST est pris en charge uniquement pour un niveau de compatibilité de 100 et supérieur. Pour des niveaux de compatibilité de 80 et 90, la liste de mots vides système est toujours assignée à la base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP FULLTEXT STOPLIST stoplist_name  
;  
```  
  
## <a name="arguments"></a>Arguments  
 *stoplist_name*  
 Nom de la liste de mots vides de texte intégral à supprimer de la base de données.  
  
## <a name="remarks"></a>Notes  
 DROP FULLTEXT STOPLIST échoue si des index de texte intégral quelconques font référence à la liste de mots vides de texte intégral en cours de suppression.  
  
## <a name="permissions"></a>Permissions  
 Pour supprimer une liste de mots vides requiert ayant l’autorisation DROP sur la liste de mots vides ou l’appartenance à la **db_owner** ou **db_ddladmin** base de données fixe.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous supprime une liste de mots vides de texte intégral nommée `myStoplist`.  
  
```  
DROP FULLTEXT STOPLIST myStoplist;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER FULLTEXT STOPLIST &#40; Transact-SQL &#41;](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)   
 [CRÉER une liste de mots vides de texte intégral &#40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [Sys.fulltext_stoplists &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)  
  
  
