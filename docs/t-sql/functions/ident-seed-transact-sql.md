---
title: IDENT_SEED (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IDENT_SEED_TSQL
- IDENT_SEED
dev_langs:
- TSQL
helpviewer_keywords:
- identity columns [SQL Server], IDENT_SEED function
- seed values [SQL Server]
- IDENT_SEED function
ms.assetid: e4cb8eb8-affb-4810-a8a9-0110af3c247a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ef3bfdbb21839bd7f4f60ba1a731e39ec1f42c1f
ms.sourcegitcommit: bbdf51f0d56acfa6bcc4a5c4fe2c9f3cd4225edc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56079305"
---
# <a name="identseed-transact-sql"></a>IDENT_SEED (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne la valeur de départ d’origine (sous la forme **numeric**(**@@** MAXPRECISION,0)) spécifiée lors de la création d’une colonne d’identité dans une table ou une vue. La modification de la valeur actuelle d’une colonne d’identité en utilisant DBCC CHECKIDENT ne modifie pas la valeur retournée par cette fonction.  
  
 ![Icône Lien de l’article](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de l’article") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IDENT_SEED ( 'table_or_view' )  
```  
  
## <a name="arguments"></a>Arguments  
 **'** *table_or_view* **'**  
 [Expression](../../t-sql/language-elements/expressions-transact-sql.md) qui spécifie la table ou la vue dans laquelle rechercher une valeur de départ d’identité. *table_or_view* peut être une constante de type chaîne de caractères entre guillemets, une variable, une fonction ou un nom de colonne. *table_or_view* est de type **char**, **nchar**, **varchar** ou **nvarchar**.  
  
## <a name="return-types"></a>Types de retour  
 **numeric**  
  
## <a name="exceptions"></a>Exceptions  
 Retourne NULL en cas d’erreur ou si un appelant n’est pas autorisé à voir l’objet.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un utilisateur peut seulement voir les métadonnées des éléments sécurisables qui lui appartiennent ou pour lesquels il dispose d’une autorisation. Cette sécurité signifie que les fonctions intégrées générant des métadonnées comme IDENT_SEED peuvent retourner la valeur NULL si l’utilisateur ne dispose d’aucune autorisation sur l’objet. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-the-seed-value-from-a-specified-table"></a>A. Renvoi de la valeur de départ d'une table spécifiée  
 L'exemple suivant renvoie la valeur initiale pour la table `Person.Address` de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
SELECT IDENT_SEED('Person.Address') AS Identity_Seed;  
GO  
```  
  
### <a name="b-returning-the-seed-value-from-multiple-tables"></a>b. Renvoi de la valeur initiale de plusieurs tables  
 L’exemple suivant retourne les tables de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] qui contiennent une colonne d’identité avec une valeur de départ.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT TABLE_SCHEMA, TABLE_NAME,   
   IDENT_SEED(TABLE_SCHEMA + '.' + TABLE_NAME) AS IDENT_SEED  
FROM INFORMATION_SCHEMA.TABLES  
WHERE IDENT_SEED(TABLE_SCHEMA + '.' + TABLE_NAME) IS NOT NULL;  
GO  
```  
  
 Voici un jeu de résultats partiel.  
  
 ```
 TABLE_SCHEMA       TABLE_NAME                   IDENT_SEED  
------------       ---------------------------  -----------  
Person             Address                                1  
Production         ProductReview                          1  
Production         TransactionHistory                100000  
Person             AddressType                            1  
Production         ProductSubcategory                     1  
Person             vAdditionalContactInfo                 1  
dbo                AWBuildVersion                         1
```  
  
## <a name="see-also"></a> Voir aussi  
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Fonctions système &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [IDENT_CURRENT &#40;Transact-SQL&#41;](../../t-sql/functions/ident-current-transact-sql.md)   
 [IDENT_INCR &#40;Transact-SQL&#41;](../../t-sql/functions/ident-incr-transact-sql.md)   
 [DBCC CHECKIDENT &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)   
 [sys.identity_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-identity-columns-transact-sql.md)  
  
