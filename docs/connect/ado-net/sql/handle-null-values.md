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
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 2bcd54ab83429b1f7961480210c12eb546a2aa70
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896734"
---
# <a name="handling-null-values"></a>Traitement des valeurs Null

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Une valeur Null dans une base de données relationnelle est utilisée lorsque la valeur d’une colonne est inconnue ou manquante. Une valeur Null n’est ni une chaîne vide (pour les types de données caractère ou DateHeure), ni une valeur zéro (pour les types de données numériques). La spécification SQL-92 ANSI indique qu’une valeur Null doit être la même pour tous les types de données, de sorte que toutes les valeurs Null sont gérées de manière cohérente. L’espace de noms <xref:System.Data.SqlTypes> fournit une sémantique Null en implémentant l’interface <xref:System.Data.SqlTypes.INullable>. Chacun des types de données de <xref:System.Data.SqlTypes> a sa propre propriété `IsNull` et une valeur `Null` qui peut être assignée à une instance de ce type de données.  
  
> [!NOTE]
>  La version .NET Framework 2.0 et la version .NET Core 1.0 ont introduit le support des types Nullable, qui permettent aux programmeurs d’étendre un type valeur pour représenter toutes les valeurs du type sous-jacent. Ces types Nullable CLR représentent une instance de la structure <xref:System.Nullable>. Cette fonctionnalité est particulièrement utile lorsque les types valeur sont boxed et unboxed, ce qui offre une meilleure compatibilité avec les types d’objets. Les types Nullable CLR ne sont pas destinés au stockage des valeurs Null de base de données, car une valeur Null SQL ANSI ne se comporte pas de la même façon qu’une référence `null` (ou `Nothing` dans Visual Basic). Pour travailler avec les valeurs Null SQL ANSI de la base de données, utilisez les valeurs Null <xref:System.Data.SqlTypes> au lieu de <xref:System.Nullable>. Pour plus d’informations sur l’utilisation des types Nullables CLR dans C#, consultez [Types Nullables](https://docs.microsoft.com/dotnet/csharp/programming-guide/nullable-types/) et pour C#, consultez [Utilisation des types Nullables](https://docs.microsoft.com/dotnet/csharp/programming-guide/nullable-types/using-nullable-types/).  
  
## <a name="nulls-and-three-valued-logic"></a>Valeurs Null et logique ternaire  
L’autorisation de valeurs Null dans les définitions de colonne introduit une logique ternaire dans votre application. Une comparaison peut évaluer entre une et trois conditions :  
  
- True  
  
- False  
  
- Unknown  
  
Étant donné que la valeur Null est considérée comme inconnue, deux valeurs Null comparées l’une avec l’autre ne sont pas considérées comme égales. Dans les expressions utilisant des opérateurs arithmétiques, si l’un des opérandes a la valeur Null, le résultat est également Null.  
  
## <a name="nulls-and-sqlboolean"></a>Valeurs Null et SqlBoolean  
La comparaison entre tout <xref:System.Data.SqlTypes> retourne une <xref:System.Data.SqlTypes.SqlBoolean>. La fonction `IsNull` pour chaque `SqlType` retourne un <xref:System.Data.SqlTypes.SqlBoolean> et peut être utilisée pour vérifier les valeurs Null. Les tables de vérité suivantes montrent comment les opérateurs AND, OR et NOT fonctionnent dans la présence d’une valeur Null. (T = true (vrai), F = false (faux) et U = unknown (inconnu) ou Null.)  
  
