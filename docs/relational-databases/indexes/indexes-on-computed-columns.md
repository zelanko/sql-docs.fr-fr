---
title: Index sur les colonnes calculées | Microsoft Docs
ms.custom: ''
ms.date: 11/19/2018
ms.prod: sql
ms.prod_service: table-view-index, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- computed columns, index creation
- index creation [SQL Server], computed columns
- imprecise columns
- persisted computed columns
- precise [SQL Server]
ms.assetid: 8d17ac9c-f3af-4bbb-9cc1-5cf647e994c4
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: de2efcf3b99e21284cf964b1cd43bc85027ecaac
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85760795"
---
# <a name="indexes-on-computed-columns"></a>Index sur les colonnes calculées
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Vous pouvez définir des index sur des colonnes calculées si les règles suivantes sont respectées :  
  
-   Conditions requises liées à la propriété  
-   Conditions requises liées au déterminisme  
-   Conditions requises liées à la précision  
-   Conditions requises liées aux types de données  
-   Conditions requises liées à l'option SET  
  
#### <a name="ownership-requirements"></a>Conditions requises liées à la propriété
  
Toutes les références de fonctions dans la colonne calculée doivent avoir le même propriétaire que la table.  
  
## <a name="determinism-requirements"></a>Conditions requises liées au déterminisme  

Une expression est déterministe lorsqu'elle retourne toujours le même résultat pour un ensemble donné d'entrées. La propriété **IsDeterministic** de la fonction [COLUMNPROPERTY](../../t-sql/functions/columnproperty-transact-sql.md) indique si un paramètre *computed_column_expression* est déterministe ou non.  
Le paramètre *computed_column_expression* doit être déterministe. Une *expression_de_colonne_calculée* est déterministe quand toutes les conditions suivantes sont vraies :  
  
