---
title: Remplissage d’une table hiérarchique à l’aide de méthodes hiérarchiques | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- HierarchyID
helpviewer_keywords:
- HierarchyID
ms.assetid: 2c95fa60-5b8e-4a05-ac09-cffe2b05900a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0ec81ae3a078846ad9288fe75eab9fe30d547a4e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66110063"
---
# <a name="populating-a-hierarchical-table-using-hierarchical-methods"></a>Remplissage d'une table hiérarchique utilisant des méthodes hiérarchiques
  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] a 8 employés travaillant dans le service Marketing. La hiérarchie des employés se présente comme suit :  
  
 **David**, **EmployeeID** 6, est le directeur du marketing. **David**est le supérieur de trois spécialistes en marketing :  
  
-   **Sariya**, **EmployeeID** 46  
  
-   **John**, **EmployeeID** 271  
  
-   **Jill**, **EmployeeID** 119  
  
 **Sariya** est la supérieure de l’assistante marketing**Wanida** ( **EmployeeID**269) et **John** est le supérieur de l’assistante marketing**Mary** ( **EmployeeID**272).  
  
### <a name="to-insert-the-root-of-the-hierarchy-tree"></a>Pour insérer la racine de la structure hiérarchique  
  
1.  L’exemple suivant permet d’insérer **David** (directeur du marketing) à la table, à la racine de la structure hiérarchique. La colonne **OrdLevel** est une colonne calculée. Par conséquent, elle ne fait pas partie de l'instruction INSERT. La méthode [GetRoot()](/sql/t-sql/data-types/getroot-database-engine) est utilisée pour remplir ce premier enregistrement en tant que racine de la structure hiérarchique.  
  
    ```  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES (hierarchyid::GetRoot(), 6, 'David', 'Marketing Manager') ;  
    GO  
    ```  
  
2.  Exécutez le code suivant pour examiner la ligne initiale de la table :  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    ```  
  
 Comme dans la leçon précédente, nous allons utiliser la méthode `ToString()` pour convertir le type de données `hierarchyid` dans un format plus compréhensible.  
  
### <a name="to-insert-a-subordinate-employee"></a>Pour insérer un employé subordonné  
  
1.  **David** est le supérieur de **Sariya**. Pour insérer le nœud **de Sariya** , vous devez créer une valeur **OrgNode** appropriée de type `hierarchyid`de données. Le code suivant permet de créer une variable de type de données `hierarchyid` et de la remplir avec la valeur racine OrgNode de la table. Il utilise ensuite cette variable avec la méthode [GetDescendant()](/sql/t-sql/data-types/getdescendant-database-engine) pour insérer une ligne qui est un nœud subordonné. `GetDescendant` nécessite deux arguments. Vérifiez les valeurs d'argument des options suivantes :  
  
    -   Si parent est NULL, `GetDescendant` retourne NULL.  
  
    -   Si parent n'est pas NULL et que enfant1 et enfant2 sont NULL, `GetDescendant` retourne un enfant de parent.  
  
    -   Si parent et enfant1 ne sont pas NULL et que enfant2 est NULL, `GetDescendant` retourne un enfant de parent supérieur à enfant1.  
  
    -   Si parent et enfant2 ne sont pas NULL et que enfant1 est NULL, `GetDescendant` retourne un enfant de parent inférieur à enfant2.  
  
    -   Si parent, enfant1 et enfant 2 ne sont pas NULL, `GetDescendant` retourne un enfant de parent supérieur à enfant1 et inférieur à enfant2.  
  
     Le code suivant utilise les arguments `(NULL, NULL)` du parent racine parce qu'il n'y pas encore de ligne dans la table, à l'exception de la racine. Exécutez le code suivant pour insérer **Sariya**:  
  
    ```  
    DECLARE @Manager hierarchyid   
    SELECT @Manager = hierarchyid::GetRoot()  
    FROM HumanResources.EmployeeOrg ;  
  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES  
    (@Manager.GetDescendant(NULL, NULL), 46, 'Sariya', 'Marketing Specialist') ;  
  
    ```  
  
2.  Répétez la requête à partir de la première procédure pour interroger la table et voir comment les entrées apparaissent :  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    ```  
  
### <a name="to-create-a-procedure-for-entering-new-nodes"></a>Pour créer une procédure afin d'entrer de nouveaux nœuds  
  
1.  Pour simplifier l’entrée des données, créez la procédure stockée suivante pour ajouter des employés à la table **EmployeeOrg** . La procédure accepte les valeurs d'entrée relatives à l'employé ajouté. Cela inclut **l’EmployeeID** du directeur du nouvel employé, le numéro **d’EmployeeID** du nouvel employé ainsi que leurs prénoms et titres respectifs. La procédure utilise `GetDescendant()` ainsi que la méthode [GetAncestor()](/sql/t-sql/data-types/getancestor-database-engine) . Exécutez le code suivant pour créer la procédure :  
  
    ```  
    CREATE PROC AddEmp(@mgrid int, @empid int, @e_name varchar(20), @title varchar(20))   
    AS   
    BEGIN  
       DECLARE @mOrgNode hierarchyid, @lc hierarchyid  
       SELECT @mOrgNode = OrgNode   
       FROM HumanResources.EmployeeOrg   
       WHERE EmployeeID = @mgrid  
       SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
       BEGIN TRANSACTION  
          SELECT @lc = max(OrgNode)   
          FROM HumanResources.EmployeeOrg   
          WHERE OrgNode.GetAncestor(1) =@mOrgNode ;  
  
          INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
          VALUES(@mOrgNode.GetDescendant(@lc, NULL), @empid, @e_name, @title)  
       COMMIT  
    END ;  
    GO  
    ```  
  
2.  L’exemple suivant permet d’ajouter les 4 employés restants dont **David**est le supérieur direct ou indirect.  
  
    ```  
    EXEC AddEmp 6, 271, 'John', 'Marketing Specialist' ;  
    EXEC AddEmp 6, 119, 'Jill', 'Marketing Specialist' ;  
    EXEC AddEmp 46, 269, 'Wanida', 'Marketing Assistant' ;  
    EXEC AddEmp 271, 272, 'Mary', 'Marketing Assistant' ;  
    ```  
  
3.  Réexécutez la requête suivante pour vérifier les lignes de la table **EmployeeOrg** :  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    /1/1/        0x5AC0  2        269        Wanida  Marketing Assistant  
    /2/          0x68    1        271        John    Marketing Specialist  
    /2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
    /3/          0x78    1        119        Jill    Marketing Specialist  
    ```  
  
 La table est maintenant complètement remplie avec l'organisation du service Marketing.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Interrogation d'une table hiérarchique à l'aide de méthodes hiérarchiques](lesson-2-3-querying-a-hierarchical-table-using-hierarchy-methods.md)  
  
  
