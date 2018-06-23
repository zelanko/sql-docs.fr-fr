---
title: Codage de Types définis par l’utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- validation [CLR integration]
- UDTs [CLR integration], coding
- UserDefined serialization format [CLR integration]
- Point UDT
- Parse method
- null values [CLR integration]
- ToString method
- ValidatePoint method
- attributes [CLR integration]
- coding user-defined types [CLR integration]
- Read method
- Write method
- nullability [CLR integration]
- user-defined types [CLR integration], coding
- Currency UDT
- validating UDT values
- exposing UDT properties [CLR integration]
ms.assetid: 1e5b43b3-4971-45ee-a591-3f535e2ac722
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ab1bc1114d6bfd0ab29a2cc1e16b73466baa1d9a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051065"
---
# <a name="coding-user-defined-types"></a>Codage de types définis par l'utilisateur
  Lorsque vous codez votre définition de type défini par l'utilisateur (UDT, User-Defined Type), vous devez implémenter différentes fonctionnalités, selon que vous implémentez le type défini par l'utilisateur comme classe ou comme structure, et selon les options de format et de sérialisation que vous avez choisies.  
  
 L'exemple de cette section illustre l'implémentation d'un type défini par l'utilisateur `Point` en tant que `struct` (ou `Structure` dans Visual Basic). Le type défini par l'utilisateur `Point` consiste en coordonnées X et Y implémentées comme procédures de propriété.  
  
 Les espaces de noms suivants sont requis lors de la définition d'un type défini par l'utilisateur :  
  
```vb  
Imports System  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
```  
  
```csharp  
using System;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
```  
  
 L'espace de noms `Microsoft.SqlServer.Server` contient les objets requis pour différents attributs de votre type défini par l'utilisateur et l'espace de noms `System.Data.SqlTypes` contient les classes qui représentent les types de données natifs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disponibles à l'assembly. Il se peut bien sûr que le bon fonctionnement de votre assembly requiert des espaces de noms supplémentaires. Le type défini par l'utilisateur `Point` utilise également l'espace de noms `System.Text` pour manipuler des chaînes.  
  
> [!NOTE]  
>  Les objets de base de données Visual C++, comme les types définis par l'utilisateur, compilés avec `/clr:pure` ne sont pas pris en charge pour l'exécution.  
  
## <a name="specifying-attributes"></a>Spécification d'attributs  
 Les attributs déterminent la façon dont la sérialisation est utilisée pour construire la représentation de stockage des types définis par l'utilisateur et pour transmettre des types définis par l'utilisateur par valeur au client.  
  
 L'attribut `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` est requis. L'attribut `Serializable` est facultatif. Vous pouvez également spécifier l'attribut `Microsoft.SqlServer.Server.SqlFacetAttribute` pour fournir des informations à propos du type de retour d'un type défini par l'utilisateur. Pour plus d’informations, consultez [Attributs personnalisés pour les routines CLR](../clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)  
  
### <a name="point-udt-attributes"></a>Attributs du type défini par l'utilisateur Point  
 L'attribut `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` définit le format de stockage pour le type défini par l'utilisateur `Point` à `Native`. `IsByteOrdered` a la valeur `true`, ce qui garantit que les résultats des comparaisons dans SQL Server sont les mêmes que si les comparaisons avaient eu lieu dans le code managé. Le type défini par l'utilisateur implémente l'interface `System.Data.SqlTypes.INullable` pour rendre le type défini par l'utilisateur compatible avec la valeur NULL.  
  
 Le fragment de code suivant montre les attributs pour le type défini par l'utilisateur `Point`.  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True)> _  
  Public Structure Point  
    Implements INullable  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true)]  
