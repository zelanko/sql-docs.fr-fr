---
title: Codage des types définis par l’utilisateur (fr) Microsoft Docs
description: Cet exemple montre comment implémenter un UDT à utiliser dans une base de données SQL Server. Il met en œuvre l’UDT comme structure.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a9d51cc0c33c8b656df176baa606a88a542ca4bc
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486952"
---
# <a name="creating-user-defined-types---coding"></a>Création de types définis par l’utilisateur - Codage
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Lorsque vous codez votre définition de type défini par l'utilisateur (UDT, User-Defined Type), vous devez implémenter différentes fonctionnalités, selon que vous implémentez le type défini par l'utilisateur comme classe ou comme structure, et selon les options de format et de sérialisation que vous avez choisies.  
  
 L’exemple de cette section illustre la mise en œuvre d’un **point** UDT comme **struct** (ou **structure** dans la base visuelle). Le **Point** UDT se compose de coordonnées X et Y mises en œuvre comme procédures de propriété.  
  
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
  
 L’espace de nom **Microsoft.SqlServer.Server** contient les objets requis pour divers attributs de votre UDT, et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le **system.Data.SqlTypes** namespace contient les classes qui représentent les types de données indigènes disponibles pour l’assemblage. Il se peut bien sûr que le bon fonctionnement de votre assembly requiert des espaces de noms supplémentaires. Le **Point** UDT utilise également l’espace nom **System.Text** pour travailler avec les cordes.  
  
> [!NOTE]  
>  Les objets de base de données Visual CMD, tels que les UDT, compilés avec **/clr:pure** ne sont pas pris en charge pour l’exécution.  
  
## <a name="specifying-attributes"></a>Spécification d'attributs  
 Les attributs déterminent la façon dont la sérialisation est utilisée pour construire la représentation de stockage des types définis par l'utilisateur et pour transmettre des types définis par l'utilisateur par valeur au client.  
  
 Le **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** est nécessaire. **L’attribut Serializable** est facultatif. Vous pouvez également spécifier le **Microsoft.SqlServer.Server.SqlFacetAttribute** pour fournir des informations sur le type de retour d’un UDT. Pour plus d’informations, consultez [Attributs personnalisés pour les routines CLR](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)  
  
