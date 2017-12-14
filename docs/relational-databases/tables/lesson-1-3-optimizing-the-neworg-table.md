---
title: Optimisation de la table NewOrg | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: optimizing tables
ms.assetid: 89ff6d37-94c0-4773-8be9-dde943fff023
caps.latest.revision: "23"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1bef7b50cb8f67baeca6e17c9406fc542a8e73fd
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-1-3---optimizing-the-neworg-table"></a>Leçon 1-3 : Optimisation de la table NewOrg
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)] La table **NewOrd** que vous avez créée dans la tâche [Remplissage d’une table avec des données hiérarchiques existantes](../../relational-databases/tables/lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) contient toutes les informations relatives aux employés et représente la structure hiérarchique à l’aide d’un type de données **hierarchyid**. Cette tâche ajoute de nouveaux index pour prendre en charge les recherches sur la colonne **hierarchyid** .  
  
## <a name="clustered-index"></a>Index cluster  
La colonne **hierarchyid** (**OrgNode**) est la clé primaire de la table **NewOrg** . Quand la table a été créée, elle contenait un index cluster nommé **PK_NewOrg_OrgNode** pour forcer l’unicité de la colonne **OrgNode** . Cet index cluster prend également en charge une recherche à profondeur prioritaire de la table.  
  
## <a name="nonclustered-index"></a>Index non cluster  
Cette étape crée deux index non cluster pour prendre en charge des recherches typiques.  
  
#### <a name="to-index-the-neworg-table-for-efficient-searches"></a>Pour indexer la table NewOrg en vue d'effectuer recherches efficaces  
  
1.  Pour faciliter les requêtes au même niveau de la hiérarchie, utilisez la méthode [GetLevel](../../t-sql/data-types/getlevel-database-engine.md) pour créer une colonne calculée qui contient le niveau dans la hiérarchie. Créez ensuite un index composite sur le niveau et **Hierarchyid**. Exécutez le code suivant pour créer la colonne calculée et l'index à largeur prioritaire :  
  
    ```  
    ALTER TABLE NewOrg   
       ADD H_Level AS OrgNode.GetLevel() ;  
    CREATE UNIQUE INDEX EmpBFInd   
       ON NewOrg(H_Level, OrgNode) ;  
    GO  
    ```  
  
2.  Créez un index unique sur la colonne **EmployeeID** . Il s’agit de la recherche singleton classique d’un seul employé par numéro **EmployeeID** . Exécutez le code suivant pour créer un index sur **EmployeeID**:  
  
    ```  
    CREATE UNIQUE INDEX EmpIDs_unq ON NewOrg(EmployeeID) ;  
    GO  
    ```  
  
3.  Exécutez le code suivant pour récupérer des données de la table dans l'ordre de chacun des trois index :  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID  
    FROM NewOrg   
    ORDER BY OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY H_Level, OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY EmployeeID;  
    GO  
    ```  
  
4.  Comparez les jeux de résultats pour voir comment l'ordre est stocké dans chaque type d'index. Seules les quatre premières lignes de chaque de sortie suivent.  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    Index à profondeur prioritaire : les enregistrements d'employés sont stockés à proximité de leur responsable.  
  
    `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
    `/             0x         0         1      zarifin`  
  
    `/1/          0x58        1         2      tplate`  
  
    `/1/1/       0x5AC0       2         4      schai`  
  
    `/1/1/1/     0x5AD6       3         9      jwang`  
  
    `/1/1/2/     0x5ADA       3        10      malexander`  
  
    `/1/2/       0x5B40       2         5      elang`  
  
    `/1/3/       0x5BC0       2         6      gsmits`  
  
    `/2/         0x68         1         3      hjensen`  
  
    `/2/1/       0x6AC0       2         7      sdavis`  
  
    `/2/2/       0x6B40       2         8      norint`  
  
    Index avec **EmployeeID** prioritaire : les lignes sont stockées dans l’ordre des **EmployeeID**.  
  
    `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
    `/             0x         0         1      zarifin`  
  
    `/1/          0x58        1         2      tplate`  
  
    `/2/         0x68         1         3      hjensen`  
  
    `/1/1/       0x5AC0       2         4      schai`  
  
    `/1/2/       0x5B40       2         5      elang`  
  
    `/1/3/       0x5BC0       2         6      gsmits`  
  
    `/2/1/       0x6AC0       2         7      sdavis`  
  
    `/2/2/       0x6B40       2         8      norint`  
  
    `/1/1/1/     0x5AD6       3         9      jwang`  
  
    `/1/1/2/     0x5ADA       3        10      malexander`  
  
> [!NOTE]  
> Pour les diagrammes qui affichent la différence entre un index à profondeur prioritaire et un index à largeur prioritaire, consultez [Données hiérarchiques &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md).  
  
#### <a name="to-drop-the-unnecessary-columns"></a>Pour supprimer les colonnes inutiles  
  
1.  La colonne **ManagerID** représente la relation employé/responsable, qui est maintenant représentée par la colonne **OrgNode** . Si les autres applications n’ont pas besoin de la colonne **ManagerID** , vous pouvez envisager de la supprimer à l’aide de l’instruction suivante :  
  
    ```  
    ALTER TABLE NewOrg DROP COLUMN ManagerID ;  
    GO  
    ```  
  
2.  La colonne **EmployeeID** est également redondante. La colonne **OrgNode** identifie chaque employé de façon univoque. Si les autres applications n’ont pas besoin de la colonne **EmployeeID** , vous pouvez envisager de supprimer l’index puis la colonne, en utilisant le code suivant :  
  
    ```  
    DROP INDEX EmpIDs_unq ON NewOrg ;  
    ALTER TABLE NewOrg DROP COLUMN EmployeeID ;  
    GO  
    ```  
  
#### <a name="to-replace-the-original-table-with-the-new-table"></a>Pour remplacer la table d'origine par la nouvelle table  
  
1.  Si votre table d’origine contenait des index ou contraintes supplémentaires, ajoutez-les à la table **NewOrg** .  
  
2.  Remplacez l’ancienne table **EmployeeDemo** par la nouvelle table. Exécutez le code suivant pour supprimer l'ancienne table, puis renommez la nouvelle table avec l'ancien nom :  
  
    ```  
    DROP TABLE EmployeeDemo ;  
    GO  
    sp_rename 'NewOrg', EmployeeDemo ;  
    GO  
    ```  
  
3.  Exécutez le code suivant pour examiner la table finale :  
  
    ```  
    SELECT * FROM EmployeeDemo ;  
    ```  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
[Résumé : Conversion d'une table en une structure hiérarchique](../../relational-databases/tables/lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
  
  