-   Toutes les fonctions référencées par l'expression sont déterministes et précises, notamment les fonctions définies par l'utilisateur et les fonctions intégrées. Pour plus d’informations, consultez [Fonctions déterministes et non déterministes](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md). Les fonctions peuvent être imprécises si la colonne calculée est de type PERSISTED. Pour plus d’informations, consultez [Création d’index sur des colonnes calculées persistantes](#BKMK_persisted) , plus loin dans cette rubrique.  
  
-   Toutes les colonnes auxquelles l'expression fait référence proviennent de la table contenant la colonne calculée.  
  
-   Aucune référence de colonne n'extrait de données provenant de plusieurs lignes. Par exemple, certaines fonctions d’agrégation, telles que SUM ou AVG, dépendent de données provenant de plusieurs lignes et rendraient un paramètre *computed_column_expression* non déterministe.  
  
-   Le paramètre *computed_column_expression* n’a pas d’accès aux données système ni utilisateur.  
  
Une colonne calculée qui contient une expression CLR (Common Language Runtime) doit être déterministe et marquée comme PERSISTED avant de pouvoir être indexée. Les expressions de type CLR définies par l'utilisateur sont permises dans les définitions de colonnes calculées. Les colonnes calculées de type CLR définies par l'utilisateur peuvent être indexées à condition que le type soit comparable. Pour plus d’informations, consultez [Types CLR définis par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  

#### <a name="cast-and-convert"></a>CAST et CONVERT

Lorsque vous faites référence aux littéraux de chaîne de type de données de date dans des colonnes calculées indexées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il est recommandé de convertir explicitement le littéral dans le type de date souhaité à l'aide d'un style de format de date déterministe. Pour obtenir la liste des styles de formats de date déterministes, consultez [CAST et CONVERT](../../t-sql/functions/cast-and-convert-transact-sql.md). 

Pour plus d’informations, consultez [Conversion non déterministe de chaînes de date littérale en valeurs DATE](../../t-sql/data-types/nondeterministic-convert-date-literals.md).

#### <a name="compatibility-level"></a>Niveau de compatibilité

La conversion implicite de données de caractères non-Unicode entre les classements est considérée comme non déterministe, à moins que le niveau de compatibilité soit égal ou inférieur à 80.  

Lorsque le niveau de compatibilité de la base de données est égal à 90, vous ne pouvez pas créer d'index sur les colonnes calculées qui contiennent ces expressions. Cependant, les colonnes calculées existantes qui contiennent ces expressions provenant d'une base de données mise à niveau sont gérables. Si vous utilisez des colonnes calculées indexées contenant une chaîne implicite pour les conversions de dates, afin d'éviter tout endommagement éventuel d'index, assurez-vous que les paramètres LANGUAGE et DATEFORMAT sont cohérents dans vos bases de données et applications.

Le niveau de compatibilité 90 correspond à SQL Server 2005.



## <a name="precision-requirements"></a>Conditions requises liées à la précision
  
 Le paramètre *computed_column_expression* doit être précis. Un paramètre *computed_column_expression* est précis quand une ou plusieurs des conditions suivantes sont remplies :  
  
-   Il ne s’agit pas d’une expression des types de données **float** ou **real** .  
-   Il n’utilise pas un type de données **float** ou **real** dans sa définition. Par exemple, dans l’instruction suivante, la colonne `y` est de type **int** et déterministe, mais pas précise.  
  
    ```sql  
    CREATE TABLE t2 (a int, b int, c int, x float,   
       y AS CASE x   
             WHEN 0 THEN a   
             WHEN 1 THEN b   
             ELSE c   
          END);  
    ```  
  
> [!NOTE]  
> Toute expression **float** ou **real** est considérée comme non précise et ne peut pas être une clé d’index. Autrement dit, une expression **float** ou **real** peut être utilisée dans une vue indexée mais pas en tant que clé. Ce point s'applique également aux colonnes calculées. Toute fonction, expression ou fonction définie par l’utilisateur est considérée imprécise si elle contient des expressions **float** ou **real** , même logiques (comparaisons).  
  
La propriété **IsPrecise** de la fonction COLUMNPROPERTY indique si un paramètre *computed_column_expression* est précis ou non.  


## <a name="data-type-requirements"></a>Conditions requises liées aux types de données
  
-   Le paramètre *computed_column_expression* défini pour la colonne calculée ne peut pas correspondre aux types de données **text**, **ntext**ou **image** .  
-   Les colonnes calculées dérivées des types de données **image**, **ntext**, **text**, **varchar(max)** , **nvarchar(max)** , **varbinary(max)** et **xml** peuvent être indexées tant que le type de données de lacolonne calculée est autorisé en tant que colonne clé d’index.  
-   Les colonnes calculées dérivées des types de données **image**, **ntext**et **text** peuvent être des colonnes (incluses) non-clés dans un index non-cluster tant que le type de données utilisé dans la colonne calculée lui permet d’être une colonne d’index non-clés.  


## <a name="set-option-requirements"></a>Conditions requises liées à l'option SET
  
-   L'option de niveau de connexion ANSI_NULLS doit être activée (ON) lors de l'exécution de l'instruction CREATE TABLE ou ALTER TABLE qui définit la colonne calculée. La fonction [OBJECTPROPERTY](../../t-sql/functions/objectproperty-transact-sql.md) indique si l’option est activée par le biais de la propriété **IsAnsiNullsOn** .  
-   La connexion sur laquelle l'index est créé, ainsi que toutes les connexions tentant d'exécuter des instructions INSERT, UPDATE ou DELETE appelées à modifier des valeurs de l'index, doivent comporter six options SET activées (ON) et une désactivée (OFF). L'optimiseur ignore un index sur une colonne calculée dès qu'une instruction SELECT est exécutée par une connexion qui ne respecte pas ces paramètres d'options.  
  
    -   L'option NUMERIC_ROUNDABORT doit être désactivée (OFF) et les options suivantes doivent être activées (ON) :  
    -   ANSI_NULLS  
    -   ANSI_PADDING  
    -   ANSI_WARNINGS  
    -   ARITHABORT  
    -   CONCAT_NULL_YIELDS_NULL  
    -   QUOTED_IDENTIFIER  
  
> [!NOTE]
> L'affectation de la valeur ON à ANSI_WARNINGS affecte de manière implicite la valeur ON à ARITHABORT, lorsque le niveau de compatibilité de la base de données est d'au moins 90.  
  
## <a name="creating-indexes-on-persisted-computed-columns"></a><a name="BKMK_persisted"></a> Création d’index sur des colonnes calculées persistantes  

Parfois, vous pouvez créer une colonne calculée qui est définie par une expression déterministe, mais non précise. Vous pouvez le faire quand la colonne est marquée comme PERSISTED dans l’instruction CREATE TABLE ou ALTER TABLE.

Cela signifie que le [!INCLUDE[ssDE](../../includes/ssde-md.md)] stocke les valeurs calculées dans la table et qu'il les met à jour lorsque les autres colonnes dont dépendent les colonnes calculées sont mises à jour. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilise ces valeurs persistantes pour créer un index sur la colonne et lorsqu'une requête fait référence à l'index.

Cette option vous permet de créer un index sur une colonne calculée lorsque le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne peut pas prouver avec certitude qu'une fonction qui retourne des expressions de colonnes calculées, en particulier une fonction CLR créée dans [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], est à la fois déterministe et précise.  


  
## <a name="related-content"></a>Contenu associé  
 [COLUMNPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/columnproperty-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)    
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)
  
  