### <a name="point-udt-attributes"></a>Attributs du type défini par l'utilisateur Point  
 Le **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** définit le format de stockage pour le **Point** UDT à **Native**. **IsByteOrdered** est **true**concrétisé, ce qui garantit que les résultats des comparaisons sont les mêmes dans SQL Server que si la même comparaison avait eu lieu dans le code géré. L’UDT implémente **l’interface System.Data.SqlTypes.INullable** pour rendre l’UDT nul au courant.  
  
 Le fragment de code suivant montre les attributs du **Point** UDT.  
  
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
 En plus de spécifier correctement les attributs pour vos assemblys, votre type défini par l'utilisateur doit également prendre en charge la possibilité de valeur Null. Les UDT [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chargés sont nuls, mais pour que l’UDT reconnaisse une valeur nulle, l’UDT doit implémenter **l’interface System.Data.SqlTypes.INullable.**  
  
 Vous devez créer une propriété nommée **IsNull**, qui est nécessaire pour déterminer si une valeur est nulle à partir de l’intérieur du code CLR. Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trouve une instance Null d'un type défini par l'utilisateur, celui-ci est rendu persistant à l'aide de méthodes de gestion de valeur Null ordinaires. Le serveur ne perd pas de temps à sérialiser ou désérialiser le type défini par l'utilisateur si cela n'est pas nécessaire et il ne gaspille pas d'espace pour stocker un type défini par l'utilisateur Null. Ce contrôle des valeurs Null est effectué chaque fois qu'un type défini par l'utilisateur est rapporté du CLR, ce qui signifie que l'utilisation de la construction [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL pour vérifier le caractère Null des types définis par l'utilisateur doit toujours fonctionner. La propriété **IsNull** est également utilisée par le serveur pour vérifier si une instance est nulle. Une fois que le serveur a détermine que le type défini par l'utilisateur est Null, il peut utiliser sa gestion Null native.  
  
 La méthode **get()** **d’IsNull** n’est pas spéciale-cased en aucune façon. Si un ** \@** **point** variable p est **Null**, ** \@p.IsNull** évaluera, par défaut, "NULL", et non "1". C’est parce que **l’attribut SqlMethod (OnNullCall)** de la méthode **IsNull obtenir ()** par défaut à faux. Étant donné que l’objet est **nul,** lorsque la propriété est demandée l’objet n’est pas déséialisé, la méthode n’est pas appelée, et une valeur par défaut de "NULL" est retournée.  
  
### <a name="example"></a>Exemple  
 Dans l'exemple suivant, la variable `is_Null` est privée et contient l'état de Null pour l'instance du type défini par l'utilisateur. Votre code doit maintenir une valeur appropriée pour `is_Null`. L’UDT doit également avoir une propriété statique nommée **Null** qui renvoie une instance de valeur nulle de l’UDT. Cela permet au type défini par l'utilisateur de renvoyer une valeur Null si l'instance est en effet Null dans la base de données.  
  
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
 Considérez un tableau qui contient les points schéma (id int, point d’emplacement), où **Point** est un CLR UDT, et les requêtes suivantes:  
  
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
  
 Les deux requêtes renvoient les DIU de points avec des emplacements non**nuls.** Dans la Requête 1, la gestion de Null normale est utilisée et là aucune désérialisation du type défini par l'utilisateur n'est requise. La requête 2, d’autre part, doit déséialiser chaque objet non**nul** et appeler dans le CLR pour obtenir la valeur de la propriété **IsNull.** De toute évidence, l’utilisation **de IS NULL** affichera de meilleures performances et il ne devrait jamais y avoir de raison de lire la propriété **IsNull** d’un UDT à partir du [!INCLUDE[tsql](../../includes/tsql-md.md)] code.  
  
 Alors, quelle est l’utilisation de la propriété **IsNull?** Tout d’abord, il est nécessaire de déterminer si une valeur est **nulle** à partir de l’intérieur du code CLR. Deuxièmement, le serveur a besoin d’un moyen de tester si une instance est **Null**, de sorte que cette propriété est utilisée par le serveur. Après qu’il détermine qu’il est **Null**, alors il peut utiliser sa manipulation nulle indigène pour le manipuler.  
  
## <a name="implementing-the-parse-method"></a>Implémentation de la méthode Parse  
 Les méthodes **Parse** et **ToString** permettent des conversions vers et depuis les représentations de cordes de l’UDT. La méthode **Parse** permet de convertir une chaîne en UDT. Il doit être déclaré **statique** (ou **partagé** dans Visual Basic), et prendre un paramètre de type **System.Data.SqlTypes.SqlString**.  
  
 Le code suivant implémente la méthode **Parse** pour le **Point** UDT, qui sépare les coordonnées X et Y. La méthode **Parse** a un seul argument de type **System.Data.SqlTypes.SqlString**, et suppose que les valeurs X et Y sont fournies comme une chaîne de virgule. La définition de l’attribut **Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall** au **faux** empêche la méthode **Parse** d’être appelée à partir d’une instance nulle de Point.  
  
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
 La méthode **ToString** convertit l’UDT **Point** en une valeur de chaîne. Dans ce cas, la chaîne "NULL" est retournée pour une instance nulle du type **Point.** La méthode **ToString** inverse la méthode **Parse** en utilisant un **System.Text.StringBuilder** pour retourner un **System.String** délimité par virgule composé des valeurs de coordonnées X et Y. Parce que **InvokeIfReceiverIsNull** par défaut à faux, le chèque pour une instance nulle de **Point** est inutile.  
  
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
 Le **Point** UDT expose les coordonnées X et Y qui sont mises en œuvre en tant que propriétés publiques de lecture-écriture de type **System.Int32**.  
  
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
 Lors de l'utilisation de données de type défini par l'utilisateur, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] convertit automatiquement les valeurs binaires en valeurs de type défini par l'utilisateur. Ce processus de conversion nécessite de vérifier que les valeurs sont adaptées au format de sérialisation du type et de s'assurer que la valeur peut être désérialisée correctement. Cela permet de garantir que la valeur peut être reconvertie au format binaire. Dans le cas des types définis par l'utilisateur ordonnés par octet, cela permet de s'assurer également que la valeur binaire résultante correspond à la valeur binaire d'origine. Cela empêche des valeurs non valides d'être rendues persistantes dans la base de données. Dans certains cas, ce niveau de contrôle peut être inadéquat. Une validation supplémentaire peut être requise lorsque les valeurs de type défini par l'utilisateur doivent se trouver dans un domaine ou une plage attendu(e). Par exemple, un type défini par l'utilisateur qui implémente une date peut exiger que la valeur de jour soit un nombre positif compris dans une certaine plage de valeurs valides.  
  
 La propriété **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName** de la propriété **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** vous permet de fournir le nom d’une méthode de validation que le serveur exécute lorsque les données sont affectées à un UDT ou converties en UDT. **ValidationMethodName** est également appelé pendant le fonctionnement de l’utilitaire bcp, BULK INSERT, DBCC CHECKDB, DBCC CHECKFILEGROUP, DBCC CHECKTABLE, requête distribuée et flux de données tabulaires (TDS) opérations d’appel de procédure à distance (RPC). La valeur par défaut pour **ValidationMethodName** est nulle, ce qui indique qu’il n’existe pas de méthode de validation.  
  
