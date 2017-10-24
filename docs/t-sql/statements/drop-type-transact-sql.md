---
title: "TYPE de déplacement (Transact-SQL) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP TYPE
- DROP_TYPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [SQL Server], deleting
- UDTs [SQL Server], deleting
- alias data types [SQL Server], removing
- DROP TYPE statement
ms.assetid: 11bf83f9-0718-4238-a835-83d2eb14ae7b
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4187c6bff08e5502f5edc6acd8d82334684a68d4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="drop-type-transact-sql"></a>DROP TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Supprime de la base de données active un type de données alias ou un type de données CLR (Common Language Runtime) défini par l'utilisateur.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DROP TYPE [ IF EXISTS ] [ schema_name. ] type_name [ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *S’IL EXISTE*  
 **S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Conditionnellement supprime le type uniquement s’il existe déjà.  
  
 *schema_name*  
 Nom du schéma auquel appartient le type de données alias ou défini par l'utilisateur  
  
 *TYPE_NAME*  
 Nom du type de données alias ou défini par l'utilisateur à supprimer  
  
## <a name="remarks"></a>Notes  
 L'instruction DROP TYPE ne s'exécutera pas si l'une des informations suivantes est vraie :  
  
-   Des tables de la base de données contiennent des colonnes du type de données alias ou du type défini par l'utilisateur. Pour plus d’informations sur les alias ou des colonnes de type défini par l’utilisateur peuvent être obtenus en interrogeant le [sys.columns](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) ou [sys.column_type_usages](../../relational-databases/system-catalog-views/sys-column-type-usages-transact-sql.md) affichages catalogue.  
  
-   Il existe des colonnes calculées, des contraintes CHECK, des vues liées au schéma et des fonctions liées au schéma dont les définitions font référence au type alias ou au type défini par l'utilisateur. Plus d’informations sur ces références peuvent être obtenues en interrogeant le [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) affichage catalogue.  
  
-   Il existe des fonctions, des procédures stockées ou des déclencheurs créés dans la base de données, et ces routines utilisent des variables et des paramètres de type alias ou de type défini par l'utilisateur. Pour plus d’informations sur les alias ou les paramètres de type défini par l’utilisateur peuvent être obtenus en interrogeant le [sys.parameters](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md) ou [sys.parameter_type_usages](../../relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql.md) affichages catalogue.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’autorisation CONTROL sur *type_name* ou l’autorisation ALTER sur *nom_schéma*.  
  
## <a name="examples"></a>Exemples  
 Cet exemple suppose qu'un type nommé `ssn` est déjà créé dans la base de données actuelle.  
  
```  
DROP TYPE ssn ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

