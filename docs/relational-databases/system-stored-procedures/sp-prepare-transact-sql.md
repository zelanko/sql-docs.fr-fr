---
title: sp_prepare (Transact SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepare_TSQL
- sp_cursor_prepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepare
ms.assetid: f328c9eb-8211-4863-bafa-347e1bf7bb3f
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9b52f71577bed8a0433c8d516cdc9cbd877066e4
ms.sourcegitcommit: f46fd79fd32a894c8174a5cb246d9d34db75e5df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/26/2018
ms.locfileid: "53785930"
---
# <a name="spprepare-transact-sql"></a>sp_prepare (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

Prépare une paramétrable [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction et retourne une instruction *gérer* pour l’exécution.  `sp_prepare` est appelé en spécifiant ID = 11 dans un paquet data stream (TDS).  
  
 ![Icône Lien de l’article](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_prepare handle OUTPUT, params, stmt, options  
```  
  
## <a name="arguments"></a>Arguments  
 *handle*  
 Généré par SQL Server *handle préparé* identificateur. *gérer* est un paramètre obligatoire avec une **int** valeur de retour.  
  
 *params*  
 Identifie des instructions paramétrables. Le *params* définition de variables est substituée aux marqueurs de paramètre dans l’instruction. *params* est un paramètre obligatoire qui demande un **ntext**, **nchar**, ou **nvarchar** valeur d’entrée. Entrez une valeur NULL si l'instruction n'est pas paramétrable.  
  
 *stmt*  
 Définit le jeu de résultats de curseur. Le *stmt* paramètre est obligatoire et demande pour un **ntext**, **nchar**, ou **nvarchar** valeur d’entrée.  
  
 *options*  
 Paramètre optionnel qui retourne une description des colonnes du jeu de résultats du curseur. *options* requiert la valeur d’entrée int suivante :  
  
|Value|Description|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
## <a name="examples"></a>Exemples  
A. L'exemple suivant prépare et exécute une instruction simple.  
  
```sql  
DECLARE @P1 int;  
EXEC sp_prepare @P1 output,   
    N'@P1 nvarchar(128), @P2 nvarchar(100)',  
    N'SELECT database_id, name FROM sys.databases WHERE name=@P1 AND state_desc = @P2';  
EXEC sp_execute @P1, N'tempdb', N'ONLINE';  
EXEC sp_unprepare @P1;  
```

b. L’exemple suivant prépare une instruction dans la base de données AdventureWorks2016 et exécute ensuite à l’aide de la poignée.

```sql
-- Prepare query
DECLARE @P1 int;  
EXEC sp_prepare @P1 output,   
    N'@Param int',  
    N'SELECT *
FROM Sales.SalesOrderDetail AS sod
INNER JOIN Production.Product AS p ON sod.ProductID = p.ProductID
WHERE SalesOrderID = @Param
ORDER BY Style DESC;';  

-- Return handle for calling application
SELECT @P1;
GO
```
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```
-----------
1

(1 row affected)
```

Puis l’application exécute la requête deux fois à l’aide de la valeur du handle 1, avant de supprimer le plan préparé.

```sql
EXEC sp_execute 1, 49879;  
GO

EXEC sp_execute 1, 48766;
GO

EXEC sp_unprepare 1; 
GO
```
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  

