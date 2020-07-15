---
title: DROP INDEX (Selective XML Indexes) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP XML INDEX statement
dev_langs:
- TSQL
ms.assetid: 4779ae84-e5f4-4d04-8fc1-e24a6631b428
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6fb75992f2bcd229217c40582cd8087c6099d34f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85766317"
---
# <a name="drop-index-selective-xml-indexes"></a>DROP INDEX (Selective XML Indexes)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Supprime un index XML sélectif existant ou l'index XML secondaire sélectif dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Index XML sélectifs &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md).  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
DROP INDEX index_name ON <object>  
    [ WITH ( <drop_index_option> [ ,...n ] ) ]  
  
<object> ::=  
{ database_name.schema_name.table_or_view_name | schema_name.table_or_view_name | table_or_view_name }  
  
<drop_index_option> ::=  
{  
    MAXDOP = max_degree_of_parallelism  
    | ONLINE = { ON | OFF }  
}  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a> Arguments  
 *index_name*  
 Nom de l'index existant à supprimer.  
  
 *\< object>* est la table contenant la colonne XML indexée. Utilisez l'un des éléments suivants :  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
-   `table_name`  
  
 *\<drop_index_option>* Pour plus d’informations sur les options drop index, consultez [DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md).  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 L'exécution de DROP INDEX nécessite une autorisation ALTER sur la table ou la vue. L'autorisation est accordée par défaut au rôle serveur fixe sysadmin et aux rôles de base de données fixes db_ddladmin et db_owner.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre une instruction DROP INDEX.  
  
```  
DROP INDEX sxi_index ON tbl;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Index XML sélectifs &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [Créer, modifier ou supprimer des index XML sélectifs](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md)  
  
  

