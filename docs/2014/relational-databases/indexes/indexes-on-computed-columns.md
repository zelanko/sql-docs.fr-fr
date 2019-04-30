---
title: Index sur les colonnes calculées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: c5aa2bd118d99afea6a1ee6ea8f41c646146c32f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63162455"
---
# <a name="indexes-on-computed-columns"></a>Index sur les colonnes calculées
  Vous pouvez définir des index sur des colonnes calculées si les règles suivantes sont respectées :  
  
-   Conditions requises liées à la propriété  
  
-   Conditions requises liées au déterminisme  
  
-   Conditions requises liées à la précision  
  
-   Conditions requises liées aux types de données  
  
-   Conditions requises liées à l'option SET  
  
 **Ownership Requirements**  
  
 Toutes les références de fonctions dans la colonne calculée doivent avoir le même propriétaire que la table.  
  
 **Determinism Requirements**  
  
> [!IMPORTANT]  
>  Une expression est déterministe lorsqu'elle retourne toujours le même résultat pour un ensemble donné d'entrées. La propriété **IsDeterministic** de la fonction [COLUMNPROPERTY](/sql/t-sql/functions/columnproperty-transact-sql) indique si un paramètre *computed_column_expression* est déterministe ou non.  
  
 Le paramètre *computed_column_expression* doit être déterministe. Un paramètre *computed_column_expression* est déterministe quand une ou plusieurs des conditions suivantes sont remplies :  
  
