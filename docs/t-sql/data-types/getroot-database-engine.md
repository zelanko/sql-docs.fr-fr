---
title: "GetRoot (moteur de base de données) | Documents Microsoft"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GetRoot
- GetRoot_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetRoot [Database Engine]
ms.assetid: 240b70f1-eeda-44ab-b4bb-9e4af80fa7c0
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4de7e4010400cbf3d192efb3dd6709792d734ba
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="getroot-database-engine"></a>GetRoot (moteur de base de données)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne la racine de la structure hiérarchique. GetRoot() est une méthode statique.
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Transact-SQL syntax  
hierarchyid::GetRoot ( )   
```  
  
```sql
-- CLR syntax  
static SqlHierarchyId GetRoot ( )   
```  
  
## <a name="return-types"></a>Types de retour  
**SQL Server de type de retour : hierarchyid**
  
**CLR de type de retour : SqlHierarchyId**
  
## <a name="remarks"></a>Notes  
Sert à déterminer le nœud racine dans une arborescence hiérarchique.
  
## <a name="examples"></a>Exemples  
  
### <a name="a-transact-sql-example"></a>A. Exemple Transact-SQL  
L'exemple suivant retourne la racine de l'arborescence hiérarchique :
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode = hierarchyid::GetRoot()  
```  
  
### <a name="b-clr-example"></a>B. Exemple CLR  
L’extrait de code suivant appelle la méthode GetRoot() :
  
```sql
SqlHierarchyId.GetRoot()  
```  
  
## <a name="see-also"></a>Voir aussi
[Référence de méthodes de type de données hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Données hiérarchiques &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  

