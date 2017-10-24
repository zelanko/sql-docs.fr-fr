---
title: "CRÉER (fonction) (entrepôt de données SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8cad1b2c-5ea0-4001-9060-2f6832ccd057
caps.latest.revision: 14
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 55f1b7e612a1c7d120e06078b0fdba45d6409d36
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-function-sql-data-warehouse"></a>CRÉER (fonction) (entrepôt de données SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Crée une fonction définie par l'utilisateur dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Une fonction définie par l’utilisateur est un [!INCLUDE[tsql](../../includes/tsql-md.md)] routine qui accepte des paramètres, exécute une action, par exemple un calcul complexe et retourne le résultat de cette action en tant que valeur. La valeur de retour doit être une valeur scalaire (unique). Utilisez cette instruction pour créer une routine réutilisable, exploitable :  
  
-   dans des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] telles que SELECT ;  
  
-   dans des applications appelant la fonction ;  
  
-   dans la définition d'une autre fonction définie par l'utilisateur ;  
  
-   pour définir une contrainte CHECK sur une colonne ;  
  
-   pour remplacer une procédure stockée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
--Transact-SQL Scalar Function Syntax  
CREATE FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
  ]  
)  
RETURNS return_data_type  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    BEGIN   
        function_body   
        RETURN scalar_expression  
    END  
[ ; ]  
  
<function_option>::=   
{  
    [ SCHEMABINDING ]  
  | [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]  
}  
  
```  
  
## <a name="arguments"></a>Arguments  
 *schema_name*  
 Nom du schéma auquel appartient la fonction définie par l'utilisateur.  
  
 *nom de la fonction*  
 Nom de la fonction définie par l'utilisateur. Les noms de fonctions doivent être conformes aux règles des identificateurs et doivent être uniques au sein de la base de données et son schéma.  
  
> [!NOTE]  
>  Les parenthèses sont requises après le nom de fonction même si aucun paramètre n'est spécifié.  
  
 @*nom_paramètre*  
 Paramètre dans la fonction définie par l'utilisateur. Un ou plusieurs paramètres peuvent être déclarés.  
  
 Une fonction peut comprendre au maximum 2 100 paramètres. La valeur de chaque paramètre déclaré doit être fournie par l'utilisateur lors de l'exécution de la fonction, sauf si vous définissez une valeur par défaut pour le paramètre.  
  
 Spécifiez un nom de paramètre en plaçant le signe @ comme premier caractère. Le nom de paramètre doit suivre les règles applicables aux identificateurs. Un paramètre étant local à une fonction, vous pouvez utiliser le même nom dans d'autres fonctions. Les paramètres ne peuvent que prendre la place de constantes ; ils ne peuvent pas être utilisés à la place de noms de tables, de colonnes ou d'autres objets de base de données.  
  
> [!NOTE]  
>  ANSI_WARNINGS n'est pas honoré lorsque vous transmettez des paramètres dans une procédure stockée, dans une fonction définie par l'utilisateur ou lorsque vous déclarez et définissez des variables dans une instruction par lot. Par exemple, si une variable est définie en tant que **char (3)**, puis définissez une valeur supérieure à trois caractères, les données sont tronquées à la taille définie et l’insertion ou instruction de mise à jour réussit.  
  
 *parameter_data_type*  
 Est le type de données de paramètre. Pour [!INCLUDE[tsql](../../includes/tsql-md.md)] fonctions, tous les types de données scalaires pris en charge dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] sont autorisées. Le type de données d’horodatage (rowversion) n’est pas un type pris en charge.  
  
 [=*par défaut* ]  
 Valeur par défaut pour le paramètre. Si un *par défaut* la valeur est définie, la fonction peut être exécutée sans spécifier de valeur pour ce paramètre.  
  
 Lorsque l'un des paramètres de la fonction possède une valeur par défaut, le mot clé DEFAULT doit être spécifié lors de l'appel de la fonction afin de récupérer la valeur par défaut. Ce comportement est différent de l'utilisation de paramètres avec des valeurs par défaut dans des procédures stockées pour lesquelles l'omission du paramètre implique également la prise en compte de la valeur par défaut.  
  
 *return_data_type*  
 Valeur de retour d'une fonction scalaire définie par l'utilisateur. Pour [!INCLUDE[tsql](../../includes/tsql-md.md)] fonctions, tous les types de données scalaires pris en charge dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] sont autorisées. Le type de données d’horodatage (rowversion) n’est pas un type pris en charge. Les types non scalaires du curseur et la table ne sont pas autorisés.  
  
 *function_body*  
 Série de [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions.  Le function_body ne peut pas contenir une instruction SELECT et ne peut pas référencer les données de la base de données.  Le function_body ne peut pas référencer des tables ou des vues. Le corps de la fonction peut appeler d’autres fonctions déterministes mais ne peut pas appeler les fonctions non déterministes. 
  
 Dans les fonctions scalaires, *function_body* est une série de [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions ensemble, retournent une valeur scalaire.  
  
 *scalar_expression*  
 Indique la valeur scalaire retournée par la fonction scalaire.  
  
 **\<function_option > :: =** 
  
 Spécifie que la fonction aura une ou plusieurs des options ci-dessous.  
  
 SCHEMABINDING  
 Indique que la fonction est liée aux objets de base de données auxquels elle fait référence. Si SCHEMABINDING est précisé, les objets de base ne peuvent pas être modifiés d'une manière susceptible d'affecter la définition de la fonction. Cette dernière doit d'ailleurs être modifiée ou supprimée au préalable pour supprimer les dépendances par rapport à l'objet qui doit être modifié.  
  
 La liaison de la fonction aux objets auxquels elle fait référence est supprimée uniquement lorsqu'une des actions suivantes se produit :  
  
-   La fonction est supprimée.  
  
-   La fonction est modifiée, avec l'instruction ALTER, sans spécification de l'option SCHEMABINDING.  
  
 Une fonction peut être liée au schéma uniquement si les conditions suivantes sont vérifiées :  
  
-   Toutes les fonctions définies par l’utilisateur référencées par la fonction sont également liées au schéma.  
  
-   Les fonctions et les autres fonctions référencées par la fonction sont référencées à l’aide d’un nom d’une ou deux parties.  
  
-   Uniquement les fonctions intégrées et les autres fonctions dans la même base de données peuvent être référencées dans le corps de l’UDF.  
  
-   L'utilisateur qui exécute l'instruction CREATE FUNCTION dispose de l'autorisation REFERENCES pour les objets de base de données auxquels la fonction fait référence.  
  
 Pour supprimer SCHEMABINDING utiliser ALTER  
  
 RETOURNE LA VALEUR NULL EN ENTRÉE NULL | **APPELÉE SUR UNE ENTRÉE NULL**  
 Spécifie le **OnNULLCall** attribut d’une fonction scalaire. S'il n'est pas spécifié, l'argument CALLED ON NULL INPUT est implicite par défaut. Cela signifie que le corps de la fonction est exécuté même si la valeur NULL est transmise comme argument.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Si une fonction définie par l'utilisateur n'est pas créée avec la clause SCHEMABINDING, les modifications apportées aux objets sous-jacents peuvent affecter la définition de la fonction et produire des résultats inattendus en cas d'appel. Nous vous recommandons d'implémenter l'une des méthodes suivantes pour vous assurer que la fonction ne devient pas obsolète en raison des modifications apportées à ses objets sous-jacents :  
  
-   Spécifiez la clause WITH SCHEMABINDING lors de la création de la fonction. Vous vous assurez ainsi que les objets référencés dans la définition de la fonction ne peuvent pas être modifiés sauf si la fonction est également modifiée.  
  
## <a name="interoperability"></a>Interopérabilité  
 Les instructions suivantes sont valides dans une fonction :  
  
-   Instructions d'affectation  
  
-   Instructions de contrôle de flux à l'exception des instructions TRY...CATCH  
  
-   Instructions DECLARE définissant des variables de données locales.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Les fonctions définies par l'utilisateur ne permettent pas d'exécuter des actions qui modifient l'état des bases de données.  
  
 Les fonctions définies par l'utilisateur peuvent être imbriquées ; en d'autres termes, une fonction définie par l'utilisateur peut en appeler une autre. Le niveau d'imbrication est incrémenté lorsque la fonction appelée commence à s'exécuter, et décrémenté lorsque l'exécution est terminée. Les fonctions définies par l'utilisateur peuvent être imbriquées jusqu'à 32 niveaux. Le dépassement des niveaux d'imbrication maximum autorisés, provoque l'échec de la totalité de la chaîne de fonctions appelantes.   
  
## <a name="metadata"></a>Métadonnées  
 Cette section répertorie les affichages catalogue système que vous pouvez utiliser pour retourner des métadonnées sur les fonctions définies par l’utilisateur.  
  
 [Sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) : affiche la définition de [!INCLUDE[tsql](../../includes/tsql-md.md)] fonctions définies par l’utilisateur. Exemple :  
  
```  
SELECT definition, type   
FROM sys.sql_modules AS m  
JOIN sys.objects AS o   
    ON m.object_id = o.object_id   
    AND type = ('FN');  