-   Toutes les fonctions référencées par l'expression sont déterministes et précises, notamment les fonctions définies par l'utilisateur et les fonctions intégrées. Pour plus d’informations, consultez [Fonctions déterministes et non déterministes](../user-defined-functions/deterministic-and-nondeterministic-functions.md). Les fonctions peuvent être imprécises si la colonne calculée est de type PERSISTED. Pour plus d’informations, consultez [Création d’index sur des colonnes calculées persistantes](#BKMK_persisted) , plus loin dans cette rubrique.  
  
-   Toutes les colonnes auxquelles l'expression fait référence proviennent de la table contenant la colonne calculée.  
  
-   Aucune référence de colonne n'extrait de données provenant de plusieurs lignes. Par exemple, certaines fonctions d’agrégation, telles que SUM ou AVG, dépendent de données provenant de plusieurs lignes et rendraient un paramètre *computed_column_expression* non déterministe.  
  
-   Le paramètre *computed_column_expression* n’a pas d’accès aux données système ni utilisateur.  
  
 Une colonne calculée qui contient une expression CLR (Common Language Runtime) doit être déterministe et marquée comme PERSISTED avant de pouvoir être indexée. Les expressions de type CLR définies par l'utilisateur sont permises dans les définitions de colonnes calculées. Les colonnes calculées de type CLR définies par l'utilisateur peuvent être indexées à condition que le type soit comparable. Pour plus d’informations, consultez [Types CLR définis par l’utilisateur](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
> [!NOTE]  
>  Lorsque vous faites référence aux littéraux de chaîne de type de données de date dans des colonnes calculées indexées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il est recommandé de convertir explicitement le littéral dans le type de date souhaité à l'aide d'un style de format de date déterministe. Pour obtenir la liste des styles de formats de date déterministes, consultez [CAST et CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql). Les expressions qui impliquent une conversion implicite des chaînes de caractères en type de données de date sont considérées comme non déterministes, à moins que le niveau de compatibilité de la base de données ne soit réglé sur 80 ou sur une valeur inférieure. Cela est dû au fait que les résultats dépendent des paramètres [LANGUAGE](/sql/t-sql/statements/set-language-transact-sql) et [DATEFORMAT](/sql/t-sql/statements/set-dateformat-transact-sql) de la session serveur. Par exemple, les résultats de l'expression `CONVERT (datetime, '30 listopad 1996', 113)` dépendent du paramètre LANGUAGE, car la chaîne '`30 listopad 1996`' désigne des mois différents selon la langue. De même, dans l'expression `DATEADD(mm,3,'2000-12-01')`, le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] interprète la chaîne `'2000-12-01'` en se basant sur le paramètre DATEFORMAT.  
>   
>  La conversion implicite de données de caractères non Unicode entre les classements est aussi considérée comme non déterministe, à moins que le niveau de compatibilité soit égal ou inférieur à 80.  
>   
>  Lorsque le niveau de compatibilité de la base de données est égal à 90, vous ne pouvez pas créer d'index sur les colonnes calculées qui contiennent ces expressions. Cependant, les colonnes calculées existantes qui contiennent ces expressions provenant d'une base de données mise à niveau sont gérables. Si vous utilisez des colonnes calculées indexées contenant une chaîne implicite pour les conversions de dates, afin d'éviter tout endommagement éventuel d'index, assurez-vous que les paramètres LANGUAGE et DATEFORMAT sont cohérents dans vos bases de données et applications.  
  
 **Precision Requirements**  
  
 Le paramètre *computed_column_expression* doit être précis. Un paramètre *computed_column_expression* est précis quand une ou plusieurs des conditions suivantes sont remplies :  
  
-   Ce n'est pas une expression composée de données de type `float` ou `real`.  
  
-   L'expression n'utilise pas de données de type `float` ou `real` dans sa définition. Par exemple, dans l'instruction suivante, la colonne `y` est de type `int` et déterministe, mais pas précise.  
  
    ```  
    CREATE TABLE t2 (a int, b int, c int, x float,   
       y AS CASE x   
             WHEN 0 THEN a   
             WHEN 1 THEN b   
             ELSE c   
          END);  
    ```  
  
> [!NOTE]  
>  Toute expression `float` ou `real` est considérée comme non précise et ne peut pas être une clé d'index. Autrement dit, une expression `float` ou `real` peut être utilisée dans une vue indexée mais pas en tant que clé. Ce point s'applique également aux colonnes calculées. Toute fonction, expression ou fonction définie par l'utilisateur est considérée imprécise si elle contient des expressions `float` ou `real`, même logiques (comparaisons).  
  
 La propriété **IsPrecise** de la fonction COLUMNPROPERTY indique si un paramètre *computed_column_expression* est précis ou non.  
  
 **Data Type Requirements**  
  
-   Le *computed_column_expression* défini pour la colonne calculée ne peut pas correspondre à la `text`, `ntext`, ou `image` types de données.  
  
-   Les colonnes calculées dérivées des types de données `image`, `ntext`, `text`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)` et `xml` peuvent être indexées tant que le type de données utilisé dans la colonne calculée lui permet d'être une colonne d'index clés.  
  
-   Les colonnes calculées dérivées des types de données `image`, `ntext` et `text` peuvent être des colonnes (incluses) non-clés dans un index non-cluster tant que le type de données utilisé dans la colonne calculée lui permet d'être une colonne d'index non-clés.  
  
 **SET Option Requirements**  
  
-   L'option de niveau de connexion ANSI_NULLS doit être activée (ON) lors de l'exécution de l'instruction CREATE TABLE ou ALTER TABLE qui définit la colonne calculée. La fonction [OBJECTPROPERTY](/sql/t-sql/functions/objectpropertyex-transact-sql) indique si l’option est activée par le biais de la propriété **IsAnsiNullsOn** .  
  
-   La connexion sur laquelle l'index est créé, ainsi que toutes les connexions tentant d'exécuter des instructions INSERT, UPDATE ou DELETE appelées à modifier des valeurs de l'index, doivent comporter six options SET activées (ON) et une désactivée (OFF). L'optimiseur ignore un index sur une colonne calculée dès qu'une instruction SELECT est exécutée par une connexion qui ne respecte pas ces paramètres d'options.  
  
    -   L'option NUMERIC_ROUNDABORT doit être désactivée (OFF) et les options suivantes doivent être activées (ON) :  
  
    -   ANSI_NULLS  
  
    -   ANSI_PADDING  
  
    -   ANSI_WARNINGS  
  
    -   ARITHABORT  
  
    -   CONCAT_NULL_YIELDS_NULL  
  
    -   QUOTED_IDENTIFIER  
  
     L'affectation de la valeur ON à ANSI_WARNINGS affecte de manière implicite la valeur ON à ARITHABORT, lorsque le niveau de compatibilité de la base de données est d'au moins 90.  
  
##  <a name="BKMK_persisted"></a> Création d’index sur des colonnes calculées persistantes  
 Vous pouvez créer un index sur une colonne calculée définie par une expression déterministe mais non précise si la colonne est marquée comme PERSISTED dans l'instruction CREATE TABLE ou ALTER TABLE. Cela signifie que le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] utilise ces valeurs persistantes lorsqu’il crée un index sur la colonne, et lorsque l’index est référencé dans une requête. Cette option vous permet de créer un index sur une colonne calculée lorsque [!INCLUDE[ssDE](../../../includes/dnprdnshort-md.md)], est déterministe et précise.  
  
## <a name="related-content"></a>Contenu associé  
 [COLUMNPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/columnproperty-transact-sql)  
  
  