![Table de vérité](../media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Comprendre l’option ANSI_NULLS  
<xref:System.Data.SqlTypes> fournit la même sémantique que lorsque l’option ANSI_NULLS est activée dans SQL Server. Tous les opérateurs arithmétiques (+, -, *, /, %), les opérateurs de bits (~, &, &#124;) et la plupart des fonctions retournent une valeur null si l’un des opérandes ou des arguments est une valeur null, excepté pour la propriété `IsNull`.  
  
La norme ANSI SQL-92 ne prend pas en charge *columnName* = NULL dans une clause WHERE. Dans SQL Server, l’option ANSI_NULLS contrôle à la fois la possibilité de valeur Null par défaut dans la base de données et l’évaluation des comparaisons par rapport aux valeurs Null. Si ANSI_NULLS est activé (valeur par défaut), l’opérateur IS NULL doit être utilisé dans les expressions lors du test des valeurs Null. Par exemple, la comparaison suivante donne toujours un résultat inconnu quand ANSI_NULLS est activé :  
  
```console
colname > NULL  
```  
  
La comparaison avec une variable contenant une valeur Null génère également Inconnu :  
  
```console
colname > @MyVariable  
```  
  
Utilisez le prédicat IS NULL ou IS NOT NULL pour tester si une valeur est NULL. Ceci peut compliquer encore la clause WHERE. Par exemple, la colonne TerritoryID de la table AdventureWorks Customer autorise les valeurs Null. Si une instruction SELECT doit rechercher des valeurs NULL en plus des autres, elle doit inclure un prédicat IS NULL :  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
Si vous désactivez ANSI_NULLS dans SQL Server, vous pouvez créer des expressions qui utilisent l’opérateur d’égalité pour effectuer une comparaison avec la valeur Null. Toutefois, vous ne pouvez pas empêcher des connexions différentes de définir des options Null pour cette connexion. L’utilisation de IS NULL pour tester les valeurs Null fonctionne toujours, quels que soient les paramètres de ANSI_NULLS pour une connexion.  
  
La désactivation de ANSI_NULLS n’est pas prise en charge dans un `DataSet`, qui suit toujours la norme ANSI SQL-92 pour la gestion des valeurs Null dans <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Affectation des valeurs Null  
Les valeurs Null sont spéciales et leur sémantique de stockage et d’affectation diffère selon les systèmes de stockage et systèmes de type. Un `Dataset` est conçu pour être utilisé avec différents systèmes de type et de stockage.  
  
Cette section décrit la sémantique Null pour l’affectation de valeurs Null à un <xref:System.Data.DataColumn> dans un <xref:System.Data.DataRow> sur les différents systèmes de type.  
  
`DBNull.Value`  
Cette affectation est valide pour un `DataColumn` de n’importe quel type. Si le type implémente `INullable`, `DBNull.Value` est forcé dans la valeur Null fortement typée appropriée.  
  
`SqlType.Null`  
Tous les types de données <xref:System.Data.SqlTypes> implémentent `INullable`. Si la valeur Null fortement typée peut être convertie dans le type de données de la colonne à l’aide d’opérateurs de forçage de type implicite, l’affectation doit y être soumise. Sinon, une exception de forçage de type non valide est levée.  
  
`null`  
Si « Null » est une valeur autorisée pour le type de données `DataColumn` donné, il est converti en `DbNull.Value` approprié ou `Null` associé au type de `INullable` (`SqlType.Null`)  
  
`derivedUdt.Null`  
Pour les colonnes UDT, les valeurs Null sont toujours stockées en fonction du type associé à `DataColumn`. Prenons le cas d’un UDT associé à un `DataColumn` qui n’implémente pas `INullable` alors que sa sous-classe le fait. Dans ce cas, si une valeur Null fortement typée associée à la classe dérivée est attribuée, elle est stockée en tant que `DbNull.Value` non typée, car le stockage Null est toujours cohérent avec le type de données de DataColumn.  
  
> [!NOTE]
>  La structure `Nullable<T>` ou <xref:System.Nullable> n’est pas prise en charge actuellement dans le `DataSet`.  
  
### <a name="multiple-column-row-assignment"></a>Affectation de plusieurs colonnes (lignes)  
`DataTable.Add`, `DataTable.LoadDataRow` ou d’autres API acceptant une <xref:System.Data.DataRow.ItemArray%2A> mappée à une ligne, mappez « Null » à la valeur par défaut de DataColumn. Si un objet du tableau contient `DbNull.Value` ou son équivalent fortement typé, les mêmes règles que celles décrites ci-dessus sont appliquées.  
  
En outre, les règles suivantes s’appliquent à une instance des affectations Null `DataRow.["columnName"]` :  
  
- La valeur par défaut *default* est `DbNull.Value` pour tout, à l’exception des colonnes null fortement typées contenant la valeur null fortement typée appropriée.  
  
- Les valeurs Null ne sont jamais écrites lors de la sérialisation vers des fichiers XML (comme dans « xsi:nil »).  
  
- Toutes les valeurs non Null, y compris les valeurs par défaut, sont toujours écrites lors de la sérialisation en XML. Contrairement à la sémantique XSD/XML, où une valeur Null (xsi:nil) est explicite et que la valeur par défaut est implicite (si elle n’est pas présente dans XML, un analyseur de validation peut l’obtenir à partir d’un schéma XSD associé). Le contraire est vrai pour une `DataTable` : une valeur Null est implicite et la valeur par défaut est explicite.  
  
- La Valeur Null est attribuée à toutes les valeurs de colonne manquantes pour les lignes lues à partir de l’entrée XML. La valeur par défaut de DataColumn est attribuée aux lignes créées à l’aide de <xref:System.Data.DataTable.NewRow%2A> ou à des méthodes similaires.  
  
- La méthode <xref:System.Data.DataRow.IsNull%2A> renvoie `true` pour `DbNull.Value` et `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Affectation des valeurs Null  
La valeur par défaut pour toute instance <xref:System.Data.SqlTypes> est Null.  
  
Les valeurs Null dans <xref:System.Data.SqlTypes> sont spécifiques au type et ne peuvent pas être représentées par une valeur unique, telle que `DbNull`. Utilisez la propriété `IsNull` pour vérifier les valeurs Null.  
  
Les valeurs Null peuvent être attribuées à un <xref:System.Data.DataColumn> comme indiqué dans l’exemple de code suivant. Vous pouvez attribuer directement des valeurs Null à des variables `SqlTypes` sans déclencher d’exception.  
  
### <a name="example"></a>Exemple  
L’exemple de code suivant crée une <xref:System.Data.DataTable> avec deux colonnes définies comme <xref:System.Data.SqlTypes.SqlInt32> et <xref:System.Data.SqlTypes.SqlString>. Le code ajoute une ligne de valeurs connues, une ligne de valeurs Null, puis itère au sein de la <xref:System.Data.DataTable>, en attribuant les valeurs aux variables et en affichant le résultat dans la fenêtre de console.  
  
[!code-csharp[DataWorks SqlInt32_IsNull#1](~/../sqlclient/doc/samples/SqlInt32_IsNull.cs#1)]
  
Cet exemple produit les résultats suivants :  
  
```console
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Comparaison de valeurs Null avec les types SqlTypes et CLR  
Lors de la comparaison de valeurs Null, il est important de comprendre la différence entre la façon dont la méthode `Equals` évalue les valeurs Null dans les <xref:System.Data.SqlTypes> par rapport à la façon dont elle fonctionne avec les types CLR. Toutes les méthodes <xref:System.Data.SqlTypes>`Equals` utilisent la sémantique de base de données pour évaluer les valeurs Null : si une des valeurs ou les deux sont Null, la comparaison génère la valeur Null. En revanche, l’utilisation de la méthode `Equals` CLR sur deux <xref:System.Data.SqlTypes> produira la valeur true si les deux sont Null. Cela reflète la différence entre l’utilisation d’une méthode d’instance telle que la méthode `String.Equals` CLR et l’utilisation de la méthode statique/partagée, `SqlString.Equals`.  
  
L’exemple suivant illustre la différence de résultats entre la méthode `SqlString.Equals` et la méthode `String.Equals` quand chacun reçoit une paire de valeurs Null, puis une paire de chaînes vides.  
  
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