GO  
  
```  
  
 [Sys.Parameters](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md) : affiche des informations sur les paramètres définis dans les fonctions définies par l’utilisateur.  
  
 [Sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) : affiche les objets sous-jacents référencés par une fonction.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation CREATE FUNCTION dans la base de données et l'autorisation ALTER sur le schéma dans lequel la fonction est en cours de création.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-using-a-scalar-valued-user-defined-function-to-change-a-data-type"></a>A. À l’aide d’une fonction scalaire de défini par l’utilisateur pour modifier un type de données  
 Cette fonction simple prend un **int** de type de données comme entrée et retourne un **Decimal (10,2)** type de données comme sortie.  
  
```  
CREATE FUNCTION dbo.ConvertInput (@MyValueIn int)  
RETURNS decimal(10,2)  
AS  
BEGIN  
    DECLARE @MyValueOut int;  
    SET @MyValueOut= CAST( @MyValueIn AS decimal(10,2));  
    RETURN(@MyValueOut);  
END;  
GO  
  
SELECT dbo.ConvertInput(15) AS 'ConvertedValue';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER FUNCTION (SQL Server PDW)](http://msdn.microsoft.com/en-us/25ff3798-eb54-4516-9973-d8f707a13f6c)   
 [SUPPRIMER la fonction (SQL Server PDW)](http://msdn.microsoft.com/en-us/1792a90d-0d06-4852-9dec-6de1b9cd229e)  
  
  