public struct Point : INullable  
{  
```  
  
## <a name="implementing-nullability"></a>Implémentation de la possibilité de valeur NULL  
 En plus de spécifier correctement les attributs pour vos assemblys, votre type défini par l'utilisateur doit également prendre en charge la possibilité de valeur Null. Les types définis par l'utilisateur chargés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont compatibles avec la valeur Null, mais pour reconnaître une valeur Null, le type défini par l'utilisateur doit implémenter l'interface `System.Data.SqlTypes.INullable`.  
  
 Vous devez créer une propriété nommée `IsNull`, nécessaire pour déterminer si une valeur est Null dans le code CLR. Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trouve une instance Null d'un type défini par l'utilisateur, celui-ci est rendu persistant à l'aide de méthodes de gestion de valeur Null ordinaires. Le serveur ne perd pas de temps à sérialiser ou désérialiser le type défini par l'utilisateur si cela n'est pas nécessaire et il ne gaspille pas d'espace pour stocker un type défini par l'utilisateur Null. Ce contrôle des valeurs Null est effectué chaque fois qu'un type défini par l'utilisateur est rapporté du CLR, ce qui signifie que l'utilisation de la construction [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL pour vérifier le caractère Null des types définis par l'utilisateur doit toujours fonctionner. La propriété `IsNull` est également utilisée par le serveur pour tester si une instance est Null. Une fois que le serveur a détermine que le type défini par l'utilisateur est Null, il peut utiliser sa gestion Null native.  
  
 La méthode `get()` de `IsNull` ne représente en aucune façon un cas spécial. Si une variable `Point` `@p` est `Null`, `@p.IsNull` est évalué par défaut à « Null », et non à « 1 ». Cela est dû au fait que l'attribut `SqlMethod(OnNullCall)` de la méthode `IsNull get()` a par défaut la valeur « false ». L'objet étant `Null`, lorsque la propriété est demandée, l'objet n'est pas désérialisé, la méthode n'est pas appelée et une valeur par défaut de « Null » est renvoyée.  
  
### <a name="example"></a>Exemple  
 Dans l'exemple suivant, la variable `is_Null` est privée et contient l'état de Null pour l'instance du type défini par l'utilisateur. Votre code doit maintenir une valeur appropriée pour `is_Null`. Le type défini par l'utilisateur doit également avoir une propriété statique nommée `Null` qui retourne une instance de valeur Null du type défini par l'utilisateur. Cela permet au type défini par l'utilisateur de renvoyer une valeur Null si l'instance est en effet Null dans la base de données.  
  
```vb  
Private is_Null As Boolean  
  
Public ReadOnly Property IsNull() As Boolean _  
   Implements INullable.IsNull  
    Get  
        Return (is_Null)  
    End Get  
End Property  
  
Public Shared ReadOnly Property Null() As Point  
    Get  
        Dim pt As New Point  
        pt.is_Null = True  
        Return (pt)  
    End Get  
End Property  
```  
  
```csharp  
private bool is_Null;  
  
public bool IsNull  
{  
    get  
    {  
        return (is_Null);  
    }  
}  
  
public static Point Null  
{  
    get  
    {  
        Point pt = new Point();  
        pt.is_Null = true;  
        return pt;  
    }  
}  
```  
  
### <a name="is-null-vs-isnull"></a>Comparaison de IS NULL et de IsNull  
 Considérez une table qui contient le schéma Points(id int, location Point), où `Point` est un type défini par l'utilisateur CLR, et les requêtes suivantes :  
  
```  
--Query 1  
SELECT ID  
FROM Points  
WHERE NOT (location IS NULL) -- Or, WHERE location IS NOT NULL;  
```  
  
```  
--Query 2:  
SELECT ID  
FROM Points  
WHERE location.IsNull = 0;  
```  
  
 Les deux requêtes retournent les ID de points avec des emplacements non-`Null`. Dans la Requête 1, la gestion de Null normale est utilisée et là aucune désérialisation du type défini par l'utilisateur n'est requise. La Requête 2, en revanche, doit désérialiser chaque objet non-`Null` et appeler le CLR pour obtenir la valeur de la propriété `IsNull`. Il est clair que l'utilisation de `IS NULL` donnera de meilleures performances et il ne devrait jamais y avoir de raison de lire la propriété `IsNull` d'un type défini par l'utilisateur à partir de code [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Par conséquent, quelle est l'utilité de la propriété `IsNull` ? En premier lieu, elle est nécessaire pour déterminer si une valeur est `Null` à partir du code CLR. Ensuite, le serveur a besoin d'une méthode pour tester si une instance est `Null` ; il utilise par conséquent cette propriété. Après avoir déterminé que l'instance est `Null`, il peut utiliser sa gestion Null native pour la gérer.  
  
## <a name="implementing-the-parse-method"></a>Implémentation de la méthode Parse  
 Les méthodes `Parse` et `ToString` permettent d'effectuer des conversions vers et à partir de représentations de chaîne du type défini par l'utilisateur. La méthode `Parse` permet de convertir une chaîne en un type défini par l'utilisateur. Elle doit être déclarée comme `static` (ou `Shared` dans Visual Basic) et accepter un paramètre de type `System.Data.SqlTypes.SqlString`.  
  
 Le code suivant implémente la méthode `Parse` pour le type défini par l'utilisateur `Point`, qui sépare les coordonnées X et Y. La méthode `Parse` a un argument unique de type `System.Data.SqlTypes.SqlString` et suppose que les valeurs X et Y sont fournies en tant que chaîne délimitée par des virgules. L'affectation de la valeur `Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall` à l'attribut `false` empêche la méthode `Parse` d'être appelée à partir d'une instance Null de Point.  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
    return pt;  
}  
```  
  
## <a name="implementing-the-tostring-method"></a>Implémentation de la méthode ToString  
 La méthode `ToString` convertit le type défini par l'utilisateur `Point` en valeur de chaîne. Dans ce cas, la chaîne « NULL » est retournée pour une instance Null du type `Point`. La méthode `ToString` inverse la méthode `Parse` en utilisant un `System.Text.StringBuilder` pour retourner un `System.String` délimité par des virgules qui consiste en valeurs de coordonnées X et Y. Étant donné que **InvokeIfReceiverIsNull** valeur par défaut est false, la vérification pour une instance null de `Point` n’est pas nécessaire.  
  
```vb  
Private _x As Int32  
Private _y As Int32  
  
Public Overrides Function ToString() As String  
    If Me.IsNull Then  
        Return "NULL"  
    Else  
        Dim builder As StringBuilder = New StringBuilder  
        builder.Append(_x)  
        builder.Append(",")  
        builder.Append(_y)  
        Return builder.ToString  
    End If  
End Function  
```  
  
```csharp  
private Int32 _x;  
private Int32 _y;  
  
public override string ToString()  
{  
    if (this.IsNull)  
        return "NULL";  
    else  
    {  
        StringBuilder builder = new StringBuilder();  
        builder.Append(_x);  
        builder.Append(",");  
        builder.Append(_y);  
        return builder.ToString();  
    }  
}  
```  
  
## <a name="exposing-udt-properties"></a>Exposition de propriétés de type défini par l'utilisateur  
 Le type défini par l'utilisateur `Point` expose des coordonnées X et Y implémentées comme propriétés en lecture-écriture publiques de type `System.Int32`.  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _x = Value  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _y = Value  
    End Set  
End Property  
```  
  
```csharp  
public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    set   
    {  
        _x = value;  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        _y = value;  
    }  
}  
```  
  
## <a name="validating-udt-values"></a>Validation de valeurs de type défini par l'utilisateur  
 Lors de l'utilisation de données de type défini par l'utilisateur, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] convertit automatiquement les valeurs binaires en valeurs de type défini par l'utilisateur. Ce processus de conversion nécessite de vérifier que les valeurs sont adaptées au format de sérialisation du type et de s'assurer que la valeur peut être désérialisée correctement. Cela garantit que la valeur peut être convertie au format binaire. Dans le cas des types définis par l'utilisateur ordonnés par octet, cela permet de s'assurer également que la valeur binaire résultante correspond à la valeur binaire d'origine. Cela empêche des valeurs non valides d'être rendues persistantes dans la base de données. Dans certains cas, ce niveau de contrôle peut être inadéquat. Une validation supplémentaire peut être requise lorsque les valeurs de type défini par l'utilisateur doivent se trouver dans un domaine ou une plage attendu(e). Par exemple, un type défini par l'utilisateur qui implémente une date peut exiger que la valeur de jour soit un nombre positif compris dans une certaine plage de valeurs valides.  
  
 La propriété `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName` de l'attribut `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` vous permet de fournir le nom d'une méthode de validation exécutée par le serveur lorsque des données sont assignées à un type défini par l'utilisateur ou converties en un type défini par l'utilisateur. `ValidationMethodName` est également appelé pendant l'exécution de l'utilitaire bcp et des opérations BULK INSERT, DBCC CHECKDB, DBCC CHECKFILEGROUP, DBCC CHECKTABLE, requête distribuée et RPC (Remote Procedure Call) TDS (Tabular Data Stream). La valeur par défaut de `ValidationMethodName` est Null, ce qui indique qu'il n'y a aucune méthode de validation.  
  
### <a name="example"></a>Exemple  
 Le fragment de code suivant illustre la déclaration de la classe `Point`, qui spécifie un `ValidationMethodName` de `ValidatePoint`.  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True, _  
  ValidationMethodName:="ValidatePoint")> _  
  Public Structure Point  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true,   
  ValidationMethodName = "ValidatePoint")]  
public struct Point : INullable  
{  
```  
  
 Si une méthode de validation est spécifiée, elle doit avoir une signature qui ressemble au fragment de code suivant.  
  
