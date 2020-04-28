---
title: Mappage des données de paramètres CLR | Microsoft Docs
description: Cet article répertorie les types de données Microsoft SQL Server, les équivalents dans le CLR pour SQL Server et les équivalents CLR natifs dans le .NET Framework.
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
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
ms.openlocfilehash: 360a94229b107e9f24bb2a769157c75cdeb3c143
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488454"
---
# <a name="mapping-clr-parameter-data"></a>Mappage des données de paramètres CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tableau suivant répertorie les types de données, leurs équivalents dans le Common Language Runtime ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR) de dans l’espace de noms **System. Data. SqlTypes** et leurs équivalents [!INCLUDE[msCoName](../../includes/msconame-md.md)] CLR natifs dans le .NET Framework.  
  
||||  
|-|-|-|  
|**Type de données SQL Server**|Type (dans System.Data.SqlTypes ou Microsoft.SqlServer.Types)|**Type de données CLR (.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64, Nullable\<Int64>**|  
|**binary**|**SqlBytes, SqlBinary**|**Byte []**|  
|**bit**|**SqlBoolean**|**Boolean, Nullable\<>**|  
|**char**|None|None|  
|**cursor**|None|None|  
|**date**|**SqlDateTime**|**DateTime, DateTime\<Nullable>**|  
|**datetime**|**SqlDateTime**|**DateTime, DateTime\<Nullable>**|  
|**datetime2**|None|**DateTime, DateTime\<Nullable>**|  
|**DATETIMEOFFSET**|**Aucun**|**DateTimeOffset, DateTimeOffset\<Nullable>**|  
|**decimal**|**SqlDecimal**|**Décimal, Nullable\<>décimal**|  
|**float**|**SqlDouble**|**Double, double\<>Nullable**|  
|**Geography**|**SqlGeography**<br /><br /> **SqlGeography** est défini dans Microsoft. SqlServer. types. dll, qui est installé avec SQL Server et peut être téléchargé à partir [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du [Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**geometry**|**SqlGeometry**<br /><br /> **SqlGeometry** est défini dans Microsoft. SqlServer. types. dll, qui est installé avec SQL Server et peut être téléchargé à partir [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du [Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **SqlHierarchyId** est défini dans Microsoft. SqlServer. types. dll, qui est installé avec SQL Server et peut être téléchargé à partir [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du [Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**image**|None|None|  
|**int**|**SqlInt32**|**Int32, Nullable\<Int32>**|  
|**money**|**SqlMoney**|**Décimal, Nullable\<>décimal**|  
|**nchar**|**SqlChars, SqlString**|**String, Char[]**|  
|**ntext**|None|None|  
|**numeric**|**SqlDecimal**|**Décimal, Nullable\<>décimal**|  
|**nvarchar**|**SqlChars, SqlString**<br /><br /> **SqlChars** est une meilleure correspondance pour le transfert et l’accès aux données, et **SqlString** est une meilleure correspondance pour effectuer des opérations de chaîne.|**String, Char[]**|  
|**nvarchar (1), nchar (1)**|**SqlChars, SqlString**|**Char, String, Char [], Nullable\<char>**|  
|**real**|**SqlSingle** (la plage de **SqlSingle**, toutefois, est supérieure à la taille **réelle**)|**Single, Nullable\<>unique**|  
|**rowversion**|None|**Byte []**|  
|**smallint**|**SqlInt16**|**Int16, Nullable\<Int16>**|  
|**smallmoney**|**SqlMoney**|**Décimal, Nullable\<>décimal**|  
|**sql_variant**|None|**Object**|  
|**table**|None|None|  
|**text**|None|None|  
|**time**|None|**TimeSpan, null\<TimeSpan>**|  
|**timestamp**|None|None|  
|**tinyint**|**SqlByte**|**Byte, Nullable\<Byte>**|  
|**uniqueidentifier**|**SqlGuid**|**Guid,>\<GUID Nullable**|  
|**Type défini par l’utilisateur (UDT)**|None|La même classe liée au type défini par l'utilisateur dans le même assembly ou un assembly dépendant.|  
|**varbinary**|**SqlBytes, SqlBinary**|**Byte []**|  
|**varbinary (1), binaire (1)**|**SqlBytes, SqlBinary**|**byte, Byte[], Nullable\<byte>**|  
|**varchar**|None|None|  
|**xml**|**ISAPI**|None|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Conversion automatique de types de données avec les paramètres de sortie  
 Une méthode CLR peut retourner des informations au code ou au programme appelant en marquant un paramètre d’entrée avec le modificateur **out** (Microsoft Visual C#) ou ** \<out () > ByRef** (Microsoft Visual Basic) si le paramètre d’entrée est un type de données CLR dans le système. l’espace de noms **Data. SqlTypes** et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme appelant spécifient son type de données équivalent comme paramètre d’entrée, une conversion de type se produit automatiquement quand la méthode CLR retourne le type de données.  
  
 Par exemple, la procédure stockée CLR suivante a un paramètre d’entrée de type de données CLR **SqlInt32** qui est marqué avec **out** (C#) ou ** \<out () > ByRef** (Visual Basic) :  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ ... }  
```  
  
```vb  
\<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( \<Out()> ByRef value As SqlInt32)  
...  
End Sub  
```  
  
 Une fois l’assembly généré et créé dans la base de données, la procédure stockée est créée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec l’instruction Transact-SQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suivante, qui spécifie un type de données **int** comme paramètre de sortie :  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 Lorsque la procédure stockée CLR est appelée, le type de données **SqlInt32** est automatiquement converti en un type de données **int** et retourné au programme appelant.  
  
 Cependant, certains types de données CLR ne peuvent pas être convertis automatiquement en leurs types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] équivalents via un paramètre de sortie. Le tableau suivant répertorie ces exceptions.  
  
|||  
|-|-|  
|**Type de données CLR (SQL Server)**|**Type de données SQL Server**|  
|**Décimal**|SMALLMONEY|  
|**SqlMoney**|SMALLMONEY|  
|**Décimal**|money|  
|**Date/heure**|smalldatetime|  
|**SQLDateTime**|smalldatetime|  
  
## <a name="change-history"></a>Historique des modifications  
  
|Mise à jour du contenu|  
|---------------------|  
|Ajout de types **SqlGeography**, **SqlGeometry**et **SqlHierarchyId** à la table de mappage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans le .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
