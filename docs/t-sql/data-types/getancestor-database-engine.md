---
title: "GetAncestor (moteur de base de données) | Documents Microsoft"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GetAncestor_TSQL
- GetAncestor
dev_langs: TSQL
helpviewer_keywords: GetAncestor [Database Engine]
ms.assetid: b96a986f-d5e4-4034-8013-de7974594ee9
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b232238dccf5c22918a8805cdc9cd876dfef5723
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="getancestor-database-engine"></a>GetAncestor (moteur de base de données)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un **hierarchyid** représentant le  *n* ième ancêtre de *cela*.
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Transact-SQL syntax  
child.GetAncestor ( n )   
```  
  
```sql
-- CLR syntax  
SqlHierarchyId GetAncestor ( int n )  
```  
  
## <a name="arguments"></a>Arguments  
*n*  
Un **int**, représentant le nombre de niveaux à remonter dans la hiérarchie.
  
## <a name="return-types"></a>Types de retour
**SQL Server de type de retour : hierarchyid**
  
**CLR de type de retour : SqlHierarchyId**
  
## <a name="remarks"></a>Notes  
Utilisé pour tester si chaque nœud de la sortie a pour ancêtre le nœud actuel au niveau spécifié.
  
Si un nombre supérieur à [GetLevel()](../../t-sql/data-types/getlevel-database-engine.md) est transmis, la valeur NULL est retournée.
  
Si un nombre négatif est passé, une exception est levée.
  
## <a name="examples"></a>Exemples  
  
### <a name="a-finding-the-child-nodes-of-a-parent"></a>A. Recherche des nœuds enfants d'un parent  
`GetAncestor(1)` retourne les employés qui ont `david0` pour ancêtre immédiat (leur parent). L'exemple suivant utilise `GetAncestor(1)`.
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\david0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(1) = @CurrentEmployee ;  
```  
  
### <a name="b-returning-the-grandchildren-of-a-parent"></a>B. Retour des petits-enfants d'un parent  
`GetAncestor(2)` retourne les employés situés dans la hiérarchie deux niveaux en-dessous du nœud actuel. Il s'agit des petits-enfants du nœud actuel. L'exemple suivant utilise `GetAncestor(2)`.
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\ken0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(2) = @CurrentEmployee ;  
```  
  
### <a name="c-returning-the-current-row"></a>C. Retour de la ligne actuelle  
Pour retourner le nœud actuel à l’aide de `GetAncestor(0)`, exécutez le code suivant.
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\david0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(0) = @CurrentEmployee ;  
```  
  
### <a name="d-returning-a-hierarchy-level-if-a-table-is-not-present"></a>D. Retour d'un niveau de la hiérarchie si une table n'est pas présente  
`GetAncestor` retourne le niveau sélectionné de la hiérarchie même si une table n'est pas présente. Par exemple, le code suivant désigne un employé actuel et retourne le `hierarchyid` de l'ancêtre de l'employé actuel sans référence à une table.
  
```sql
DECLARE @CurrentEmployee hierarchyid ;  
DECLARE @TargetEmployee hierarchyid ;  
SELECT @CurrentEmployee = '/2/3/1.2/5/3/' ;  
SELECT @TargetEmployee = @CurrentEmployee.GetAncestor(2) ;  
SELECT @TargetEmployee.ToString(), @TargetEmployee ;  
```  
  
### <a name="e-calling-a-common-language-runtime-method"></a>E. Appel d'une méthode CLR (Common Language Runtime)  
L'extrait de code suivant appelle la méthode `GetAncestor()`.
  
```sql
this.GetAncestor(1)  
```  
  
## <a name="see-also"></a>Voir aussi
[IsDescendantOf &#40; moteur de base de données &#41;](../../t-sql/data-types/isdescendantof-database-engine.md)  
[Référence de méthodes de type de données hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Données hiérarchiques &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