```vb  
Private Function ValidationFunction() As Boolean  
    If (validation logic here) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidationFunction()  
{  
    if (validation logic here)  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
 La méthode de validation peut avoir une portée quelconque et doit retourner `true` si la valeur est valide et `false` dans le cas contraire. Si la méthode retourne `false` ou lève une exception, la valeur est traitée comme non valide et une erreur est déclenchée.  
  
 Dans l'exemple ci-dessous, le code autorise uniquement des valeurs de zéro ou plus pour les coordonnées X et Y.  
  
```vb  
Private Function ValidatePoint() As Boolean  
    If (_x >= 0) And (_y >= 0) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidatePoint()  
{  
    if ((_x >= 0) && (_y >= 0))  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
### <a name="validation-method-limitations"></a>Limitations de méthode de validation  
 Le serveur appelle la méthode de validation lorsqu'il effectue des conversions, et non lorsque des données sont insérées en définissant des propriétés individuelles ou à l'aide d'une instruction INSERT [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Vous devez appeler explicitement la méthode de validation à partir d’accesseurs Set de propriété et la `Parse` méthode si vous souhaitez que la méthode de validation à exécuter dans toutes les situations. Cela n'est pas obligatoire, et dans certains cas peut ne pas être souhaitable.  
  
### <a name="parse-validation-example"></a>Exemple de validation Parse  
 Pour vous assurer que le `ValidatePoint` méthode est appelée dans le `Point` (classe), vous devez l’appeler à partir de la `Parse` (méthode) et à partir de la propriété des valeurs de coordonnées procédures qui définissent des X et Y. Le fragment de code suivant montre comment appeler le `ValidatePoint` méthode de validation à partir de la `Parse` (fonction).  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
  
    ' Call ValidatePoint to enforce validation  
    ' for string conversions.  
    If Not pt.ValidatePoint() Then  
        Throw New ArgumentException("Invalid XY coordinate values.")  
    End If  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
  
    // Call ValidatePoint to enforce validation  
    // for string conversions.  
    if (!pt.ValidatePoint())   
        throw new ArgumentException("Invalid XY coordinate values.");  
    return pt;  
}  
```  
  
### <a name="property-validation-example"></a>Exemple de validation de propriété  
 Le fragment de code suivant montre comment appeler le `ValidatePoint` méthode de validation à partir de procédures de propriété définir les coordonnées X et Y.  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _x  
        _x = Value  
        If Not ValidatePoint() Then  
            _x = temp  
            Throw New ArgumentException("Invalid X coordinate value.")  
        End If  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _y  
        _y = Value  
        If Not ValidatePoint() Then  
            _y = temp  
            Throw New ArgumentException("Invalid Y coordinate value.")  
        End If  
    End Set  
End Property  
```  
  