### <a name="example"></a>Exemple  
 Le fragment de code suivant montre la déclaration pour la classe **Point,** qui spécifie une **ValidationMethodName** de **ValidatePoint**.  
  
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
  
 La méthode de validation peut avoir n’importe quelle portée et devrait revenir **vrai** si la valeur est valide, et **faux** autrement. Si la méthode renvoie **fausse** ou jette une exception, la valeur est traitée comme non valide et une erreur est soulevée.  
  
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
  
 Vous devez appeler explicitement la méthode de validation des ensembles de propriétés et la méthode **Parse** si vous voulez que la méthode de validation s’exécute dans toutes les situations. Cela n'est pas obligatoire, et dans certains cas peut ne pas être souhaitable.  
  
### <a name="parse-validation-example"></a>Exemple de validation Parse  
 Pour vous assurer que la méthode **ValidatePoint** est invoquée dans la classe **Point,** vous devez l’appeler à partir de la méthode **Parse** et des procédures de propriété qui définissent les valeurs de coordonnées X et Y. Le fragment de code suivant montre comment appeler la méthode de validation **ValidatePoint** de la fonction **Parse.**  
  
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
 Le fragment de code suivant montre comment appeler la méthode de validation **ValidatePoint** des procédures de propriété qui réglementent les coordonnées X et Y.  
  
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
 Lors du codage de méthodes UDT, considérez si l'algorithme utilisé pourrait changer avec le temps. Si c'est le cas, vous pourriez envisager de créer une classe séparée pour les méthodes utilisées par votre type défini par l'utilisateur. Si l'algorithme change, vous pouvez recompiler la classe avec le nouveau code et charger l'assembly dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sans affecter le type défini par l'utilisateur. Dans de nombreux cas, les types définis par l'utilisateur peuvent être rechargés à l'aide de l'instruction  [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY, mais cela pourrait provoquer des problèmes avec les données existantes. Par exemple, **l’UDT de devise** incluse dans la base de données d’échantillons **AdventureWorks** utilise une fonction **ConvertCurrency** pour convertir les valeurs de change, qui est implémentée dans une catégorie distincte. Il est possible que les algorithmes de conversion puissent changer de manière imprévisible dans le futur, ou que de nouvelles fonctionnalités soient requises. Séparer la fonction **ConvertCurrency** de la mise en œuvre **de l’UDT de devises** offre une plus grande flexibilité lors de la planification des changements futurs.  
  
