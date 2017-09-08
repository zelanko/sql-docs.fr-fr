---
title: DELETE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DELETE
- DELETE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- row removal [SQL Server]
- DELETE statement [SQL Server], about DELETE statement
- views [SQL Server], deleting rows
- removing rows
- tables [SQL Server], deleting rows
- DELETE statement [SQL Server]
- deleting rows
- row removal [SQL Server], DELETE statement
- deleting data
ms.assetid: ed6b2105-0f35-408f-ba51-e36ade7ad5b2
caps.latest.revision: 78
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9b4238aeb45bd18a5b868640af235985f33ccb4c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="delete-transact-sql"></a>DELETE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Supprime une ou plusieurs lignes d’une table ou une vue dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
[ WITH <common_table_expression> [ ,...n ] ]  
DELETE   
    [ TOP ( expression ) [ PERCENT ] ]   
    [ FROM ]   
    { { table_alias  
      | <object>   
      | rowset_function_limited   
      [ WITH ( table_hint_limited [ ...n ] ) ] }   
      | @table_variable  
    }  
    [ <OUTPUT Clause> ]  
    [ FROM table_source [ ,...n ] ]   
    [ WHERE { <search_condition>   
            | { [ CURRENT OF   
                   { { [ GLOBAL ] cursor_name }   
                       | cursor_variable_name   
                   }   
                ]  
              }  
            }   
    ]   
    [ OPTION ( <Query Hint> [ ,...n ] ) ]   
[; ]  
  
<object> ::=  
{   
    [ server_name.database_name.schema_name.   
      | database_name. [ schema_name ] .   
      | schema_name.  
    ]  
    table_or_view_name   
}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DELETE FROM [database_name . [ schema ] . | schema. ] table_name    
    [ WHERE <search_condition> ]   
    [ OPTION ( <query_options> [ ,...n ]  ) ]  
