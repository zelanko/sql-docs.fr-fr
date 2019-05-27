---
title: Réorganisation de données dans une table hiérarchique à l’aide de méthodes hiérarchiques | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 7b8064c7-62c6-488d-84d2-57a5828fb907
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5f289257d64a691a93d44d63d2a30991227802e1
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66110109"
---
# <a name="reordering-data-in-a-hierarchical-table-using-hierarchical-methods"></a>Réorganisation de données dans une table hiérarchique à l'aide de méthodes hiérarchiques
  La réorganisation d'une hiérarchie est une tâche de maintenance courante. Dans cette tâche, nous utiliserons une instruction UPDATE avec la méthode [GetReparentedValue](/sql/t-sql/data-types/getreparentedvalue-database-engine) pour déplacer en premier lieu une seule ligne vers un nouvel emplacement dans la hiérarchie. Puis, nous déplacerons la totalité d'une sous-arborescence vers un nouvel emplacement.  
  
 La méthode `GetReparentedValue` accepte deux arguments. Le premier argument décrit la partie de la hiérarchie à modifier. Par exemple, si une hiérarchie est **/1/4/2/3/** et que vous souhaitez modifier la section **/1/4/** , la hiérarchie devient **/2/1/2/3/**, laissant les deux derniers nœuds (**2/3 /**) inchangés. Les nœuds à modifier (**/1/4/**) doivent être spécifiés comme premier argument. Le deuxième argument fournit le nouveau niveau de hiérarchie, dans notre exemple **/2/1/**. Les deux arguments ne doivent pas nécessairement contenir le même nombre de niveaux.  
  
### <a name="to-move-a-single-row-to-a-new-location-in-the-hierarchy"></a>Pour déplacer une ligne unique vers un nouvel emplacement dans la hiérarchie  
  
1.  Sariya est actuellement la supérieure de Wanida. Dans cette procédure, vous déplacez Wanida du nœud **/1/1/,** où elle se trouve actuellement, pour que Jill soit sa supérieure. Son nouveau nœud deviendra ainsi **/3/1/** . **/1/** sera donc le premier argument et **/3/** le second. Ceux-ci correspondent aux valeurs **OrgNode** de Sariya et de Jill. Exécutez le code suivant pour déplacer Wanida de l'organisation de Sariya vers celle de Jill :  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 269 ;   
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 46 ;   
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 119 ;   
  
    UPDATE HumanResources.EmployeeOrg  
    SET OrgNode = @CurrentEmployee. GetReparentedValue(@OldParent, @NewParent)   
    WHERE OrgNode = @CurrentEmployee ;  
    GO  
    ```  
  
2.  Exécutez le code suivant pour afficher le résultat :  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
     Wanida se trouve maintenant au nœud **/3/1/**.  
  
### <a name="to-reorganize-a-section-of-a-hierarchy"></a>Pour réorganiser une section d'une hiérarchie  
  
1.  Pour montrer comment déplacer simultanément un plus grand nombre de personnes, exécutez d'abord le code suivant pour ajouter un subalterne interne à Wanida :  
  
    ```  
    EXEC AddEmp 269, 291, 'Kevin', 'Marketing Intern'  ;  
    GO  
    ```  
  
2.  Kevin est désormais le subalterne de Wanida, elle-même subalterne de Jill, elle-même subalterne de David. Cela signifie que Kevin est au niveau **/3/1/1/**. Pour déplacer tous les subalternes de Jill vers un nouveau responsable, nous allons mettre à jour tous les nœuds qui ont **/3/** comme valeur **OrgNode** vers une nouvelle valeur. Exécutez le code suivant pour mettre à jour Wanida de sorte que Sariya soit sa supérieure, en conservant Kevin comme subalterne de Wanida :  
  
    ```  
    DECLARE @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 119 ; -- Jill  
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ; -- Sariya  
    DECLARE children_cursor CURSOR FOR  
    SELECT OrgNode FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @OldParent;  
    DECLARE @ChildId hierarchyid;  
    OPEN children_cursor  
    FETCH NEXT FROM children_cursor INTO @ChildId;  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
    START:  
        DECLARE @NewId hierarchyid;  
        SELECT @NewId = @NewParent.GetDescendant(MAX(OrgNode), NULL)  
        FROM HumanResources.EmployeeOrg WHERE OrgNode.GetAncestor(1) = @NewParent;  
  
        UPDATE HumanResources.EmployeeOrg  
        SET OrgNode = OrgNode.GetReparentedValue(@ChildId, @NewId)  
        WHERE OrgNode.IsDescendantOf(@ChildId) = 1;  
        IF @@error <> 0 GOTO START -- On error, retry  
            FETCH NEXT FROM children_cursor INTO @ChildId;  
    END  
    CLOSE children_cursor;  
    DEALLOCATE children_cursor;  
  
    ```  
  
3.  Exécutez le code suivant pour afficher le résultat :  
  
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
/1/1//2      0x5AD0  3        291        Kevin   Marketing Intern  
/2/          0x68    1        271        John    Marketing Specialist  
/2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
/3/          0x78    1        119        Jill    Marketing Specialist  
```  
  
 La totalité de l'arborescence de l'organisation dont Jill était la supérieure (Wanida et Kevin) a maintenant Sariya comme supérieure.  
  
 Pour obtenir une procédure stockée qui réorganise une section d’une hiérarchie, consultez la section « Déplacement de sous-arborescences » de [Déplacement de sous-arborescences](../hierarchical-data-sql-server.md#BKMK_MovingSubtrees).  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Résumé : La gestion des données dans une Table hiérarchique](lesson-2-5-summary-managing-data-in-a-hierarchical-table.md)  
  
  