```csharp  
    public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    // Call ValidatePoint to ensure valid range of Point values.  
    set   
    {  
        Int32 temp = _x;  
        _x = value;  
        if (!ValidatePoint())  
        {  
            _x = temp;  
            throw new ArgumentException("Invalid X coordinate value.");  
        }  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        Int32 temp = _y;  
        _y = value;  
        if (!ValidatePoint())  
        {  
            _y = temp;  
            throw new ArgumentException("Invalid Y coordinate value.");  
        }  
    }  
}  
```  
  
## <a name="coding-udt-methods"></a>Codage de méthodes UDT  
 Lors du codage de méthodes UDT, considérez si l'algorithme utilisé pourrait changer avec le temps. Si c'est le cas, vous pourriez envisager de créer une classe séparée pour les méthodes utilisées par votre type défini par l'utilisateur. Si l'algorithme change, vous pouvez recompiler la classe avec le nouveau code et charger l'assembly dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sans affecter le type défini par l'utilisateur. Dans de nombreux cas, les types définis par l'utilisateur peuvent être rechargés à l'aide de l'instruction  [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY, mais cela pourrait provoquer des problèmes avec les données existantes. Par exemple, le `Currency` UDT inclus avec le **AdventureWorks** exemple de base de données utilise un **ConvertCurrency** de fonction pour convertir des valeurs monétaires, implémentée dans une classe distincte. Il est possible que les algorithmes de conversion puissent changer de manière imprévisible dans le futur, ou que de nouvelles fonctionnalités soient requises. Séparer le **ConvertCurrency** fonction à partir de la `Currency` implémentation d’UDT offre davantage de flexibilité lors de la planification des modifications futures.  
  
