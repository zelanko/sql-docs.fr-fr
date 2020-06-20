---
title: Mappage des données de paramètres CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlBinary data type
- SqlInt16 data type
- SqlMoney data type
- SqlString data type
- SqlSingle data type
- data types [CLR integration]
- SqlInt64 data type
- SqlDateTime data type
- SqlXml data type
- SqlBoolean data type
- SqlDecimal data type
- SqlBytes data type
- mapping data types [CLR integration]
- SqlChars data type
- SqlInt32 data type
ms.assetid: 89b43ee9-b9ad-4281-a4bf-c7c8d116daa2
author: rothja
ms.author: jroth
ms.openlocfilehash: 70274fcc16caec38d4d960f89fe586b32662dc57
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84954779"
---
# <a name="mapping-clr-parameter-data"></a>Mappage des données de paramètres CLR
  Le tableau suivant répertorie les [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données, leurs équivalents dans le Common Language Runtime (CLR) pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans l' `System.Data.SqlTypes` espace de noms, et leurs équivalents CLR natifs dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.  
  
||||  
|-|-|-|  
|**Type de données SQL Server**|Type (dans System.Data.SqlTypes ou Microsoft.SqlServer.Types)|**Type de données CLR (.NET Framework)**|  
|`bigint`|`SqlInt64`|**Int64, Nullable\<Int64>**|  
|`binary`|`SqlBytes, SqlBinary`|`Byte[]`|  
|`bit`|`SqlBoolean`|**Boolean, Nullable\<Boolean>**|  
|`char`|None|None|  
|`cursor`|None|None|  
|`date`|`SqlDateTime`|**DateTime, Nullable\<DateTime>**|  
|`datetime`|`SqlDateTime`|**DateTime, Nullable\<DateTime>**|  
|`datetime2`|None|**DateTime, Nullable\<DateTime>**|  
|`DATETIMEOFFSET`|`None`|**DateTimeOffset, Nullable\<DateTimeOffset>**|  
|`decimal`|`SqlDecimal`|**Décimal, Nullable\<Decimal>**|  
|`float`|`SqlDouble`|**Double, Nullable\<Double>**|  
|`geography`|`SqlGeography`<br /><br /> `SqlGeography`est défini dans Microsoft.SqlServer.Types.dll, qui est installé avec SQL Server et qui peut être téléchargé à partir du [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Feature Pack](https://www.microsoft.com/download/details.aspx?id=53164).|None|  
|`geometry`|`SqlGeometry`<br /><br /> `SqlGeometry`est défini dans Microsoft.SqlServer.Types.dll, qui est installé avec SQL Server et qui peut être téléchargé à partir du [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Feature Pack](https://www.microsoft.com/download/details.aspx?id=53164).|None|  
|`hierarchyid`|`SqlHierarchyId`<br /><br /> `SqlHierarchyId`est défini dans Microsoft.SqlServer.Types.dll, qui est installé avec SQL Server et qui peut être téléchargé à partir du [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Feature Pack](https://www.microsoft.com/download/details.aspx?id=53164).|None|  
|`image`|None|None|  
|`int`|`SqlInt32`|**Int32, Nullable\<Int32>**|  
|`money`|`SqlMoney`|**Décimal, Nullable\<Decimal>**|  
|`nchar`|`SqlChars, SqlString`|`String, Char[]`|  
|`ntext`|None|None|  
|`numeric`|`SqlDecimal`|**Décimal, Nullable\<Decimal>**|  
|`nvarchar`|`SqlChars, SqlString`<br /><br /> `SQLChars` est une meilleure correspondance pour le transfert de données et leur accès, et `SQLString` est une meilleure correspondance pour effectuer des opérations sur une chaîne.|`String, Char[]`|  
|`nvarchar(1), nchar(1)`|`SqlChars, SqlString`|**Char, String, Char [], Nullable\<char>**|  
|`real`|`SqlSingle` (la plage de `SqlSingle`, toutefois, est plus grande que `real`)|**Unique, Nullable\<Single>**|  
|`rowversion`|None|`Byte[]`|  
|`smallint`|`SqlInt16`|**Int16, Nullable\<Int16>**|  
|`smallmoney`|`SqlMoney`|**Décimal, Nullable\<Decimal>**|  
|`sql_variant`|None|`Object`|  
|`table`|None|None|  
|`text`|None|None|  
|`time`|None|**TimeSpan, Nullable\<TimeSpan>**|  
|`timestamp`|None|None|  
|`tinyint`|`SqlByte`|**Byte, Nullable\<Byte>**|  
|`uniqueidentifier`|`SqlGuid`|**Guid, Nullable\<Guid>**|  
|`User-defined type(UDT)`|None|La même classe liée au type défini par l'utilisateur dans le même assembly ou un assembly dépendant.|  
|**varbinary**|`SqlBytes, SqlBinary`|`Byte[]`|  
|`varbinary(1), binary(1)`|`SqlBytes, SqlBinary`|**Byte, Byte [], Nullable\<byte>**|  
|`varchar`|None|None|  
|`xml`|`SqlXml`|None|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Conversion automatique de types de données avec les paramètres de sortie  
 Une méthode CLR peut retourner des informations au programme ou code appelant en marquant un paramètre d'entrée avec le modificateur `out` (Microsoft Visual C#) ou `<Out()> ByRef` (Microsoft Visual Basic). Si le paramètre d'entrée est un type de données CLR de l'espace de noms `System.Data.SqlTypes` et que le programme appelant spécifie son type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] équivalent comme paramètre d'entrée, une conversion de type se produit automatiquement lorsque la méthode CLR retourne le type de données.  
  
 Par exemple, la procédure stockée CLR suivante a un paramètre d'entrée de type de données CLR `SqlInt32` marqué avec `out` (C#) ou `<Out()> ByRef` (Visual Basic) :  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ ... }  
```  
  
```vb  
<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
...  
End Sub  
```  
  
 Après que l'assembly a été créé dans la base de données, la procédure stockée est créée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec le code Transact-SQL suivant, qui spécifie un type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`int` comme paramètre OUTPUT :  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 Lorsque la procédure stockée CLR est appelée, le type de données `SqlInt32` est converti automatiquement en un type de données `int` et retourné au programme appelant.  
  
 Cependant, certains types de données CLR ne peuvent pas être convertis automatiquement en leurs types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] équivalents via un paramètre de sortie. Le tableau suivant répertorie ces exceptions.  
  
|||  
|-|-|  
|**Type de données CLR (SQL Server)**|**Type de données SQL Server**|  
|`Decimal`|SMALLMONEY|  
|`SqlMoney`|SMALLMONEY|  
|`Decimal`|money|  
|`DateTime`|smalldatetime|  
|`SQLDateTime`|smalldatetime|  
  
## <a name="change-history"></a>Historique des modifications  
  
|Mise à jour du contenu|  
|---------------------|  
|Ajout de types `SqlGeography`, `SqlGeometry` et `SqlHierarchyId` à la table de mappage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans le .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