[; ]  
```  
  
## <a name="arguments"></a>Arguments  
 AVEC \<common_table_expression >  
 Spécifie l'ensemble de résultats nommé temporaire, également appelé « expression de table commune », défini dans l'étendue de l'instruction DELETE. Le jeu de résultats est dérivé d'une instruction SELECT.  
  
 Les expressions de table communes peuvent également s'utiliser avec les instructions SELECT, INSERT, UPDATE et CREATE VIEW. Pour plus d’informations, consultez [avec common_table_expression &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 HAUT **(***expression***)** [%]  
 Spécifie le nombre ou le pourcentage de lignes aléatoires qui seront supprimées. L'argument*expression* peut être un nombre ou un pourcentage de lignes. Les lignes référencées dans l'expression TOP utilisée dans les instructions INSERT, UPDATE ou DELETE ne sont pas triées dans un ordre précis. Pour plus d’informations, consultez [TOP &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
 FROM  
 Mot clé facultatif qui peut être utilisé entre le mot clé DELETE et la cible *nom_table_ou_vue*, ou *fonction_ensemble_de_lignes_limitée*.  
  
 *alias_de_table*  
 L’alias spécifié dans l’argument *table_source* clause représentant la table ou la vue à partir de laquelle les lignes doivent être supprimés.  
  
 *nom_serveur*  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Le nom du serveur (à l’aide d’un nom de serveur lié ou [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md) fonctionner en tant que le nom du serveur) sur lequel se trouve la table ou la vue. Si *nom_serveur* est spécifié, *nom_base_de_données* et *nom_schéma* sont requis.  
  
 *database_name*  
 Nom de la base de données.  
  
 *schema_name*  
 Nom du schéma auquel appartient la vue ou la table.  
  
 *table_or view_name*  
 Nom de la table ou de la vue à partir desquelles les lignes doivent être supprimées.  
  
 Une variable de table, dans son étendue, est également utilisable comme source de la table dans une instruction DELETE.  
  
 La vue référencée par *nom_table_ou_vue* doit être mis à jour et faire référence exactement à une table de base dans la clause FROM de la définition de vue. Pour plus d’informations sur les vues de mettre à jour, consultez [CREATE VIEW &#40; Transact-SQL &#41; ](../../t-sql/statements/create-view-transact-sql.md).  
  
 *rowset_function_limited*  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Soit le [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md) ou [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) fonction, selon les possibilités du fournisseur.  
  
 AVEC **(** \<table_hint_limited > [... *n*] **)**  
 Spécifie un ou plusieurs indicateurs de table autorisés pour une table cible. Le mot clé WITH et les parenthèses sont obligatoires. NOLOCK et READUNCOMMITTED ne sont pas autorisés. Pour plus d’informations sur les indicateurs de table, consultez [indicateurs de Table &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-table.md).  
  
 \<OUTPUT_Clause >  
 Retourne des lignes supprimées ou des expressions basées sur ces lignes au cours de l'exécution de l'opération DELETE. Aucune instruction DML ciblant des vues ou des tables distantes ne prend en charge la clause OUTPUT. Pour plus d’informations, consultez [Clause OUTPUT &#40; Transact-SQL &#41; ](../../t-sql/queries/output-clause-transact-sql.md).  
  
 À partir de *table_source*  
 Spécifie une clause FROM supplémentaire. Cela [!INCLUDE[tsql](../../includes/tsql-md.md)] extension Delete permet de spécifier des données de \<table_source > et supprimer les lignes correspondantes de la table dans la première clause.  
  
 Cette extension, qui spécifie une jointure, peut être utilisée dans la clause WHERE à la place d'une sous-requête pour identifier les lignes à supprimer.  
  
 Pour plus d’informations, consultez [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md).  
  
 WHERE  
 Spécifie les conditions limitant le nombre de lignes à supprimer. Si une clause WHERE n'est pas spécifiée, DELETE supprime toutes les lignes de la table.  
  
 Il existe deux types d'opérations de suppression, en fonction des conditions définies dans la clause WHERE :  
  
-   Une suppression par recherche spécifie une condition de recherche permettant de désigner les lignes à supprimer. Par exemple, où *column_name* = *valeur*.  
  
-   Une suppression positionnée utilise la clause CURRENT OF pour spécifier un curseur. La suppression a lieu à la position actuelle du curseur. Cela peut être plus précise qu’une instruction DELETE par recherche qui utilise WHERE *search_condition* clause pour qualifier les lignes à supprimer. Une instruction DELETE par recherche supprime plusieurs lignes si la condition de recherche n'identifie pas de façon univoque une ligne unique.  
  
\<search_condition >  
 Spécifie les conditions de limitation applicables aux lignes à supprimer. Le nombre de prédicats inclus dans une condition de recherche est illimité. Pour plus d’informations, consultez [Condition de recherche &#40; Transact-SQL &#41; ](../../t-sql/queries/search-condition-transact-sql.md).  
  
 CURRENT OF  
 Spécifie que l'instruction DELETE s'effectue à l'emplacement actuel du curseur spécifié.  
  
 GLOBAL  
 Spécifie que *cursor_name* fait référence à un curseur global.  
  
 *tous les autres cas*  
 Nom du curseur ouvert à partir duquel a lieu l'extraction. Si un global et un curseur local portant le nom *cursor_name* existe, cet argument fait référence au curseur global si GLOBAL est spécifié ; sinon, elle fait référence au curseur local. Le curseur doit pouvoir gérer les mises à jour.  
  
 *nom_de_variable_de_curseur*  
 Nom d'une variable curseur. La variable de curseur doit référencer un curseur qui autorise les mises à jour.  
  
 OPTION **(** \<query_hint > [ **,**... *n*] **)**  
 Mots clés spécifiant les indicateurs d’optimiseur sont utilisés pour personnaliser la façon dont le [!INCLUDE[ssDE](../../includes/ssde-md.md)] traite l’instruction. Pour plus d’informations, consultez [Indicateurs de requête &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Pour supprimer toutes les lignes dans une table, utilisez TRUNCATE TABLE. TRUNCATE TABLE est plus rapide et utilise moins de ressources du système et du journal des transactions que l'instruction DELETE. TRUNCATE TABLE présente des restrictions, par exemple, la table ne peut pas participer à la réplication. Pour plus d’informations, consultez [TRUNCATE TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/truncate-table-transact-sql.md)  
  
 Utilisez le @@ROWCOUNT fonction pour retourner le nombre de supprimer des lignes à l’application cliente. Pour plus d’informations, consultez [@@ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/functions/rowcount-transact-sql.md).  
  
## <a name="error-handling"></a>Gestion des erreurs  
 Vous pouvez implémenter la gestion des erreurs pour l'instruction DELETE en spécifiant cette dernière dans une construction TRY…CATCH.  
  
 L'instruction DELETE peut échouer si elle viole un déclencheur ou si elle essaie de supprimer une ligne référencée par des données dans une autre table avec une contrainte FOREIGN KEY. Si l'instruction DELETE supprime plusieurs lignes et qu'une de ces lignes viole un déclencheur ou une contrainte, une erreur est retournée et aucune ligne n'est supprimée.  
  
 Lorsqu’une instruction DELETE rencontre une erreur arithmétique (dépassement de capacité, division par zéro ou erreur de domaine) lors de l’évaluation d’expression, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] gère ces erreurs comme si SET ARITHABORT a la valeur ON. Le reste du lot est annulé et un message d'erreur est retourné.  
  
## <a name="interoperability"></a>Interopérabilité  
 DELETE peut s'utiliser dans le corps d'une fonction définie par l'utilisateur si l'objet modifié est une variable de table.  
  
 Lorsque vous supprimez une ligne qui contient une colonne FILESTREAM, vous supprimez également ses fichiers de système de fichiers sous-jacents. Les fichiers sous-jacents sont supprimés par le garbage collector FILESTREAM. Pour plus d’informations, consultez [accéder aux données de FILESTREAM avec Transact-SQL](../../relational-databases/blob/access-filestream-data-with-transact-sql.md).  
  
 Il n'est pas possible de spécifier la clause FROM dans une instruction DELETE qui référence directement ou indirectement une vue sur laquelle est défini le déclencheur INSTEAD OF. Pour plus d’informations sur les déclencheurs INSTEAD OF, consultez [CREATE TRIGGER &#40; Transact-SQL &#41; ](../../t-sql/statements/create-trigger-transact-sql.md).  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Lorsque TOP est utilisé avec DELETE, les lignes référencées ne sont pas réorganisées dans un ordre particulier et la clause ORDER BY ne peut pas être spécifiée directement dans cette instruction. Si vous devez utiliser une clause TOP pour supprimer des lignes dans un ordre chronologique significatif, vous devez associer à cette clause TOP une clause ORDER BY dans une instruction de sous-sélection. Consultez la section Exemples plus loin dans cette rubrique.  
  
 TOP ne peut pas être utilisé dans une instruction DELETE avec des vues partitionnées.  
  
## <a name="locking-behavior"></a>Comportement de verrouillage  
 Par défaut, une instruction DELETE acquiert toujours un verrou exclusif (X) sur la table qu'il modifie et maintient ce verrou jusqu'à la fin de la transaction. Un verrou exclusif (X) empêche toute autre transaction de modifier les données ; les opérations de lecture ne peuvent avoir lieu qu'avec l'indicateur NOLOCK ou le niveau d'isolation « lecture non validée ». Vous pouvez spécifier des indicateurs de table pour remplacer ce comportement par défaut pour la durée de l'instruction DELETE en spécifiant une autre méthode de verrouillage ; toutefois, nous vous recommandons de ne recourir aux indicateurs qu'en dernier ressort et seulement si vous êtes un développeur ou un administrateur de base de données expérimenté. Pour plus d’informations, consultez [Indicateurs de table &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md).  
  
 Lorsque des lignes sont supprimées à partir d’un segment de mémoire du [!INCLUDE[ssDE](../../includes/ssde-md.md)] peut utiliser pour l’opération de verrouillage de page ou de ligne. Par conséquent, les pages rendues vides par l'opération de suppression demeurent allouées au segment de mémoire. Lorsque des pages vides ne sont pas désallouées, l'espace associé ne peut pas être réutilisé par d'autres objets dans la base de données.  
  
 Pour supprimer des lignes d'un segment de mémoire et désallouer des pages, utilisez l'une des méthodes suivantes.  
  
-   Spécifiez l'indicateur TABLOCK dans l'instruction DELETE. Grâce à l'indicateur TABLOCK, l'opération de suppression utilise un verrou exclusif sur la table au lieu d'un verrou de ligne ou de page. Les pages sont ainsi désallouées. Pour plus d’informations sur l’indicateur TABLOCK, consultez [indicateurs de Table &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-table.md).  
  
-   Utilisez TRUNCATE TABLE si toutes les lignes doivent être supprimées de la table.  
  
-   Créez un index cluster sur le segment de mémoire avant de supprimer les lignes. Vous pouvez supprimer l'index cluster après avoir supprimé les lignes. Cette méthode prend plus de temps que les méthodes précédentes et utilise davantage de ressources temporaires.  
  
> [!NOTE]  
>  Pages vides peuvent être supprimées à partir d’un segment de mémoire à tout moment à l’aide de la `ALTER TABLE <table_name> REBUILD` instruction.  
  
## <a name="logging-behavior"></a>Comportement de journalisation  
 L'instruction DELETE est toujours entièrement journalisée.  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 Les autorisations DELETE sont requises sur la table cible. Des autorisations SELECT sont également requises si l'instruction comporte une clause WHERE.  
  
 SUPPRIMER les autorisations par défaut aux membres de la **sysadmin** rôle serveur fixe le **db_owner** et **db_datawriter** les rôles de base de données et le propriétaire de la table. Membres de la **sysadmin**, **db_owner**et le **db_securityadmin** rôles et le propriétaire de la table peuvent transférer des autorisations à d’autres utilisateurs.  
  
## <a name="examples"></a>Exemples  
  
|Catégorie|Éléments syntaxiques proposés|  
|--------------|------------------------------|  
|[Syntaxe de base](#BasicSyntax)|DELETE|  
|[Limitation des lignes supprimées](#LimitRows)|WHERE • FROM • curseur •|  
|[Suppression de lignes dans une table distante](#RemoteTables)|Serveur lié • fonction d'ensemble de lignes OPENQUERY • fonction d'ensemble de lignes OPENDATASOURCE|  
|[Capture des résultats de l’instruction DELETE](#CaptureResults)|Clause OUTPUT|  
  
###  <a name="BasicSyntax"></a>Syntaxe de base  
 Les exemples fournis dans cette section présentent les fonctionnalités de base de l'instruction DELETE en utilisant la syntaxe minimale requise.  
  
#### <a name="a-using-delete-with-no-where-clause"></a>A. Utilisation de DELETE sans clause WHERE  
 L'exemple suivant supprime toutes les lignes de la table `SalesPersonQuotaHistory` dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)], car aucune clause WHERE ne limite le nombre de lignes supprimées.  
  
```  
DELETE FROM Sales.SalesPersonQuotaHistory;  
GO  
```  
  
###  <a name="LimitRows"></a>Limitation des lignes supprimées  
 Les exemples de cette section montrent comment limiter le nombre de lignes qui seront supprimées.  
  
#### <a name="b-using-the-where-clause-to-delete-a-set-of-rows"></a>B. Utilisation de la clause WHERE pour supprimer un jeu de lignes  
 L’exemple suivant supprime toutes les lignes de la `ProductCostHistory` de table dans le [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de données dans laquelle la valeur de la `StandardCost` colonne est plus de `1000.00`.  
  
```    
DELETE FROM Production.ProductCostHistory  
WHERE StandardCost > 1000.00;  
GO  
```  
  
 L'exemple suivant illustre une clause WHERE plus complexe. La clause WHERE définit deux conditions qui doivent être rencontrées pour déterminer les lignes à supprimer. La valeur dans la colonne `StandardCost` doit être comprise entre `12.00` et `14.00` , tandis que la valeur dans la colonne `SellEndDate` doit être Null. L’exemple imprime également la valeur de la **@@ROWCOUNT**  fonction pour retourner le nombre de nombre de lignes supprimées.  
  
```  
DELETE Production.ProductCostHistory  
WHERE StandardCost BETWEEN 12.00 AND 14.00  
      AND EndDate IS NULL;  