### <a name="example"></a>Exemple  
 Le `Point` classe contient trois méthodes simples pour calculer la distance : **Distance**, **DistanceFrom** et **DistanceFromXY**. Chacune retourne un `double` qui calcule la distance de `Point` à zéro, la distance d'un point spécifié à `Point` et la distance des coordonnées X et Y spécifiées à `Point`. **Distance** et **DistanceFrom** chaque appel **DistanceFromXY**et montrent comment utiliser différents arguments pour chaque méthode.  
  
```vb  
' Distance from 0 to Point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function Distance() As Double  
    Return DistanceFromXY(0, 0)  
End Function  
  
' Distance from Point to the specified point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFrom(ByVal pFrom As Point) As Double  
    Return DistanceFromXY(pFrom.X, pFrom.Y)  
End Function  
  
' Distance from Point to the specified x and y values.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFromXY(ByVal ix As Int32, ByVal iy As Int32) _  
    As Double  
    Return Math.Sqrt(Math.Pow(ix - _x, 2.0) + Math.Pow(iy - _y, 2.0))  
End Function  
```  
  
```csharp  
// Distance from 0 to Point.  
[SqlMethod(OnNullCall = false)]  
public Double Distance()  
{  
    return DistanceFromXY(0, 0);  
}  
  
// Distance from Point to the specified point.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFrom(Point pFrom)  
{  
    return DistanceFromXY(pFrom.X, pFrom.Y);  
}  
  
// Distance from Point to the specified x and y values.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFromXY(Int32 iX, Int32 iY)  
{  
    return Math.Sqrt(Math.Pow(iX - _x, 2.0) + Math.Pow(iY - _y, 2.0));  
}  
```  
  
### <a name="using-sqlmethod-attributes"></a>Utilisation d'attributs SqlMethod  
 La classe `Microsoft.SqlServer.Server.SqlMethodAttribute` fournit des attributs personnalisés pouvant être utilisés pour marquer des définitions de méthode afin de spécifier le déterminisme, pour le comportement d'appel Null, et de spécifier si une méthode est un mutateur. Les valeurs par défaut de ces propriétés sont assumées et l'attribut personnalisé est utilisé uniquement lorsqu'une valeur non définie par défaut est exigée.  
  