### <a name="example"></a>Exemple  
 La classe **Point** contient trois méthodes simples pour calculer la distance: **Distance**, **DistanceDe** et **DistanceFromXY**. Chacun renvoie un **double** calcul de la distance de **Point** à zéro, la distance d’un point spécifié à **Point**, et la distance entre les coordonnées spécifiées X et Y jusqu’au **point**. **Distance** et **distanceDe** chaque appel **DistanceDeXY**, et de démontrer comment utiliser des arguments différents pour chaque méthode.  
  
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
 La classe **Microsoft.SqlServer.Server.SqlMethodAttribute** fournit des attributs personnalisés qui peuvent être utilisés pour marquer les définitions de la méthode afin de spécifier le déterminisme, sur le comportement d’appel nul, et de spécifier si une méthode est un mutateur. Les valeurs par défaut de ces propriétés sont assumées et l'attribut personnalisé est utilisé uniquement lorsqu'une valeur non définie par défaut est exigée.  
  
> [!NOTE]  
>  La classe **SqlMethodAttribute** hérite de la classe **SqlFunctionAttribute,** de sorte **que SqlMethodAttribute** hérite des champs **FillRowMethodName** et **TableDefinition** de **SqlFunctionAttribute**. Cela implique qu'il est possible d'écrire une méthode table, ce qui n'est pas le cas. La méthode compile et l’assemblage se déploie, mais une erreur sur le type de retour **IEnumerable** \<est soulevée au moment de\<l’exécution avec le\<message suivant: "Méthode, propriété, ou champ 'nom>' en classe 'classe>' dans l’assemblage 'assemblage>' a type de retour invalide."  
  
 Le tableau suivant décrit certaines des propriétés **Microsoft.SqlServer.Server.SqlMethodAttribute** pertinentes qui peuvent être utilisées dans les méthodes UDT, et énumère leurs valeurs par défaut.  
  
 DataAccess  
 Indique si la fonction implique l'accès aux données utilisateur stockées dans l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par défaut est **DataAccessKind**. **Aucun**.  
  
 IsDeterministic  
 Indique si la fonction produit les mêmes valeurs de sortie étant donné les mêmes valeurs d'entrée et le même état de la base de données. La valeur par défaut est **false**.  
  
 IsMutator  
 Indique si la méthode provoque une modification d'état dans l'instance de type défini par l'utilisateur. La valeur par défaut est **false**.  
  
 IsPrecise  
 Indique si la fonction implique des calculs imprécis, tels que des opérations à virgule flottante. La valeur par défaut est **false**.  
  
 OnNullCall  
 Indique si la méthode est appelée lorsque des arguments d'entrée de référence nulle sont spécifiés. Par défaut est **vrai**.  
  
### <a name="example"></a>Exemple  
 La propriété **Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator** vous permet de marquer une méthode qui permet un changement dans l’état d’un cas d’UDT. [!INCLUDE[tsql](../../includes/tsql-md.md)] ne vous permet pas de définir deux propriétés de type défini par l'utilisateur dans la clause SET d'une instruction UPDATE. Toutefois, vous pouvez avoir une méthode marquée comme mutateur qui modifie les deux membres.  
  
