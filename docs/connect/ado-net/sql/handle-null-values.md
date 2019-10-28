---
title: Traitement des valeurs Null
description: Montre comment utiliser des valeurs GUID et uniqueidentifier dans SQL Server et .NET.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 6ae2bc8d816dd2bc32572447483dacd76dd967f0
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452182"
---
# <a name="handling-null-values"></a>Traitement des valeurs Null

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Une valeur null dans une base de données relationnelle est utilisée lorsque la valeur d’une colonne est inconnue ou manquante. Une valeur NULL n’est ni une chaîne vide (pour les types de données caractère ou DateTime), ni une valeur zéro (pour les types de données numériques). La spécification SQL-92 ANSI indique qu’une valeur null doit être la même pour tous les types de données, de sorte que toutes les valeurs NULL sont gérées de manière cohérente. L’espace de noms <xref:System.Data.SqlTypes> fournit une sémantique null en implémentant l’interface <xref:System.Data.SqlTypes.INullable>. Chacun des types de données de <xref:System.Data.SqlTypes> a sa propre propriété `IsNull` et une valeur `Null` qui peut être assignée à une instance de ce type de données.  
  
> [!NOTE]
>  Le .NET Framework version 2,0 et la version .NET Core 1,0 ont introduit la prise en charge des types Nullable, qui permettent aux programmeurs d’étendre un type valeur pour représenter toutes les valeurs du type sous-jacent. Ces types Nullable CLR représentent une instance de la structure <xref:System.Nullable>. Cette fonctionnalité est particulièrement utile lorsque les types valeur sont boxed et unboxed, ce qui offre une meilleure compatibilité avec les types d’objets. Les types Nullable CLR ne sont pas destinés au stockage des valeurs null de base de données, car une valeur null SQL ANSI ne se comporte pas de la même façon qu’une référence `null` (ou `Nothing` dans Visual Basic). Pour travailler avec les valeurs NULL SQL ANSI de la base de données, utilisez <xref:System.Data.SqlTypes> valeurs NULL au lieu de <xref:System.Nullable>. Pour plus d’informations sur l’utilisation des types CLR C# Nullable dans, consultez [types Nullable](https://docs.microsoft.com/dotnet/csharp/programming-guide/nullable-types/), et pour voir utilisation de C# [types Nullable](https://docs.microsoft.com/dotnet/csharp/programming-guide/nullable-types/using-nullable-types/).  
  
## <a name="nulls-and-three-valued-logic"></a>Valeurs NULL et logique à trois valeurs  
L’autorisation de valeurs NULL dans les définitions de colonne introduit une logique à trois valeurs dans votre application. Une comparaison peut correspondre à l’une des trois conditions suivantes :  
  
- True  
  
- False  
  
- Unknown  
  
Étant donné que la valeur null est considérée comme inconnue, deux valeurs NULL sont comparées les unes aux autres ne sont pas considérées comme égales. Dans les expressions utilisant des opérateurs arithmétiques, si l’un des opérandes a la valeur null, le résultat est également null.  
  
## <a name="nulls-and-sqlboolean"></a>Valeurs NULL et SqlBoolean  
La comparaison entre tout <xref:System.Data.SqlTypes> retourne une <xref:System.Data.SqlTypes.SqlBoolean>. La fonction `IsNull` pour chaque `SqlType` retourne un <xref:System.Data.SqlTypes.SqlBoolean> et peut être utilisée pour vérifier les valeurs NULL. Les tables de vérité suivantes montrent comment les opérateurs AND, OR et NOT fonctionnent dans la présence d’une valeur null. (T = true, F = false et U = Unknown, ou null.)  
  