PRINT 'Number of rows deleted is ' + CAST(@@ROWCOUNT as char(3));  
```  
  
#### <a name="c-using-a-cursor-to-determine-the-row-to-delete"></a>C. Utilisation d'un curseur pour déterminer la ligne à supprimer  
 L’exemple suivant supprime une ligne de la `EmployeePayHistory` de table dans le [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] de la base de données à l’aide d’un curseur nommé `my`_`cursor`. La suppression est appliquée uniquement à la ligne actuellement extraite à partir du curseur.  
  
```  
DECLARE complex_cursor CURSOR FOR  
    SELECT a.BusinessEntityID  
    FROM HumanResources.EmployeePayHistory AS a  
    WHERE RateChangeDate <>   
         (SELECT MAX(RateChangeDate)  
          FROM HumanResources.EmployeePayHistory AS b  
          WHERE a.BusinessEntityID = b.BusinessEntityID) ;  
OPEN complex_cursor;  
FETCH FROM complex_cursor;  
DELETE FROM HumanResources.EmployeePayHistory  
WHERE CURRENT OF complex_cursor;  
CLOSE complex_cursor;  
DEALLOCATE complex_cursor;  
GO  
```  
  
#### <a name="d-using-joins-and-subqueries-to-data-in-one-table-to-delete-rows-in-another-table"></a>D. Utilisation de jointures et de sous-requêtes sur les données d'une table pour supprimer des lignes dans une autre table  
 Les exemples suivants illustrent deux façons de supprimer des lignes dans une table selon les données figurant dans une autre table. Dans les deux exemples, des lignes de la `SalesPersonQuotaHistory` de table dans le [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de données sont supprimés en fonction des ventes year-to-date stockées dans le `SalesPerson` table. La première `DELETE` instruction montre la solution de sous-requête compatible ISO tandis que la seconde `DELETE` montre l’instruction le [!INCLUDE[tsql](../../includes/tsql-md.md)] à partir de l’extension pour joindre les deux tables.  
  
```  
-- SQL-2003 Standard subquery  
  
