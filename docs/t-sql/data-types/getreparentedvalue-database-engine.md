---
title: "GetReparentedValue (moteur de base de données) | Documents Microsoft"
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
- Reparent_TSQL
- Reparent
dev_langs:
- TSQL
helpviewer_keywords:
- Reparent [Database Engine]
ms.assetid: f47f8e25-08ef-498b-84f4-a317aca1f358
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 57f565258c7fd95347d7d9bd36b2dd2034712efe
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="getreparentedvalue-database-engine"></a>GetReparentedValue (moteur de base de données)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un nœud dont le chemin de la racine est le chemin d’accès à *newRoot*, suivi par le chemin d’accès à partir de *oldRoot* à *cela*.
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Transact-SQL syntax  
node. GetReparentedValue ( oldRoot, newRoot )  
```  
  
```sql
-- CLR syntax  
SqlHierarchyId GetReparentedValue ( SqlHierarchyId oldRoot , SqlHierarchyId newRoot )  
```  
  
## <a name="arguments"></a>Arguments  
*oldRoot*  
A **hierarchyid** qui est le nœud qui représente le niveau de la hiérarchie qui doit être modifié.
  
*newRoot*  
A **hierarchyid** qui représente le nœud qui remplacera le *oldRoot* section du nœud actuel afin de le déplacer.
  
## <a name="return-types"></a>Types de retour  
**SQL Server de type de retour : hierarchyid**
  
**CLR de type de retour : SqlHierarchyId**
  
## <a name="remarks"></a>Notes  
Peut être utilisé pour modifier l’arborescence en déplaçant des nœuds de *oldRoot* à *newRoot*. GetReparentedValue peut être utilisé pour déplacer un nœud d'une hiérarchie vers un nouvel emplacement de la hiérarchie. Le **hierarchyid** représente le type de données, mais n’applique pas la structure hiérarchique. Les utilisateurs doivent s'assurer que la structure hierarchyid convient au nouvel emplacement. Un index unique sur la **hierarchyid** type de données peut permettre d’éviter les entrées en double. Pour obtenir un exemple de déplacement d’une sous-arborescence entière, consultez [hiérarchique de données &#40; SQL Server &#41; ](../../relational-databases/hierarchical-data-sql-server.md).
  
## <a name="examples"></a>Exemples  
  
### <a name="a-comparing-two-node-locations"></a>A. Comparaison de deux emplacements de nœuds  
L'exemple suivant montre le hierarchyid actuel d'un nœud. Il montre également que le **hierarchyid** du nœud est si le nœud était déplacé pour devenir un descendant de la  **@NewParent**  nœud. Il utilise la méthode `ToString()` pour afficher les relations hiérarchiques.
  
```sql
DECLARE @SubjectEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
SELECT @SubjectEmployee = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\gail0' ;  
SELECT @OldParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\roberto0' ; -- who is /1/1/  
SELECT @NewParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\wanida0' ; -- who is /2/3/  
  
SELECT OrgNode.ToString() AS Current_OrgNode_AS_Text,   
(@SubjectEmployee. GetReparentedValue(@OldParent, @NewParent) ).ToString() AS Proposed_OrgNode_AS_Text,  
OrgNode AS Current_OrgNode,  
@SubjectEmployee. GetReparentedValue(@OldParent, @NewParent) AS Proposed_OrgNode,  
*  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode = @SubjectEmployee ;  
GO  
```  
  
### <a name="b-updating-a-node-to-a-new-location"></a>B. Mise à jour d'un nœud à un nouvel emplacement  
L'exemple suivant utilise `GetReparentedValue()` dans une instruction UPDATE pour déplacer un nœud d'un emplacement à un autre dans la hiérarchie :
  
```sql
DECLARE @SubjectEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
SELECT @SubjectEmployee = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\gail0' ; -- Node /1/1/2/  
SELECT @OldParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\roberto0' ; -- Node /1/1/  
SELECT @NewParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\wanida0' ; -- Node /2/3/  
  
UPDATE HumanResources.EmployeeDemo  
SET OrgNode = @SubjectEmployee. GetReparentedValue(@OldParent, @NewParent)   
WHERE OrgNode = @SubjectEmployee ;  
  
SELECT OrgNode.ToString() AS Current_OrgNode_AS_Text,   
*  
FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\gail0' ; -- Now node /2/3/2/  
```  
  
### <a name="c-clr-example"></a>C. Exemple CLR  
L’extrait de code suivant appelle la méthode GetReparentedValue :
  
```sql
this. GetReparentedValue(oldParent, newParent)  
```  
  
## <a name="see-also"></a>Voir aussi
[Référence de méthodes de type de données hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Données hiérarchiques &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  

