---
title: Cartographier les données de paramètres CLR (fr) Microsoft Docs
description: Cet article répertorie les types de données Microsoft SQL Server, les équivalents dans le CLR pour SQL Server, et les équivalents CLR natifs dans le cadre .NET.
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
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488454"
---
# <a name="mapping-clr-parameter-data"></a>Mappage des données de paramètres CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le tableau [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suivant répertorie les types de données, leurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] équivalents dans l’heure courante de l’exécution de langue (CLR) pour dans **l’espace de nom System.Data.SqlTypes,** et leurs équivalents CLR natifs dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] cadre .NET.  
  
||||  
|-|-|-|  
|**Type de données SQL Server**|Type (dans System.Data.SqlTypes ou Microsoft.SqlServer.Types)|**Type de données CLR (.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64, Nullable\<Int64>**|  
|**binary**|**SqlBytes, SqlBinary**|**Byte[]**|  
|**bit**|**SqlBoolean**|**Boolean, Nullable\<Boolean>**|  
|**char**|None|None|  
|**cursor**|None|None|  
|**date**|**Temps de sqlDate**|**DateTime, Nullable\<DateTime>**|  
|**datetime**|**Temps de sqlDate**|**DateTime, Nullable\<DateTime>**|  
|**datetime2**|None|**DateTime, Nullable\<DateTime>**|  
|**Datetimeoffset**|**Aucun**|**DateTimeOffset, Nullable\<DateTimeOffset>**|  
|**decimal**|**Sqldecimal**|**Décimale, Décalité\<nulle>**|  
|**float**|**Sqldouble.op_implicit**|**Double, Nullable\<Double>**|  
|**Geography**|**SqlGeography**<br /><br /> **SqlGeography** est défini dans Microsoft.SqlServer.Types.dll, qui est installé avec [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SQL Server et peut être téléchargé à partir du [pack de fonctionnalités](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**geometry**|**SqlGeometry**<br /><br /> **SqlGeometry** est défini dans Microsoft.SqlServer.Types.dll, qui est installé avec [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SQL Server et peut être téléchargé à partir du [pack de fonctionnalités](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **SqlHierarchyId** est défini dans Microsoft.SqlServer.Types.dll, qui est installé avec [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SQL Server et peut être téléchargé à partir du [pack d’entités](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**image**|None|None|  
|**int**|**SqlInt32**|**Int32, Nullable\<Int32>**|  
|**money**|**SqlMoney (SqlMoney)**|**Décimale, Décalité\<nulle>**|  
|**nchar**|**SqlChars, SqlString**|**String, Char[]**|  
|**ntext**|None|None|  
|**numeric**|**Sqldecimal**|**Décimale, Décalité\<nulle>**|  
|**nvarchar**|**SqlChars, SqlString**<br /><br /> **SQLChars** est un meilleur match pour le transfert et l’accès des données, et **SQLString** est un meilleur match pour effectuer les opérations String.|**String, Char[]**|  
|**nvarchar(1), nchar(1)**|**SqlChars, SqlString**|**Char, String, Char[],\<Nullable char>**|  
|**real**|**SqlSingle** (la gamme de **SqlSingle**, cependant, est plus grande que **réelle**)|**Simple, Nullable\<Single>**|  
|**rowversion**|None|**Byte[]**|  
|**smallint**|**SqlInt16**|**Int16, Nullable\<Int16>**|  
|**smallmoney**|**SqlMoney (SqlMoney)**|**Décimale, Décalité\<nulle>**|  
|**sql_variant**|None|**Object**|  
|**table**|None|None|  
|**text**|None|None|  
|**time**|None|**TimeSpan, Nullable\<TimeSpan>**|  
|**timestamp**|None|None|  
|**tinyint**|**SqlByte**|**Byte, Nullable\<Byte>**|  
|**uniqueidentifier**|**SqlGuid (SqlGuid)**|**Guid, Nullable\<Guid>**|  
|**Type défini par l’utilisateur (UDT)**|None|La même classe liée au type défini par l'utilisateur dans le même assembly ou un assembly dépendant.|  
|**varbinary**|**SqlBytes, SqlBinary**|**Byte[]**|  
|**varbinaire(1), binaire(1)**|**SqlBytes, SqlBinary**|**byte, Byte[], Nullable\<byte>**|  
|**varchar**|None|None|  
|**xml**|**Sqlxml**|None|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Conversion automatique de types de données avec les paramètres de sortie  
 Une méthode CLR peut retourner des informations au code d’appel ou au programme en marquant un paramètre d’entrée avec le modificateur **(Microsoft** Visual C) ou ** \<Out()> ByRef** (Microsoft Visual Basic) Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le paramètre d’entrée est un type de données CLR dans le **système.Data.SqlTypes** namespace, et le programme d’appels spécifie son type de données équivalent comme paramètre d’entrée, une conversion de type se produit automatiquement lorsque la méthode CLR retourne le type de données.  
  
 Par exemple, la procédure stockée clR suivante a un paramètre d’entrée de type de données **ClR SqlInt32** qui est marqué avec **out** (C) ou ** \<Out()> ByRef** (Visual Basic):  
  
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
  
 Une fois l’assemblage construit et créé dans la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données, la procédure stockée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est créée avec le Transact-SQL suivant, qui spécifie un type de données d’int comme paramètre OUTPUT : **int**  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 Lorsque la procédure stockée par CLR est appelée, le type de données **SqlInt32** est automatiquement converti en type de données **int** et retourné au programme d’appel.  
  
 Cependant, certains types de données CLR ne peuvent pas être convertis automatiquement en leurs types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] équivalents via un paramètre de sortie. Le tableau suivant répertorie ces exceptions.  
  
|||  
|-|-|  
|**Type de données CLR (SQL Server)**|**Type de données SQL Server**|  
|**Decimales**|SMALLMONEY|  
|**SqlMoney (SqlMoney)**|SMALLMONEY|  
|**Decimal**|money|  
|**Datetime**|smalldatetime|  
|**SQLDateTime (en anglais)**|smalldatetime|  
  
## <a name="change-history"></a>Historique des modifications  
  
|Mise à jour du contenu|  
|---------------------|  
|Ajout **de SqlGeography**, **SqlGeometry**, et **SqlHierarchyId** types à la table de cartographie.|  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans le .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
