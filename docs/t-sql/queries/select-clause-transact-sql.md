---
title: Clause SELECT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SELECT Clause
- SELECT_Clause_TSQL
- DISTINCT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- parentheses [SQL Server]
- identity columns [SQL Server], SELECT clause
- SELECT clause
- $IDENTITY keyword
- user-defined types [SQL Server], invoking methods and properties
- SELECT statement [SQL Server], processing orders
- clauses [SQL Server], SELECT
- $ROWGUID keyword
- queries [SQL Server], results
ms.assetid: 2616d800-4853-4cf1-af77-d32d68d8c2ef
caps.latest.revision: 54
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e8b6972868c221ec0368b689164eff740ae6f1a7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="select-clause-transact-sql"></a>Clause SELECT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Spécifie les colonnes doivent être retournées par la requête.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT [ ALL | DISTINCT ]  
[ TOP ( expression ) [ PERCENT ] [ WITH TIES ] ]   
<select_list>   
<select_list> ::=   
    {   
      *   
      | { table_name | view_name | table_alias }.*   
      | {  
          [ { table_name | view_name | table_alias }. ]  
               { column_name | $IDENTITY | $ROWGUID }   
          | udt_column_name [ { . | :: } { { property_name | field_name }   
            | method_name ( argument [ ,...n] ) } ]  
          | expression  
          [ [ AS ] column_alias ]   
         }  
      | column_alias = expression   
    } [ ,...n ]   
```  
  
## <a name="arguments"></a>Arguments  
 **ALL**  
 Indique que les doublons de lignes peuvent apparaître dans le jeu de résultats. ALL est l'argument par défaut.  
  
 DISTINCT  
 Indique que seules des lignes uniques peuvent apparaître dans le jeu de résultats. Les valeurs nulles sont considérées comme étant égales pour le mot clé DISTINCT.  
  
 HAUT (*expression* ) [%] [WITH TIES]  
 Indique que seul un premier ensemble ou pourcentage de lignes spécifié sera retourné à partir du jeu de résultats de la requête. L'argument*expression* peut être un nombre ou un pourcentage de lignes.  
  
 Pour la compatibilité descendante, à l’aide de la partie supérieure *expression* sans parenthèses dans Sélectionnez les instructions est pris en charge, mais nous ne recommandons pas il. Pour plus d’informations, consultez [TOP &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
\<select_list > les colonnes à sélectionner pour le jeu de résultats. La liste de sélection est une série d'expressions séparées par des virgules. Le nombre maximum d'expressions pouvant être spécifiées dans la liste de sélection est de 4096.  
  
 \*  
 Indique que toutes les colonnes de toutes les tables et vues de la clause FROM doivent être renvoyées. Les colonnes sont renvoyées par table ou vue, comme indiqué dans la clause FROM, et par ordre d'apparition dans la table ou la vue.  
  
 *nom_table* | *view_name* | *table*_*alias*. *  
 Limite l’étendue de la \* à la table ou vue spécifiée.  
  
 *nom_colonne*  
 Nom d'une colonne à renvoyer. Qualifier *column_name* pour éviter une référence ambiguë, ce qui se produit lorsque deux tables dans la clause FROM possèdent des colonnes avec des noms dupliqués. Par exemple, les tables SalesOrderHeader et SalesOrderDetail de le [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] base de données à la fois possèdent une colonne nommée ModifiedDate. Si les deux tables sont associées dans une requête, la date de modification des entrées SalesOrderDetail peut être spécifiée dans la liste de sélection en tant que SalesOrderDetail.ModifiedDate.  
  
 *expression*  
 Constante, fonction ou toute combinaison de noms de colonne, de constantes et de fonctions reliées par un ou plusieurs opérateurs, ou par une sous-requête.  
  
 $IDENTITY  
 Renvoie la colonne d'identité. Pour plus d’informations, consultez [IDENTITY &#40; Propriété &#41; &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql-identity-property.md), [ALTER TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-transact-sql.md), et [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).  
  
 Si plusieurs tables de la clause FROM possèdent une colonne dotée de la propriété IDENTITY, $IDENTITY doit être qualifié avec le nom de table approprié, tel que T1.$IDENTITY.  
  
 $ROWGUID  
 Retourne la colonne GUID de la ligne.  
  
 Si plusieurs tables de la clause FROM sont dotées de la propriété ROWGUIDCOL, $ROWGUID doit être qualifié avec le nom de table approprié, tel que T1.$ROWGUID.  
  
 *udt_column_name*  
 Nom d'une colonne de type CLR (Common Language Runtime) définie par l'utilisateur à retourner.  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] renvoie des valeurs d'un type défini par l'utilisateur en représentation binaire. Pour retourner des valeurs de type défini par l’utilisateur dans la chaîne ou au format XML, utilisez [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) ou [convertir](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
 { . | :: }  
 Spécifie une méthode, une propriété ou un champ d'un type CLR défini par l'utilisateur. À utiliser. pour une méthode, une propriété ou un champ d'instance (non statique). Utilisez :: pour une méthode, une propriété ou un champ statique. Pour appeler une méthode, une propriété ou un champ de type CLR défini par l'utilisateur, vous devez avoir l'autorisation EXECUTE sur le type.  
  
 *property_name*  
 Est une propriété publique de *udt_column_name*.  
  
 *nom_champ*  
 Est un membre de données public *udt_column_name*.  
  
 *nom_méthode*  
 Est une méthode publique de *udt_column_name* qui accepte un ou plusieurs arguments. *nom_méthode* ne peut pas être une méthode mutateur.  
  
 L'exemple ci-dessous sélectionne les valeurs pour la colonne `Location`, défini comme étant de type `point`, à partir de la table `Cities`, en invoquant une méthode du type appelé `Distance` :  
  
```  
CREATE TABLE dbo.Cities (  
     Name varchar(20),  
     State varchar(20),  
     Location point );  