> [!NOTE]  
>  La classe `SqlMethodAttribute` hérite de la classe `SqlFunctionAttribute` ; par conséquent, `SqlMethodAttribute` hérite des champs `FillRowMethodName` et `TableDefinition` de `SqlFunctionAttribute`. Cela implique qu'il est possible d'écrire une méthode table, ce qui n'est pas le cas. La méthode compile et déploie l’assembly, mais une erreur sur le `IEnumerable` retourner le type est déclenché lors de l’exécution avec le message suivant : « méthode, propriété ou champ «\<nom >' dans la classe\<classe >' dans l’assembly '\<assembly >' a un type de retour non valide. »  
  
 Le tableau suivant décrit quelques-unes des propriétés `Microsoft.SqlServer.Server.SqlMethodAttribute` pertinentes qui peuvent être utilisées dans les méthodes UDT et répertorie leurs valeurs par défaut.  
  
 DataAccess  
 Indique si la fonction implique l'accès aux données utilisateur stockées dans l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La valeur par défaut est `DataAccessKind``None`.  
  
 IsDeterministic  
 Indique si la fonction produit les mêmes valeurs de sortie étant donné les mêmes valeurs d'entrée et le même état de la base de données. Valeur par défaut est `false`.  
  
 IsMutator  
 Indique si la méthode provoque une modification d'état dans l'instance de type défini par l'utilisateur. Valeur par défaut est `false`.  
  
 IsPrecise  
 Indique si la fonction implique des calculs imprécis, tels que des opérations à virgule flottante. Valeur par défaut est `false`.  
  
 OnNullCall  
 Indique si la méthode est appelée lorsque des arguments d'entrée de référence nulle sont spécifiés. Valeur par défaut est `true`.  
  
### <a name="example"></a>Exemple  
 La propriété `Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator` vous permet de marquer une méthode qui autorise une modification de l'état d'une instance d'un type défini par l'utilisateur. [!INCLUDE[tsql](../../includes/tsql-md.md)] ne vous permet pas de définir deux propriétés de type défini par l'utilisateur dans la clause SET d'une instruction UPDATE. Toutefois, vous pouvez avoir une méthode marquée comme mutateur qui modifie les deux membres.  
  
> [!NOTE]  
>  Les méthodes mutateurs ne sont pas autorisés dans les requêtes. Elles peuvent être appelées uniquement dans les instructions d'assignation ou les instructions de modification de données. Si une méthode marquée comme mutateur ne retourne pas `void` (ou n'est pas un `Sub` dans Visual Basic), CREATE TYPE échoue avec une erreur.  
  
 L'instruction suivante suppose l'existence d'un type défini par l'utilisateur `Triangles` qui a une méthode `Rotate`. L'instruction UPDATE [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante appelle la méthode `Rotate` :  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 La méthode `Rotate` est décorée avec le paramètre d'attribut `SqlMethod` `IsMutator` à `true` afin que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puisse marquer la méthode comme méthode mutateur. Le code affecte également la valeur `OnNullCall` à `false`, ce qui indique au serveur que la méthode retourne une référence Null (`Nothing` dans Visual Basic) si l'un des paramètres d'entrée est une référence Null.  
  
```vb  
<SqlMethod(IsMutator:=True, OnNullCall:=False)> _  
Public Sub Rotate(ByVal anglex as Double, _  
  ByVal angley as Double, ByVal anglez As Double)   
   RotateX(anglex)  
   RotateY(angley)  
   RotateZ(anglez)  
End Sub  
```  
  
```csharp  
[SqlMethod(IsMutator = true, OnNullCall = false)]  
public void Rotate(double anglex, double angley, double anglez)   
{  
   RotateX(anglex);  
   RotateY(angley);  
   RotateZ(anglez);  
}  
```  
  