DELETE FROM Sales.SalesPersonQuotaHistory   
WHERE BusinessEntityID IN   
    (SELECT BusinessEntityID   
     FROM Sales.SalesPerson   
     WHERE SalesYTD > 2500000.00);  
GO  
```  
  
```  
-- Transact-SQL extension  
  
DELETE FROM Sales.SalesPersonQuotaHistory   
FROM Sales.SalesPersonQuotaHistory AS spqh  
INNER JOIN Sales.SalesPerson AS sp  
ON spqh.BusinessEntityID = sp.BusinessEntityID  
WHERE sp.SalesYTD > 2500000.00;  
GO  
```  
  
```  
-- No need to mention target table more than once.  
  
DELETE spqh  
  FROM  
        Sales.SalesPersonQuotaHistory AS spqh  
    INNER JOIN Sales.SalesPerson AS sp  
        ON spqh.BusinessEntityID = sp.BusinessEntityID  
  WHERE  sp.SalesYTD > 2500000.00;  
```  
  
#### <a name="e-using-top-to-limit-the-number-of-rows-deleted"></a>E. Utilisation de TOP pour limiter le nombre de lignes supprimées  
 Lorsque TOP (*n*) clause est utilisée avec DELETE, l’opération de suppression est effectuée sur une sélection aléatoire de  *n*  nombre de lignes. L’exemple suivant supprime `20` lignes aléatoires à partir de la `PurchaseOrderDetail` de table dans le [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de données qui ont dû les dates antérieures au 1er juillet 2006.  
  
```  
DELETE TOP (20)   
FROM Purchasing.PurchaseOrderDetail  
WHERE DueDate < '20020701';  
GO  
```  
  
 Si vous devez utiliser une clause TOP pour supprimer des lignes dans un ordre chronologique significatif, vous devez associer à cette clause TOP une clause ORDER BY dans une instruction de sous-sélection. La requête suivante supprime les 10 lignes de la table `PurchaseOrderDetail` dont la date d'expiration est la plus proche. Pour garantir que seules 10 lignes sont supprimées, la colonne spécifiée dans l'instruction de sous-sélection (`PurchaseOrderID`) constitue la clé primaire de la table. L'utilisation d'une colonne non-clé dans l'instruction de sous-sélection peut entraîner la suppression de plus de 10 lignes si la colonne spécifiée contient des valeurs dupliquées.  
  
```  
DELETE FROM Purchasing.PurchaseOrderDetail  
WHERE PurchaseOrderDetailID IN  
   (SELECT TOP 10 PurchaseOrderDetailID   
    FROM Purchasing.PurchaseOrderDetail   
    ORDER BY DueDate ASC);  
