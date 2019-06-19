---
title: Optimisation de la table NewOrg | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- optimizing tables
ms.assetid: 89ff6d37-94c0-4773-8be9-dde943fff023
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 952043d5d001fe4fe65e6dd1aa7bb2001290429e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66110070"
---
# <a name="optimizing-the-neworg-table"></a>Optimisation de la table NewOrg
  Le **NewOrd** table que vous avez créé dans le [remplissage d’une Table avec des données hiérarchiques existantes](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) tâche contient toutes les informations des employés et représente la structure hiérarchique à l’aide d’un `hierarchyid`type de données. Cette tâche ajoute de nouveaux index pour prendre en charge les recherches sur la colonne `hierarchyid`.  
  
## <a name="clustered-index"></a>Index cluster  
 Le `hierarchyid` colonne (**OrgNode**) est la clé primaire pour la **NewOrg** table. Quand la table a été créée, elle contenait un index cluster nommé **PK_NewOrg_OrgNode** pour forcer l’unicité de la colonne **OrgNode** . Cet index cluster prend également en charge une recherche à profondeur prioritaire de la table.  
  
## <a name="nonclustered-index"></a>Index non cluster  
 Cette étape crée deux index non cluster pour prendre en charge des recherches typiques.  
  
#### <a name="to-index-the-neworg-table-for-efficient-searches"></a>Pour indexer la table NewOrg en vue d'effectuer recherches efficaces  
  
1.  Pour faciliter les requêtes au même niveau de la hiérarchie, utilisez la méthode [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) pour créer une colonne calculée qui contient le niveau dans la hiérarchie. Créez ensuite un index composite sur le niveau et `Hierarchyid`. Exécutez le code suivant pour créer la colonne calculée et l'index à largeur prioritaire :  
  
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
  
     Index à profondeur prioritaire : Enregistrements d’employés sont stockés adjacente à son responsable.  
  
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
  
     **EmployeeID**-tout d’abord d’index : Lignes sont stockées dans **EmployeeID** séquence.  
  
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
>  Pour les diagrammes qui affichent la différence entre un index à profondeur prioritaire et un index à largeur prioritaire, consultez [Données hiérarchiques &#40;SQL Server&#41;](../hierarchical-data-sql-server.md).  
  
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
 [Résumé : Conversion d’une Table en une Structure hiérarchique](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
  
