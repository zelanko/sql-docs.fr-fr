---
title: "ToString (moteur de base de données) | Documents Microsoft"
ms.custom: 
ms.date: 07/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ToString
- ToString_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ToString [Database Engine]
ms.assetid: 5fc11ca5-c26d-4518-9512-67aa0270f110
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1544b27215083f8628696cebaaf14c53c628a9ba
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="tostring-database-engine"></a>ToString (moteur de base de données)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne une chaîne avec la représentation logique de *cela*. ToString est appelée implicitement lorsqu’une conversion de **hierarchyid** à une chaîne de type se produit. Agit comme l’opposé de [Parse &#40; moteur de base de données &#41;](../../t-sql/data-types/parse-database-engine.md).
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Transact-SQL syntax  
node.ToString  ( )   
-- This is functionally equivalent to the following syntax  
-- which implicitly calls ToString():  
CAST(node AS nvarchar(4000))  
```  
  
```sql
-- CLR syntax  
string ToString  ( )   
```  
  
## <a name="return-types"></a>Types de retour
**Type:nvarchar(4000) de retour SQL Server**
  
**Type : chaîne retour CLR**
  
## <a name="remarks"></a>Notes  
Retourne l'emplacement logique dans la hiérarchie. Par exemple, `/2/1/` représente la quatrième ligne ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) dans la structure hiérarchique suivante d’un système de fichiers :
  
```sql
/        C:\  
/1/      C:\Database Files  
/2/      C:\Program Files  
/2/1/    C:\Program Files\Microsoft SQL Server  
/2/2/    C:\Program Files\Microsoft Visual Studio  
/3/      C:\Windows  
```  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-transact-sql-example-in-a-table"></a>A. Exemple Transact-SQL dans une table  
L’exemple suivant retourne le `OrgNode` colonne à la fois comme le **hierarchyid** type de données et dans le format de chaîne plus lisible :
  
```sql
SELECT OrgNode,  
OrgNode.ToString() AS Node  
FROM HumanResources.EmployeeDemo  
ORDER BY OrgNode ;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
OrgNode   Node  
0x        /  
0x58      /1/  
0x5AC0    /1/1/  
0x5B40    /1/2/  
0x5BC0    /1/3/  
0x5C20    /1/4/  
...  
```  
  
### <a name="b-converting-transact-sql-values-without-a-table"></a>B. Conversion de valeurs Transact-SQL sans table  
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
  
`hierarchyidRepresentation    StringRepresentation`
  
`-------------------------    -----------------------`
  
`0x5ADE                       /1/1/3/`
  
### <a name="c-clr-example"></a>C. Exemple CLR  
L’extrait de code suivant appelle la méthode ToString() :
  
```sql
this.ToString()  
```  
  
## <a name="see-also"></a>Voir aussi
[Référence de méthodes de type de données hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Données hiérarchiques &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  