GO  
```  
  
###  <a name="RemoteTables"></a>Suppression de lignes dans une Table distante  
 Exemples de cette section montrent comment supprimer des lignes dans une table distante en utilisant un [serveur lié](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) ou un [fonction d’ensemble de lignes](../../t-sql/functions/rowset-functions-transact-sql.md) pour référencer la table distante. Une table distante existe sur un serveur différent ou une instance différente de SQL Server.  
  
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
#### <a name="f-deleting-data-from-a-remote-table-by-using-a-linked-server"></a>F. Suppression de données dans une table distante en utilisant un serveur lié  
 L'exemple ci-dessous supprime des lignes dans une table distante. L’exemple commence par créer un lien vers la source de données à distance à l’aide de [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md). Le nom du serveur lié, `MyLinkServer`, est ensuite spécifié dans le cadre de l’objet en quatre parties sous la forme *server.catalog.schema.object*.  
  
```  
USE master;  
GO  
-- Create a link to the remote data source.   
-- Specify a valid server name for @datasrc as 'server_name' or 'server_name\instance_name'.  
  
EXEC sp_addlinkedserver @server = N'MyLinkServer',  
    @srvproduct = N' ',  
    @provider = N'SQLNCLI',   
    @datasrc = N'server_name',  
    @catalog = N'AdventureWorks2012';  
