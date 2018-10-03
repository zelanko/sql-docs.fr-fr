---
title: DROP FULLTEXT STOPLIST (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_FULLTEXT_STOPLIST_TSQL
- DROP FULLTEXT STOPLIST
dev_langs:
- TSQL
helpviewer_keywords:
- DROP FULLTEXT STOPLIST statement
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 3ee2a2bb-1dfb-4e7c-90e9-9d917cd84a15
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 9ed184138e4bec2f973cfe6df8ea758b90b4a6af
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711817"
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
 Pour supprimer une liste de mots vides, vous devez avoir l’autorisation DROP sur la liste de mots vides ou être membre du rôle de base de données fixe **db_owner** ou **db_ddladmin**.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous supprime une liste de mots vides de texte intégral nommée `myStoplist`.  
  
```  
DROP FULLTEXT STOPLIST myStoplist;  
```  
  
## <a name="see-also"></a> Voir aussi  
 [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)  
  
  
