---
title: "Parse (moteur de base de données) | Documents Microsoft"
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Parse
- Parse_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Parse [Database Engine]
ms.assetid: b37e28b6-6e2e-470a-945b-ce5252da743a
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 027940c7575f3c7901cd8668879064ff375d9986
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="parse-database-engine"></a>Parse (moteur de base de données)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Parse convertit la représentation sous forme de chaîne canonique d’un **hierarchyid** à un **hierarchyid** valeur. L’analyse est appelée implicitement lorsqu’une conversion d’un type chaîne en **hierarchyid** se produit. Agit comme l’opposé de [ToString](../../t-sql/data-types/tostring-database-engine.md). Parse() est une méthode statique.
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Transact-SQL syntax  
hierarchyid::Parse ( input )  
-- This is functionally equivalent to the following syntax   
-- which implicitly calls Parse():  
CAST ( input AS hierarchyid )  
```  
  
```sql
-- CLR syntax  
static SqlHierarchyId Parse ( SqlString input )   
```  
  
## <a name="arguments"></a>Arguments  
*entrée*  
[!INCLUDE[tsql](../../includes/tsql-md.md)] : valeur du type de données character converti.
  
CLR : valeur de chaîne évaluée.
  
## <a name="return-types"></a>Types de retour  
**SQL Server de type de retour : hierarchyid**
  
**CLR de type de retour : SqlHierarchyId**
  
## <a name="remarks"></a>Notes  
Si l’analyse reçoit une valeur qui n’est pas une représentation sous forme de chaîne valide d’un **hierarchyid**, une exception est levée. Par exemple, si **char** contiennent des types de données des espaces de fin, une exception est levée.
  
## <a name="examples"></a>Exemples  
  
### <a name="a-converting-transact-sql-values-without-a-table"></a>A. Conversion de valeurs Transact-SQL sans table  
Le de code suivant montre comment utiliser `ToString` pour convertir un **hierarchyid** valeur à une chaîne, et `Parse` pour convertir une valeur de chaîne en un **hierarchyid**.
  
```sql
DECLARE @StringValue AS nvarchar(4000), @hierarchyidValue AS hierarchyid  
SET @StringValue = '/1/1/3/'  
SET @hierarchyidValue = 0x5ADE  
  
SELECT hierarchyid::Parse(@StringValue) AS hierarchyidRepresentation,  
@hierarchyidValue.ToString() AS StringRepresentation ;
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
hierarchyidRepresentation    StringRepresentation
-------------------------    -----------------------
0x5ADE                       /1/1/3/
```
  
### <a name="b-clr-example"></a>B. Exemple CLR  
L’extrait de code suivant appelle la méthode Parse() :
  
```sql
string input = “/1/2/”;  
SqlHierarchyId.Parse(input);  
```  
  
## <a name="see-also"></a>Voir aussi
[Référence de méthodes de type de données hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Données hiérarchiques &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  

