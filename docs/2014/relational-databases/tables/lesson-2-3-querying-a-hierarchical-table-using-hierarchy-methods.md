---
title: Interrogation d’une table hiérarchique à l’aide de méthodes hiérarchiques | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 3b4f7dae-65b5-4d8d-8641-87aba9aa692d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: be1d0dcd37dba9b1025ba3e4a93aa60d2198b237
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66110044"
---
# <a name="querying-a-hierarchical-table-using-hierarchy-methods"></a>Interrogation d'une table hiérarchique à l'aide de méthodes hiérarchiques
  Maintenant que la table HumanResources.EmployeeOrg est entièrement remplie, cette tâche vous indiquera comment interroger la hiérarchie à l'aide de certaines des méthodes hiérarchiques.  
  
### <a name="to-find-subordinate-nodes"></a>Pour rechercher des nœuds subordonnés  
  
1.  Sariya a un employé subordonné. Pour rechercher les subordonnés de Sariya, exécutez la requête suivante qui utilise la méthode [IsDescendantOf](/sql/t-sql/data-types/isdescendantof-database-engine) :  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.IsDescendantOf(@CurrentEmployee ) = 1 ;  
    ```  
  
     Le résultat répertorie Sariya et Wanida. Sariya est répertoriée car elle est la descendante au niveau 0. Wanida est la descendante au niveau 1.  
  
2.  Vous pouvez également créer des requêtes sur ces informations à l’aide de la méthode [GetAncestor](/sql/t-sql/data-types/getancestor-database-engine) . `GetAncestor` prend un argument pour le niveau que vous tentez de retourner. Étant donné que Wanida est un niveau plus bas que Sariya, utilisez `GetAncestor(1)` comme indiqué dans le code suivant :  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @CurrentEmployee  
    ```  
  
     Cette fois-ci, le résultat répertorie uniquement Wanida.  
  
3.  Modifiez maintenant `@CurrentEmployee` sur David (EmployeeID 6) et le niveau sur 2. Exécutez le code suivant pour retourner également Wanida :  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 6 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(2) = @CurrentEmployee  
    ```  
  
     Cette fois-ci, le résultat répertorie également Mary, deux niveaux plus bas, dont David est également le supérieur.  
  
### <a name="to-use-getroot-and-getlevel"></a>Pour utiliser GetRoot et GetLevel  
  
1.  À mesure que la hiérarchie s'agrandit, il devient plus difficile de déterminer l'emplacement des membres dans la hiérarchie. La méthode [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) permet de déterminer le nombre de niveaux sous chaque ligne dans la hiérarchie. Exécutez le code suivant pour consulter les niveaux de toutes les lignes :  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode.GetLevel() AS EmpLevel, *  
    FROM HumanResources.EmployeeOrg ;  
    GO  
  
    ```  
  
2.  La méthode [GetRoot](/sql/t-sql/data-types/getroot-database-engine) permet de rechercher le nœud racine dans la hiérarchie. Le code suivant retourne la ligne unique qui est la racine :  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode = hierarchyid::GetRoot() ;  
    GO  
  
    ```  
  
 La tâche suivante réorganisera la hiérarchie.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Réorganisation de données dans une table hiérarchique à l'aide de méthodes hiérarchiques](lesson-2-4-reordering-data-in-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