## <a name="implementing-a-udt-with-a-user-defined-format"></a>Implémentation d'un type défini par l'utilisateur avec un format défini par l'utilisateur  
 Lors de l'implémentation d'un type défini par l'utilisateur avec un format défini par l'utilisateur, vous devez implémenter des méthodes `Read` et `Write` qui implémentent l'interface Microsoft.SqlServer.Server.IBinarySerialize pour gérer la sérialisation et désérialisation des données UDT. Vous devez également spécifier la propriété `MaxByteSize` de l'attribut `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`.  
  
### <a name="the-currency-udt"></a>Le type défini par l'utilisateur Currency  
 Le type défini par l'utilisateur `Currency` est fourni avec les exemples de CLR qui peuvent être installés avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 Le type défini par l'utilisateur `Currency` prend en charge la gestion des sommes d'argent dans le système monétaire d'une culture particulière. Vous devez définir deux champs : un `string` pour `CultureInfo`, qui spécifie qui a publié la monnaie (en-us, par exemple) et un `decimal` pour `CurrencyValue`, la somme d'argent.  
  
 Bien qu'il ne soit pas utilisé par le serveur pour effectuer des comparaisons, le type défini par l'utilisateur `Currency` implémente l'interface `System.IComparable`, qui expose une méthode unique, `System.IComparable.CompareTo`. Celle-ci est utilisée du côté client dans les situations où il est souhaitable de comparer ou d'ordonner précisément des valeurs monétaire dans des cultures.  
  
 Le code qui s'exécute dans le CLR compare la culture séparément de la valeur monétaire. Pour le code [!INCLUDE[tsql](../../includes/tsql-md.md)], les actions suivantes déterminent la comparaison :  
  
1.  Affectez la valeur « true » à l'attribut `IsByteOrdered`, ce qui indique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qu'il faut utiliser la représentation binaire persistante sur disque à des fins de comparaison.  
  