GO  
```  
  
```  
-- Specify the remote data source using a four-part name   
-- in the form linked_server.catalog.schema.object.  
  
DELETE MyLinkServer.AdventureWorks2012.HumanResources.Department 
WHERE DepartmentID > 16;  
GO  
```  
  
#### <a name="g-deleting-data-from-a-remote-table-by-using-the-openquery-function"></a>G. Suppression de données dans une table distante en utilisant la fonction OPENQUERY  
 L’exemple suivant supprime des lignes dans une table distante en spécifiant le [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md) fonction d’ensemble de lignes. Le nom de serveur lié créé dans l'exemple précédent est utilisé dans cet exemple.  
  
```  
DELETE OPENQUERY (MyLinkServer, 'SELECT Name, GroupName 
FROM AdventureWorks2012.HumanResources.Department  
WHERE DepartmentID = 18');  
GO  
```  
  
#### <a name="h-deleting-data-from-a-remote-table-by-using-the-opendatasource-function"></a>H. Suppression de données dans une table distante en utilisant la fonction OPENDATASOURCE  
 L’exemple suivant supprime des lignes dans une table distante en spécifiant le [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md) fonction d’ensemble de lignes. Spécifiez un nom de serveur valide pour la source de données en utilisant le format *nom_serveur* ou *nom_serveur\nom_instance*.  
  
```  
DELETE FROM OPENDATASOURCE('SQLNCLI',  
    'Data Source= <server_name>; Integrated Security=SSPI')  
    .AdventureWorks2012.HumanResources.Department   
WHERE DepartmentID = 17;'  
```  
  
###  <a name="CaptureResults"></a>Capture des résultats de l’instruction DELETE  
  
#### <a name="i-using-delete-with-the-output-clause"></a>I. Utilisation de DELETE avec la clause OUTPUT  
 L’exemple suivant montre comment enregistrer les résultats d’une `DELETE` instruction à une variable de table dans le [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de données.  
  
```  
DELETE Sales.ShoppingCartItem  
OUTPUT DELETED.*   
WHERE ShoppingCartID = 20621;  
  
--Verify the rows in the table matching the WHERE clause have been deleted.  
SELECT COUNT(*) AS [Rows in Table] 
FROM Sales.ShoppingCartItem 
WHERE ShoppingCartID = 20621;  
GO  
```  
  
#### <a name="j-using-output-with-fromtablename-in-a-delete-statement"></a>J. Utilisation de la clause OUTPUT avec <from_table_name> dans une instruction DELETE  
 L’exemple suivant supprime les lignes dans le `ProductProductPhoto` de table dans le [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de données en fonction de critères de recherche définis dans le `FROM` clause de la `DELETE` instruction. La clause `OUTPUT` retourne les colonnes `DELETED.ProductID`, `DELETED.ProductPhotoID`de la table en cours de suppression et les colonnes de la table `Product` . Cette méthode s'utilise dans la clause `FROM` pour spécifier les lignes à supprimer.  
  
```  
DECLARE @MyTableVar table (  
    ProductID int NOT NULL,   
    ProductName nvarchar(50)NOT NULL,  
    ProductModelID int NOT NULL,   
    PhotoID int NOT NULL);  
  
DELETE Production.ProductProductPhoto  
OUTPUT DELETED.ProductID,  
       p.Name,  
       p.ProductModelID,  
       DELETED.ProductPhotoID  
    INTO @MyTableVar  
FROM Production.ProductProductPhoto AS ph  
JOIN Production.Product as p   
    ON ph.ProductID = p.ProductID   
    WHERE p.ProductModelID BETWEEN 120 and 130;  
  
--Display the results of the table variable.  
SELECT ProductID, ProductName, ProductModelID, PhotoID   
FROM @MyTableVar  
ORDER BY ProductModelID;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="k-delete-all-rows-from-a-table"></a>K. Supprimer toutes les lignes d’une table  
 L'exemple suivant supprime toutes les lignes de la table `Table1`car aucune clause WHERE ne limite le nombre de lignes supprimées.  
  
```  
DELETE FROM Table1;  
```  
  
### <a name="l-delete-a-set-of-rows-from-a-table"></a>L. SUPPRIMER un ensemble de lignes d’une table  
 L’exemple suivant supprime toutes les lignes de la `Table1` table qui a une valeur supérieure à 1 000,00 dans les `StandardCost` colonne.  
  
```  
DELETE FROM Table1  
WHERE StandardCost > 1000.00;  
```  
  
### <a name="m-using-label-with-a-delete-statement"></a>M. À l’aide d’étiquette avec une instruction DELETE  
 L’exemple suivant utilise une étiquette avec l’instruction DELETE.  
  
```  
DELETE FROM Table1  
OPTION ( LABEL = N'label1' );  
  
```  
  
### <a name="n-using-a-label-and-a-query-hint-with-the-delete-statement"></a>N. À l’aide d’une étiquette et un indicateur de requête avec l’instruction DELETE  
 Cette requête affiche la syntaxe de base pour l’utilisation d’un indicateur de jointure de requête avec l’instruction DELETE. Pour plus d’informations sur les indicateurs de jointure et l’utilisation de la clause OPTION, consultez [OPTION (SQL Server PDW)](http://msdn.microsoft.com/en-us/72bbce98-305b-42fa-a19f-d89620621ecc).  
  
```  
-- Uses AdventureWorks  
  
DELETE FROM dbo.FactInternetSales  
WHERE ProductKey IN (   
    SELECT T1.ProductKey FROM dbo.DimProduct T1   
    JOIN dbo.DimProductSubcategory T2  
    ON T1.ProductSubcategoryKey = T2.ProductSubcategoryKey  
    WHERE T2.EnglishProductSubcategoryName = 'Road Bikes' )  
OPTION ( LABEL = N'CustomJoin', HASH JOIN ) ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [TRUNCATE TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/truncate-table-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [AVEC l’expression de table commune &#40; Transact-SQL &#41;](../../t-sql/queries/with-common-table-expression-transact-sql.md)   
 [@@ROWCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/rowcount-transact-sql.md)  
  
  


