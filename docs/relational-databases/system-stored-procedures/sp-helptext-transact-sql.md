---
title: sp_helptext (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helptext
- sp_helptext_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helptext
ms.assetid: 24135456-05f0-427c-884b-93cf38dd47a8
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 39bc13882e3293bca022f52240f18de696f3b7c1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826642"
---
# <a name="sp_helptext-transact-sql"></a>sp_helptext (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Affiche la définition d'une règle définie par l'utilisateur, d'une procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] par défaut et non chiffrée, d'une fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] définie par l'utilisateur, d'un déclencheur, d'une colonne calculée, d'une contrainte CHECK, d'une vue ou d'un objet système tel qu'une procédure stockée système.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helptext [ @objname = ] 'name' [ , [ @columnname = ] computed_column_name ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @objname = ] 'name'`Nom qualifié ou non qualifié d’un objet défini par l’utilisateur et ayant une portée de schéma. Les guillemets ne sont nécessaires que si un objet qualifié est spécifié. Si un nom qualifié complet (incluant un nom de base de données) est fourni, le nom de base de données doit être celui de la base de données active. Cet objet doit exister dans la base de données active. *Name* est de type **nvarchar (776)**, sans valeur par défaut.  
  
`[ @columnname = ] 'computed_column_name'`Nom de la colonne calculée pour laquelle afficher les informations de définition. La table qui contient la colonne doit être spécifiée en tant que *nom*. *column_name* est de **type sysname**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**Texte**|**nvarchar(255)**|Définition de l'objet|  
  
## <a name="remarks"></a>Remarques  
 sp_helptext affiche la définition utilisée pour créer un objet dans plusieurs lignes. Chaque ligne contient 255 caractères de la définition [!INCLUDE[tsql](../../includes/tsql-md.md)]. La définition se trouve dans la colonne de **définition** de l’affichage catalogue [sys. sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) .  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** . Les définitions de l'objet système sont visibles publiquement. La définition des objets utilisateur est visible par le propriétaire de l'objet ou les bénéficiaires de l'une des autorisations suivantes : ALTER, CONTROL, TAKE OWNERSHIP ou VIEW DEFINITION.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-displaying-the-definition-of-a-trigger"></a>R. Affichage de la définition d'un déclencheur  
 L’exemple suivant affiche la définition du déclencheur `dEmployee` dans la [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] base de données.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helptext 'HumanResources.dEmployee';  
GO  
```  
  
### <a name="b-displaying-the-definition-of-a-computed-column"></a>B. Affichage de la définition d'une colonne calculée  
 L'exemple suivant affiche la définition de la colonne calculée `TotalDue` dans la table `SalesOrderHeader` de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
sp_helptext @objname = N'AdventureWorks2012.Sales.SalesOrderHeader', @columnname = TotalDue ;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Text`  
  
 `---------------------------------------------------------------------`  
  
 `(isnull(([SubTotal]+[TaxAmt])+[Freight],(0)))`  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de base de données des procédures stockées &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
