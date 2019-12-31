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
manager: craigg
ms.openlocfilehash: 17eeefbe125722c666f9f56394028da8c66a66b3
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75232280"
---
# <a name="mapping-clr-parameter-data"></a>Mappage des données de paramètres CLR
  Le tableau suivant répertorie [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les types de données, leurs équivalents dans le Common Language Runtime ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR) `System.Data.SqlTypes` pour dans l’espace de noms, et leurs équivalents CLR natifs dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.  
  
||||  
|-|-|-|  
|**Type de données SQL Server**|Type (dans System.Data.SqlTypes ou Microsoft.SqlServer.Types)|**Type de données CLR (.NET Framework)**|  
|`bigint`|`SqlInt64`|**Int64, Nullable\<Int64>**|  
|`binary`|`SqlBytes, SqlBinary`|`Byte[]`|  
|`bit`|`SqlBoolean`|**Boolean, Nullable\<>**|  
|`char`|Aucune|Aucune|  
|`cursor`|Aucune|Aucune|  
|`date`|`SqlDateTime`|**DateTime, DateTime\<Nullable>**|  
|`datetime`|`SqlDateTime`|**DateTime, DateTime\<Nullable>**|  
|`datetime2`|Aucune|**DateTime, DateTime\<Nullable>**|  
|`DATETIMEOFFSET`|`None`|**DateTimeOffset, DateTimeOffset\<Nullable>**|  
|`decimal`|`SqlDecimal`|**Décimal, Nullable\<>décimal**|  
|`float`|`SqlDouble`|**Double, double\<>Nullable**|  
|`geography`|`SqlGeography`<br /><br /> `SqlGeography`est défini dans Microsoft. SqlServer. types. dll, qui est installé avec SQL Server et peut être téléchargé à partir [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]du [Feature Pack](https://www.microsoft.com/download/details.aspx?id=53164).|Aucune|  
|`geometry`|`SqlGeometry`<br /><br /> `SqlGeometry`est défini dans Microsoft. SqlServer. types. dll, qui est installé avec SQL Server et peut être téléchargé à partir [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]du [Feature Pack](https://www.microsoft.com/download/details.aspx?id=53164).|Aucune|  
|`hierarchyid`|`SqlHierarchyId`<br /><br /> `SqlHierarchyId`est défini dans Microsoft. SqlServer. types. dll, qui est installé avec SQL Server et peut être téléchargé à partir [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]du [Feature Pack](https://www.microsoft.com/download/details.aspx?id=53164).|Aucune|  
|`image`|Aucune|Aucune|  
|`int`|`SqlInt32`|**Int32, Nullable\<Int32>**|  
|`money`|`SqlMoney`|**Décimal, Nullable\<>décimal**|  
|`nchar`|`SqlChars, SqlString`|`String, Char[]`|  
|`ntext`|Aucune|Aucune|  
|`numeric`|`SqlDecimal`|**Décimal, Nullable\<>décimal**|  
|`nvarchar`|`SqlChars, SqlString`<br /><br /> 
  `SQLChars` est une meilleure correspondance pour le transfert de données et leur accès, et `SQLString` est une meilleure correspondance pour effectuer des opérations sur une chaîne.|`String, Char[]`|  
|`nvarchar(1), nchar(1)`|`SqlChars, SqlString`|**Char, String, Char [], Nullable\<char>**|  
|`real`|
  `SqlSingle` (la plage de `SqlSingle`, toutefois, est plus grande que `real`)|**Single, Nullable\<>unique**|  
|`rowversion`|Aucune|`Byte[]`|  
|`smallint`|`SqlInt16`|**Int16, Nullable\<Int16>**|  
|`smallmoney`|`SqlMoney`|**Décimal, Nullable\<>décimal**|  
|`sql_variant`|Aucune|`Object`|  
|`table`|Aucune|Aucune|  
|`text`|Aucune|Aucune|  
|`time`|Aucune|**TimeSpan, null\<TimeSpan>**|  
|`timestamp`|Aucune|Aucune|  
|`tinyint`|`SqlByte`|**Byte,>\<d’octets Nullable**|  
|`uniqueidentifier`|`SqlGuid`|**Guid,>\<GUID Nullable**|  
|`User-defined type(UDT)`|Aucune|La même classe liée au type défini par l'utilisateur dans le même assembly ou un assembly dépendant.|  
|**varbinary**|`SqlBytes, SqlBinary`|`Byte[]`|  
|`varbinary(1), binary(1)`|`SqlBytes, SqlBinary`|**Byte, Byte [],>\<d’octets Nullable**|  
|`varchar`|Aucune|Aucune|  
|`xml`|`SqlXml`|Aucune|  
  
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
|`Decimal`|smallmoney|  
|`SqlMoney`|smallmoney|  
|`Decimal`|money|  
|`DateTime`|smalldatetime|  
|`SQLDateTime`|smalldatetime|  
  
## <a name="change-history"></a>Historique des modifications  
  
|Mise à jour du contenu|  
|---------------------|  
|Ajout de types `SqlGeography`, `SqlGeometry` et `SqlHierarchyId` à la table de mappage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans le .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