GO  
DECLARE @p point (32, 23), @distance float;  
GO  
SELECT Location.Distance (@p)  
FROM Cities;  
```  
  
 *alias de column_*  
 Nom utilisé pour remplacer le nom de colonne dans le jeu de résultats de la requête. Par exemple, vous pouvez spécifier un alias tel que Quantité, Quantité à la date du jour ou Qté pour une colonne appelée quantité.  
  
 Les alias sont également utilisés pour spécifier les noms des résultats d'expressions, par exemple :  
  
 `USE AdventureWorks2012`;  
  
 `GO`  
  
 `SELECT AVG(UnitPrice) AS [Average Price]`  
  
 `FROM Sales.SalesOrderDetail;`  
  
 *column_alias* peut être utilisé dans une clause ORDER BY. Il ne peut toutefois pas être utilisé dans une clause WHERE, GROUP BY ou HAVING. Si l’expression de requête fait partie d’une instruction DECLARE CURSOR, *column_alias* ne peut pas être utilisé dans la clause FOR UPDATE.  
  
## <a name="remarks"></a>Notes  
 La longueur des données retournées pour **texte** ou **ntext** les colonnes qui sont inclus dans la liste de sélection a la valeur la plus petite valeur des éléments suivants : la taille réelle de la **texte** colonne, le paramètre de session TEXTSIZE par défaut ou la limite codée en dur l’application. Pour modifier la longueur du texte renvoyé dans une session, utilisez l'instruction SET. Par défaut, la limite de longueur pour des données textuelles renvoyées avec une instruction SELECT est de 4 Ko.  
  
 Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] déclenche l'exception 511 et annule l'instruction en cours d'exécution dans les cas suivants :  
  
-   L'instruction SELECT produit une ligne de résultats ou une ligne de table de travail intermédiaire excédant les 8060 octets.  
  
-   L'instruction DELETE, INSERT ou UPDATE tente d'opérer une action sur une ligne excédant les 8060 octets.  
  
 Une erreur se produit si aucun nom de colonne n'est attribué à une colonne créée par une instruction SELECT INTO ou CREATE VIEW.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples SELECT &#40; Transact-SQL &#41;](../../t-sql/queries/select-examples-transact-sql.md)   
 [Expressions &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
  
  

