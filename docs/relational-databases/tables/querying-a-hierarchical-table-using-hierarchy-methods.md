---
title: "Interrogation d&#39;une table hi&#233;rarchique &#224; l&#39;aide de m&#233;thodes hi&#233;rarchiques | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "HierarchyID"
ms.assetid: 3b4f7dae-65b5-4d8d-8641-87aba9aa692d
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Interrogation d&#39;une table hi&#233;rarchique &#224; l&#39;aide de m&#233;thodes hi&#233;rarchiques
Maintenant que la table HumanResources.EmployeeOrg est entièrement remplie, cette tâche vous indiquera comment interroger la hiérarchie à l'aide de certaines des méthodes hiérarchiques.  
  
### Pour rechercher des nœuds subordonnés  
  
1.  Sariya a un employé subordonné. Pour rechercher les subordonnés de Sariya, exécutez la requête suivante qui utilise la méthode [IsDescendantOf](../../t-sql/data-types/isdescendantof-database-engine.md) :  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.IsDescendantOf(@CurrentEmployee ) = 1 ;  
    ```  
  
    Le résultat répertorie Sariya et Wanida. Sariya est répertoriée car elle est la descendante au niveau 0. Wanida est la descendante au niveau 1.  
  
2.  Vous pouvez également créer des requêtes sur ces informations à l’aide de la méthode [GetAncestor](../../t-sql/data-types/getancestor-database-engine.md). `GetAncestor` prend un argument pour le niveau que vous tentez de retourner. Étant donné que Wanida est un niveau plus bas que Sariya, utilisez `GetAncestor(1)` comme indiqué dans le code suivant :  
  
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
  
3.  Modifiez maintenant `@CurrentEmployee` sur David (EmployeeID 6) et le niveau sur 2. Exécutez le code suivant pour retourner également Wanida :  
  
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
  
### Pour utiliser GetRoot et GetLevel  
  
1.  À mesure que la hiérarchie s'agrandit, il devient plus difficile de déterminer l'emplacement des membres dans la hiérarchie. La méthode [GetLevel](../../t-sql/data-types/getlevel-database-engine.md) permet de déterminer le nombre de niveaux sous chaque ligne dans la hiérarchie. Exécutez le code suivant pour consulter les niveaux de toutes les lignes :  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode.GetLevel() AS EmpLevel, *  
    FROM HumanResources.EmployeeOrg ;  
    GO  
  
    ```  
  
2.  La méthode [GetRoot](../../t-sql/data-types/getroot-database-engine.md) permet de rechercher le nœud racine dans la hiérarchie. Le code suivant retourne la ligne unique qui est la racine :  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode = hierarchyid::GetRoot() ;  
    GO  
  
    ```  
  
La tâche suivante réorganisera la hiérarchie.  
  
## Tâche suivante de la leçon  
[Réorganisation de données dans une table hiérarchique à l'aide de méthodes hiérarchiques](../../relational-databases/tables/reordering-data-in-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
  