2.  Utilisez la méthode `Write` pour le type défini par l'utilisateur `Currency` afin de déterminer la façon dont il est rendu persistant sur disque et par conséquent la façon dont les valeurs UDT sont comparées et ordonnées pour les opérations [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
3.  Enregistrez le type défini par l'utilisateur `Currency` à l'aide du format binaire suivant :  
  
    1.  Enregistrez la culture en tant que chaîne encodée UTF-16 pour les octets 0-19, avec un remplissage à droite avec des caractères Null.  
  
    2.  Utilisez les octets 20 et plus pour contenir la valeur décimale de la monnaie.  
  
 L'objectif du remplissage est de s'assurer que la culture est complètement séparée de la valeur monétaire, de sorte que lorsque deux types définis par l'utilisateur sont comparés dans le code [!INCLUDE[tsql](../../includes/tsql-md.md)], les octets de culture soient comparés à des octets de culture et les valeurs d'octets de monnaie soient comparées à des valeurs d'octets de monnaie.  
  
 Pour le code complet pour le `Currency` UDT, suivez les instructions d’installation du CLR des exemples dans [exemples pour le moteur de base de données SQL Server](http://msftengprodsamples.codeplex.com/).  
  
### <a name="currency-attributes"></a>Attributs Currency  
 Le type défini par l'utilisateur `Currency` est défini avec les attributs suivants :  
  
```vb  
<Serializable(), Microsoft.SqlServer.Server.SqlUserDefinedType( _  
    Microsoft.SqlServer.Server.Format.UserDefined, _  
    IsByteOrdered:=True, MaxByteSize:=32), _  
    CLSCompliant(False)> _  
Public Structure Currency  
Implements INullable, IComparable, _  
Microsoft.SqlServer.Server.IBinarySerialize  
```  
  
```csharp  
[Serializable]  
[SqlUserDefinedType(Format.UserDefined,   
    IsByteOrdered = true, MaxByteSize = 32)]  
    [CLSCompliant(false)]  
    public struct Currency : INullable, IComparable, IBinarySerialize  
    {  
```  
  
## <a name="creating-read-and-write-methods-with-ibinaryserialize"></a>Création de méthodes Read et Write avec IBinarySerialize  
 Lorsque vous choisissez le format de sérialisation `UserDefined`, vous devez également implémenter l'interface `IBinarySerialize` et créer vos propres méthodes `Read` et `Write`. Les procédures suivantes du type défini par l'utilisateur `Currency` utilisent `System.IO.BinaryReader` et `System.IO.BinaryWriter` pour lire et écrire dans le type défini par l'utilisateur.  
  
```vb  
' IBinarySerialize methods  
' The binary layout is as follow:  
'    Bytes 0 - 19: Culture name, padded to the right with null  
'    characters, UTF-16 encoded  
'    Bytes 20+: Decimal value of money  
' If the culture name is empty, the currency is null.  
Public Sub Write(ByVal w As System.IO.BinaryWriter) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Write  
    If Me.IsNull Then  
        w.Write(nullMarker)  
        w.Write(System.Convert.ToDecimal(0))  
        Return  
    End If  
  
    If cultureName.Length > cultureNameMaxSize Then  
        Throw New ApplicationException(String.Format(CultureInfo.CurrentUICulture, _  
           "{0} is an invalid culture name for currency as it is too long.", cultureNameMaxSize))  
    End If  
  
    Dim paddedName As String = cultureName.PadRight(cultureNameMaxSize, CChar(vbNullChar))  
  
    For i As Integer = 0 To cultureNameMaxSize - 1  
        w.Write(paddedName(i))  
    Next i  
  
    ' Normalize decimal value to two places  
    currencyVal = Decimal.Floor(currencyVal * 100) / 100  
    w.Write(currencyVal)  
End Sub  
  
Public Sub Read(ByVal r As System.IO.BinaryReader) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Read  
    Dim name As Char() = r.ReadChars(cultureNameMaxSize)  
    Dim stringEnd As Integer = Array.IndexOf(name, CChar(vbNullChar))  
  
    If stringEnd = 0 Then  
        cultureName = Nothing  
        Return  
    End If  
  
    cultureName = New String(name, 0, stringEnd)  
    currencyVal = r.ReadDecimal()  
End Sub  
  
```  
  
```csharp  
// IBinarySerialize methods  
// The binary layout is as follow:  
//    Bytes 0 - 19:Culture name, padded to the right   
//    with null characters, UTF-16 encoded  
//    Bytes 20+:Decimal value of money  
// If the culture name is empty, the currency is null.  
public void Write(System.IO.BinaryWriter w)  
{  
    if (this.IsNull)  
    {  
        w.Write(nullMarker);  
        w.Write((decimal)0);  
        return;  
    }  
  
    if (cultureName.Length > cultureNameMaxSize)  
    {  
        throw new ApplicationException(string.Format(  
            CultureInfo.InvariantCulture,   
            "{0} is an invalid culture name for currency as it is too long.",   
            cultureNameMaxSize));  
    }  
  
    String paddedName = cultureName.PadRight(cultureNameMaxSize, '\0');  
    for (int i = 0; i < cultureNameMaxSize; i++)  
    {  
        w.Write(paddedName[i]);  
    }  
  
    // Normalize decimal value to two places  
    currencyValue = Decimal.Floor(currencyValue * 100) / 100;  
    w.Write(currencyValue);  
}  
public void Read(System.IO.BinaryReader r)  
{  
    char[] name = r.ReadChars(cultureNameMaxSize);  
    int stringEnd = Array.IndexOf(name, '\0');  
  
    if (stringEnd == 0)  
    {  
        cultureName = null;  
        return;  
    }  
  
    cultureName = new String(name, 0, stringEnd);  
    currencyValue = r.ReadDecimal();  
}  
```  
  
 Pour le code complet pour le `Currency` UDT, consultez [exemples pour le moteur de base de données SQL Server](http://msftengprodsamples.codeplex.com/).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un Type défini par l’utilisateur](creating-user-defined-types.md)  
  
  