![Table de vérité](../media/truthtable-bpuedev11.gif "|::ref1::|")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Fonctionnement de l’option ANSI_NULLS  
<xref:System.Data.SqlTypes> fournit la même sémantique que lorsque l’option ANSI_NULLS est activée (on) dans SQL Server. Tous les opérateurs arithmétiques (+, -, *, /, %), les opérateurs de bits (~, &, &#124;) et la plupart des fonctions retournent une valeur null si l’un des opérandes ou des arguments est une valeur null, excepté pour la propriété `IsNull`.  
  
La norme ANSI SQL-92 ne prend pas en charge *columnName* = NULL dans une clause WHERE. Dans SQL Server, l’option ANSI_NULLS contrôle à la fois la possibilité de valeur NULL par défaut dans la base de données et l’évaluation des comparaisons par rapport aux valeurs NULL. Si ANSI_NULLS est activé (valeur par défaut), l’opérateur IS NULL doit être utilisé dans les expressions lors du test des valeurs NULL. Par exemple, la comparaison suivante donne toujours un résultat inconnu quand ANSI_NULLS est activé :  
  
```console
colname > NULL  
```  
  
La comparaison avec une variable contenant une valeur null génère également Unknown :  
  
```console
colname > @MyVariable  
```  
  
Utilisez le prédicat IS NULL ou IS NOT NULL pour tester si une valeur est NULL. Ceci peut compliquer encore la clause WHERE. Par exemple, la colonne TerritoryID de la table AdventureWorks Customer autorise les valeurs NULL. Si une instruction SELECT doit rechercher des valeurs NULL en plus des autres, elle doit inclure un prédicat IS NULL :  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
Si vous désactivez ANSI_NULLS dans SQL Server, vous pouvez créer des expressions qui utilisent l’opérateur d’égalité pour effectuer une comparaison avec la valeur null. Toutefois, vous ne pouvez pas empêcher des connexions différentes de définir des options null pour cette connexion. L’utilisation de IS NULL pour tester les valeurs Null fonctionne toujours, quels que soient les paramètres ANSI_NULLS pour une connexion.  
  
La définition de ANSI_NULLS OFF n’est pas prise en charge dans un `DataSet`, qui suit toujours la norme ANSI SQL-92 pour la gestion des valeurs NULL dans <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Assigner des valeurs null  
Les valeurs NULL sont spéciales et leur sémantique de stockage et d’affectation diffère selon les systèmes de stockage et systèmes de type. Un `Dataset` est conçu pour être utilisé avec différents systèmes de type et de stockage.  
  
Cette section décrit la sémantique null pour l’affectation de valeurs NULL à un <xref:System.Data.DataColumn> dans un <xref:System.Data.DataRow> sur les différents systèmes de type.  
  
`DBNull.Value`  
Cette assignation est valide pour un `DataColumn` de n’importe quel type. Si le type implémente `INullable`, `DBNull.Value` est forcé dans la valeur null fortement typée appropriée.  
  
`SqlType.Null`  
Tous les types de données <xref:System.Data.SqlTypes> implémentent `INullable`. Si la valeur null fortement typée peut être convertie dans le type de données de la colonne à l’aide d’opérateurs de conversion implicite, l’assignation doit passer par. Sinon, une exception de cast non valide est levée.  
  
`null`  
Si « null » est une valeur autorisée pour le type de données `DataColumn` donné, il est converti en `DbNull.Value` approprié ou `Null` associé au type de `INullable` (`SqlType.Null`)  
  
`derivedUdt.Null`  
Pour les colonnes UDT, les valeurs NULL sont toujours stockées en fonction du type associé à l' `DataColumn`. Prenons le cas d’un UDT associé à un `DataColumn` qui n’implémente pas `INullable` alors que sa sous-classe. Dans ce cas, si une valeur null fortement typée associée à la classe dérivée est assignée, elle est stockée en tant que `DbNull.Value` non typé, car le stockage NULL est toujours cohérent avec le type de données de DataColumn.  
  
> [!NOTE]
>  La structure `Nullable<T>` ou <xref:System.Nullable> n’est pas prise en charge actuellement dans le `DataSet`.  
  
### <a name="multiple-column-row-assignment"></a>Attribution de plusieurs colonnes (lignes)  
`DataTable.Add`, `DataTable.LoadDataRow` ou d’autres API qui acceptent un <xref:System.Data.DataRow.ItemArray%2A> qui est mappé à une ligne, mappez la valeur null à la valeur par défaut de DataColumn. Si un objet du tableau contient `DbNull.Value` ou son équivalent fortement typé, les mêmes règles que celles décrites ci-dessus sont appliquées.  
  
En outre, les règles suivantes s’appliquent à une instance de `DataRow.["columnName"]` assignations NULL :  
  
- La valeur par défaut *default* est `DbNull.Value` pour tout, à l’exception des colonnes null fortement typées contenant la valeur null fortement typée appropriée.  
  
- Les valeurs NULL ne sont jamais écrites lors de la sérialisation vers des fichiers XML (comme dans « xsi : Nil »).  
  
- Toutes les valeurs non null, y compris les valeurs par défaut, sont toujours écrites lors de la sérialisation en XML. Contrairement à la sémantique XSD/XML, où une valeur null (xsi : Nil) est explicite et que la valeur par défaut est implicite (si elle n’est pas présente dans XML, un analyseur de validation peut l’obtenir à partir d’un schéma XSD associé). L’inverse est vrai pour un `DataTable` : une valeur null est implicite et la valeur par défaut est Explicit.  
  
- La valeur NULL est affectée à toutes les valeurs de colonne manquantes pour les lignes lues à partir de l’entrée XML. La valeur par défaut de DataColumn est assignée aux lignes créées à l’aide de <xref:System.Data.DataTable.NewRow%2A> ou à des méthodes similaires.  
  
- La méthode <xref:System.Data.DataRow.IsNull%2A> retourne `true` pour `DbNull.Value` et `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Assigner des valeurs null  
La valeur par défaut de tout <xref:System.Data.SqlTypes> instance est null.  
  
Les valeurs NULL dans <xref:System.Data.SqlTypes> sont spécifiques au type et ne peuvent pas être représentées par une valeur unique, telle que `DbNull`. Utilisez la propriété `IsNull` pour vérifier les valeurs NULL.  
  
Les valeurs NULL peuvent être assignées à un <xref:System.Data.DataColumn> comme indiqué dans l’exemple de code suivant. Vous pouvez assigner directement des valeurs NULL à `SqlTypes` variables sans déclencher d’exception.  
  
### <a name="example"></a>Exemple  
L’exemple de code suivant crée une <xref:System.Data.DataTable> avec deux colonnes définies comme <xref:System.Data.SqlTypes.SqlInt32> et <xref:System.Data.SqlTypes.SqlString>. Le code ajoute une ligne de valeurs connues, une ligne de valeurs NULL, puis itère au sein de la <xref:System.Data.DataTable>, en assignant les valeurs aux variables et en affichant la sortie dans la fenêtre de console.  
  
[!code-csharp[DataWorks SqlInt32_IsNull#1](~/../sqlclient/doc/samples/SqlInt32_IsNull.cs#1)]
  
Cet exemple affiche les résultats suivants :  
  
```console
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Comparaison de valeurs NULL avec les types SqlTypes et CLR  
Lors de la comparaison de valeurs NULL, il est important de comprendre la différence entre la façon dont la méthode `Equals` évalue les valeurs NULL dans les <xref:System.Data.SqlTypes> par rapport à la façon dont elle fonctionne avec les types CLR. Toutes les méthodes de `Equals` <xref:System.Data.SqlTypes> utilisent la sémantique de base de données pour évaluer les valeurs NULL : si une des valeurs ou les deux sont NULL, la comparaison génère la valeur null. En revanche, l’utilisation de la méthode `Equals` CLR sur deux <xref:System.Data.SqlTypes> produira la valeur true si les deux sont null. Cela reflète la différence entre l’utilisation d’une méthode d’instance telle que la méthode de `String.Equals` CLR et l’utilisation de la méthode statique/partagée, `SqlString.Equals`.  
  
L’exemple suivant illustre la différence de résultats entre la méthode `SqlString.Equals` et la méthode `String.Equals` quand chacun reçoit une paire de valeurs NULL, puis une paire de chaînes vides.  
  
[!code-csharp[DataWorks SqlString_Equals#1](~/../sqlclient/doc/samples/SqlString_Equals.cs#1)]
  
Ce code produit la sortie suivante :  
  
```console
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True   
```  
  
## <a name="next-steps"></a>Étapes suivantes
- [Types de données SQL Server et ADO.NET](sql-server-data-types.md)