> [!NOTE]  
>  Les méthodes mutateurs ne sont pas autorisés dans les requêtes. Elles peuvent être appelées uniquement dans les instructions d'assignation ou les instructions de modification de données. Si une méthode marquée comme muteur ne retourne pas **vide** (ou n’est pas un **Sous** dans Visual Basic), CREATE TYPE échoue avec une erreur.  
  
 La déclaration suivante suppose l’existence d’un **UDT Triangles** qui a une méthode **Rotate.** L’instruction de mise à jour suivante [!INCLUDE[tsql](../../includes/tsql-md.md)] invoque la méthode **Rotate** :  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 La méthode **Rotate** est décorée avec le réglage **d’attribut SqlMethod** **IsMutator** à **vrai** de sorte que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut marquer la méthode comme une méthode de mutator. Le code définit également **OnNullCall** à **faux**, ce qui indique au serveur que la méthode renvoie une référence nulle **(rien** dans Visual Basic) si l’un des paramètres d’entrée sont des références nulles.  
  
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
 Lors de la mise en œuvre d’un UDT avec un format défini par l’utilisateur, vous devez implémenter les méthodes **Read** and **Write** qui implémentent l’interface Microsoft.SqlServer.Server.IBinarySerialize pour gérer la sérialisation et la désélisement des données UDT. Vous devez également spécifier la propriété **MaxByteSize** de la **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**.  
  
### <a name="the-currency-udt"></a>Le type défini par l'utilisateur Currency  
 L’UDT **de devise** est inclus avec les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]échantillons [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]CLR qui peuvent être installés avec , en commençant par .  
  
 L’UDT **de devises** soutient le traitement des montants d’argent dans le système monétaire d’une culture particulière. Vous devez définir deux domaines: une **chaîne** pour **CultureInfo**, qui spécifie qui a émis la monnaie (en-nous, par exemple) et une **décimale** pour **CurrencyValue**, le montant d’argent.  
  
 Bien qu’il ne soit pas utilisé par le serveur pour effectuer des comparaisons, **l’UDT devise** implémente **l’interface System.IComparable,** qui expose une seule méthode, **System.IComparable.CompareTo**. Celle-ci est utilisée du côté client dans les situations où il est souhaitable de comparer ou d'ordonner précisément des valeurs monétaire dans des cultures.  
  
 Le code qui s'exécute dans le CLR compare la culture séparément de la valeur monétaire. Pour le code [!INCLUDE[tsql](../../includes/tsql-md.md)], les actions suivantes déterminent la comparaison :  
  
1.  Définissez l’attribut **IsByteOrdered** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à vrai, qui indique d’utiliser la représentation binaire persistée sur le disque pour des comparaisons.  
  
2.  Utilisez la méthode **Écrire** pour **l’UDT de devise** pour déterminer comment l’UDT est [!INCLUDE[tsql](../../includes/tsql-md.md)] persisté sur le disque et donc comment les valeurs UDT sont comparées et commandées pour les opérations.  
  
3.  Enregistrer **l’UDT de devise** en utilisant le format binaire suivant :  

    1.  Enregistrez la culture en tant que chaîne encodée UTF-16 pour les octets 0-19, avec un remplissage à droite avec des caractères Null.  
  
    2.  Utilisez les octets 20 et plus pour contenir la valeur décimale de la monnaie.  
  
 L'objectif du remplissage est de s'assurer que la culture est complètement séparée de la valeur monétaire, de sorte que lorsque deux types définis par l'utilisateur sont comparés dans le code [!INCLUDE[tsql](../../includes/tsql-md.md)], les octets de culture soient comparés à des octets de culture et les valeurs d'octets de monnaie soient comparées à des valeurs d'octets de monnaie.  
  
 Pour la liste complète du code pour **l’UDT de devise,** suivez les instructions pour l’installation des échantillons CLR dans [SQL Server Database Engine Samples](https://msftengprodsamples.codeplex.com/).  
  
### <a name="currency-attributes"></a>Attributs Currency  
 L’UDT **de devise** est défini avec les attributs suivants.  
  
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
 Lorsque vous choisissez le format de sérialisation **UserDefined,** vous devez également implémenter l’interface **IBinarySerialize** et créer vos propres méthodes **de lecture** et **d’écriture.** Les procédures suivantes de **l’UDT de devise** utilisent le **System.IO.BinaryReader** et **System.IO.BinaryWriter** pour lire et écrire à l’UDT.  
  
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
  
 Pour la liste complète du code pour **l’UDT de devise,** voir [SQL Server Database Engine Samples](https://msftengprodsamples.codeplex.com/).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un type défini par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
