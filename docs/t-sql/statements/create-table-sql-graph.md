---
title: "CRÉER la TABLE (SQL graphique) | Documents Microsoft"
ms.custom: 
ms.date: 05/04/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SQL_GRAPH_TSQL
- TABLE
- CREATE_TABLE_TSQL
- NODE
- NODE_TSQL
- AS_NODE
- AS_NODE_TSQL
- EDGE
- EDGE_TSQL
- AS_EDGE
- AS_EDGE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- graph
- SQL graph
- CREATE TABLE SQL graph
- NODE
- EDGE
- SQL graph, CREATE TABLE statement
ms.assetid: 
caps.latest.revision: 1
author: shkale-msft
ms.author: shkale
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c32a8c4f683f20c4384089c1d2552614090f9b3d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---

# <a name="create-table-sql-graph"></a>CRÉER la TABLE (graphique SQL)
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]   

Crée une table en tant que graphique SQL un `NODE` ou un `EDGE` table. 
  
> [!NOTE]   
>  Pour des instructions Transact-SQL standard, consultez [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CREATE TABLE   
    [ database_name . [ schema_name ] . | schema_name . ] table_name   
    ( { <column_definition> } [ ,...n ] )   
    AS [ NODE | EDGE ]
[ ; ]  
```  
  
  
## <a name="arguments"></a>Arguments  
Ce document répertorie uniquement les arguments se rapportant à un graphique SQL. Pour une liste complète et une description des arguments pris en charge, consultez [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)

 *nom_base_de_données*    
 Nom de la base de données dans laquelle la table est créée. *database_name* doit spécifier le nom de la base de données existante. Si non spécifié, *nom_base_de_données* par défaut, la base de données actuelle. La connexion pour la connexion actuelle doit être associée à un ID utilisateur existant dans la base de données spécifiée par *nom_base_de_données*, et cet ID utilisateur doit disposer des autorisations CREATE TABLE.  
  
 *schema_name*    
 Nom du schéma auquel appartient la nouvelle table.  
  
 *nom_table*    
 Est le nom du tableau de bord ou de nœud. Les noms de tables doivent respecter les règles pour [identificateurs](../../relational-databases/databases/database-identifiers.md). *nom_table* peut être un maximum de 128 caractères, à l’exception des noms de tables temporaires locales (noms précédés du signe dièse (#)) qui ne peut pas dépasser 116 caractères.  
  
 NŒUD   
 Crée une table de nœud.

 BORD  
 Crée un tableau de bord.  
  
## <a name="remarks"></a>Notes  
Création d’une table temporaire en tant que nœud ou un tableau de bord n’est pas pris en charge.  

Création d’un tableau de bord ou le nœud en tant qu’une table temporelle n’est pas pris en charge.

Base de données Stretch n’est pas prise en charge pour le tableau de bord ou de nœud.

Les tableaux de bord ou le nœud ne peut pas être des tables externes (aucune polybase prise en charge pour les tables de graphique). 
  
 
## <a name="examples"></a>Exemples  
  
### <a name="a-create-a-node-table"></a>A. Créer une `NODE` table
 L’exemple suivant montre comment créer un `NODE` table

```
 CREATE TABLE Person (
        ID INTEGER PRIMARY KEY, 
        name VARCHAR(100), 
        email VARCHAR(100)
 ) AS NODE;
```

### <a name="b-create-an-edge-table"></a>B. Créer une `EDGE` table
Les exemples suivants montrent comment créer `EDGE` tables

```
 CREATE TABLE friends (
    id integer PRIMARY KEY,
    start_date date
 ) AS EDGE;

```

```
 -- Create a likes edge table, this table does not have any user defined attributes   
 CREATE TABLE likes AS EDGE;

```


## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [INSERT (graphique SQL)](../../t-sql/statements/insert-sql-graph.md)]  
 [Graphique de traitement avec SQL Server 2017](../../relational-databases/graphs/sql-graph-overview.md)


