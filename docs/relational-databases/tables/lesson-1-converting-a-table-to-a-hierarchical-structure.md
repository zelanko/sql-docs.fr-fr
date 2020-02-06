---
title: 'Leçon 1 : Conversion d’une table en structure hiérarchique | Microsoft Docs'
ms.custom: ''
ms.date: 08/22/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 05906db66c2bf4948e91dddafa2cdd54aaf936ec
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "72907296"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a>Leçon 1 : Conversion d'une table en structure hiérarchique
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
Les clients qui ont des tables utilisant des jointures réflexives pour exprimer des relations hiérarchiques peuvent convertir leurs tables en structure hiérarchique en suivant les procédures fournies dans cette leçon. Il est relativement facile d'effectuer une migration de cette représentation vers une autre à l'aide de **hierarchyid**. Après la migration, les utilisateurs disposeront d'une représentation hiérarchique compacte et facile à comprendre, qui peut être indexée de plusieurs façons pour que les requêtes soient efficaces.  
  
Cette leçon examine une table existante, crée une table contenant une colonne **hierarchyid** , remplit la table avec les données de la table source, puis illustre trois stratégies d'indexation. Cette leçon contient les rubriques suivantes :  
 
  
## <a name="prerequisites"></a>Conditions préalables requises  
Pour suivre ce tutoriel, vous avez besoin de SQL Server Management Studio, de l’accès à un serveur qui exécute SQL Server et d’une base de données AdventureWorks.

- Installez [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installez [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Téléchargez les [exemples de bases de données AdventureWorks2017](https://docs.microsoft.com/sql/samples/adventureworks-install-configure).

Les instructions de restauration des bases de données dans SSMS se trouvent ici : [Restaurer une base de données](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).  

## <a name="examine-the-current-structure-of-the-employee-table"></a>Étudier la structure actuelle de la table Employee
L’exemple de base de données Adventureworks2017 (ou ultérieur) contient une table **Employee** dans le schéma **HumanResources**. Afin d'éviter de modifier la table d'origine, cette étape effectue une copie de la table **Employee** , nommée **EmployeeDemo**. Pour simplifier l'exemple, vous ne copiez que cinq colonnes de la table d'origine. Vous interrogez ensuite la table **HumanResources.EmployeeDemo** pour vérifier comment sont structurées les données dans une table sans utiliser le type de données **hierarchyid** .  
  
### <a name="copy-the-employee-table"></a>Copier la table Employee  
  
1.  Dans une fenêtre de l'Éditeur de requête, exécutez le code suivant pour copier la structure et les données de la table **Employee** dans une nouvelle table nommée **EmployeeDemo**. Étant donné que la table d’origine utilise déjà hierarchyid, cette requête aplatit essentiellement la hiérarchie pour obtenir le nom du responsable de l’employé. Dans les parties suivantes de cette leçon, nous reconstruirons cette hiérarchie.

   ```sql  
   USE AdventureWorks2017;  
   GO  
     if OBJECT_ID('HumanResources.EmployeeDemo') is not null
    drop table HumanResources.EmployeeDemo 

    SELECT emp.BusinessEntityID AS EmployeeID, emp.LoginID, 
     (SELECT  man.BusinessEntityID FROM HumanResources.Employee man 
        WHERE emp.OrganizationNode.GetAncestor(1)=man.OrganizationNode OR 
            (emp.OrganizationNode.GetAncestor(1) = 0x AND man.OrganizationNode IS NULL)) AS ManagerID,
          emp.JobTitle, emp.HireDate
   INTO HumanResources.EmployeeDemo   
   FROM HumanResources.Employee emp ;
   GO
   ```  
  
### <a name="examine-the-structure-and-data-of-the-employeedemo-table"></a>Examiner la structure et les données de la table EmployeeDemo  
  
-   Cette nouvelle table **EmployeeDemo** représente une table classique dans une base de données existante que vous pouvez souhaiter migrer vers une nouvelle structure. Dans une fenêtre de l'Éditeur de requête, exécutez le code suivant pour voir comment la table utilise une jointure réflexive pour afficher les relations employé/responsable :  
  
    ```sql  
    SELECT   
        Mgr.EmployeeID AS MgrID, Mgr.LoginID AS Manager,   
        Emp.EmployeeID AS E_ID, Emp.LoginID, Emp.JobTitle  
    FROM HumanResources.EmployeeDemo AS Emp  
    LEFT JOIN HumanResources.EmployeeDemo AS Mgr  
    ON Emp.ManagerID = Mgr.EmployeeID  
    ORDER BY MgrID, E_ID  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    MgrID Manager                 E_ID LoginID                  JobTitle  
    NULL    NULL                    1   adventure-works\ken0        Chief Executive Officer
    1   adventure-works\ken0        2   adventure-works\terri0      Vice President of Engineering
    1   adventure-works\ken0       16   adventure-works\david0    Marketing Manager
    1   adventure-works\ken0       25   adventure-works\james1    Vice President of Production
    1   adventure-works\ken0      234   adventure-works\laura1    Chief Financial Officer
    1   adventure-works\ken0    263 adventure-works\jean0       Information Services Manager
    1   adventure-works\ken0      273   adventure-works\brian3    Vice President of Sales
    2   adventure-works\terri0    3 adventure-works\roberto0    Engineering Manager
    3   adventure-works\roberto0    4   adventure-works\rob0        Senior Tool Designer
    ...  
    ```  
  
    Les résultats se poursuivent pour un total de 290 lignes.  
  
Notez que le résultat de la clause **ORDER BY** a provoqué le regroupement des subordonnés directs de chaque niveau de gestion. Par exemple, les sept subordonnés directs de **MgrID** 1 (ken0) sont regroupés les uns à côté des autres. Il est possible, mais beaucoup plus difficile, de regrouper tous ceux dont **MgrID** 1 est le supérieur final.  


## <a name="populate-a-table-with-existing-hierarchical-data"></a>Remplir une table avec des données hiérarchiques existantes
Cette tâche crée une table et la remplit avec les données de la table **EmployeeDemo** . Les étapes de cette tâche sont les suivantes :  
  
-   Créez une table qui contient une colonne **hierarchyid** . Cette colonne pourrait remplacer les colonnes **EmployeeID** et **ManagerID** existantes. Toutefois, vous conserverez ces colonnes. Cela s'explique par le fait que les applications existantes peuvent faire référence à ces colonnes. De même, cela peut vous aider à comprendre les données après le transfert. La définition de table spécifie que **OrgNode** est la clé primaire, ce qui exige que la colonne contienne des valeurs uniques. L’index cluster sur la colonne **OrgNode** stockera la date dans la séquence **OrgNode** .    
-   Créez une table temporaire utilisée pour effectuer le suivi du nombre d'employés dont chaque responsable est le supérieur direct. 
-   Remplissez la nouvelle table en utilisant les données de la table **EmployeeDemo** .  
  
### <a name="to-create-a-new-table-named-neworg"></a>Pour créer une table nommée NewOrg  
  
-   Dans une fenêtre de l’Éditeur de requête, exécutez le code suivant pour créer une table nommée **HumanResources.NewOrg**:  
  
    ```sql   
    CREATE TABLE HumanResources.NewOrg  
    (  
      OrgNode hierarchyid,  
      EmployeeID int,  
      LoginID nvarchar(50),  
      ManagerID int  
    CONSTRAINT PK_NewOrg_OrgNode  
      PRIMARY KEY CLUSTERED (OrgNode)  
    );  
    GO  
    ```  
  
### <a name="create-a-temporary-table-named-children"></a>Créer une table temporaire nommée #Children  
  
1.  Créez une table temporaire nommée **#Children** avec une colonne nommée **Num** qui contiendra le nombre d’enfants pour chaque nœud :  
  
    ```sql  
    CREATE TABLE #Children   
       (  
        EmployeeID int,  
        ManagerID int,  
        Num int  
    );  
    GO  
    ```  
  
2.  Ajoutez un index qui accélérera considérablement la requête qui remplit la table **NewOrg** :  
  
    ```sql  
    CREATE CLUSTERED INDEX tmpind ON #Children(ManagerID, EmployeeID);  
    GO  
    ```  
  
### <a name="populate-the-neworg-table"></a>Remplir la table NewOrg  
  
1.  Les requêtes récursives interdisent les sous-requêtes avec agrégats. À la place, remplissez la table **#Children** avec le code suivant, qui utilise la méthode [ROW_NUMBER()](../../t-sql/functions/row-number-transact-sql.md) pour remplir la colonne **Num** :  
  
    ```sql 
    INSERT #Children (EmployeeID, ManagerID, Num)  
    SELECT EmployeeID, ManagerID,  
      ROW_NUMBER() OVER (PARTITION BY ManagerID ORDER BY ManagerID)   
    FROM HumanResources.EmployeeDemo  
    GO 
    ```  
  
2.  Examinez la table **#Children** . Notez la façon dont la colonne **Num** contient des numéros séquentiels pour chaque responsable.  
  
    ```sql  
    SELECT * FROM #Children ORDER BY ManagerID, Num  
    GO  
  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

    ```
    EmployeeID  ManagerID   Num
    1   NULL    1
    2        1    1
    16     1      2
    25     1      3
    234    1      4
    263    1      5
    273    1      6
    3        2    1
    4        3    1
    5        3    2
    6        3    3
    7        3    4
    ```


3.  Remplissez la table **NewOrg** . Utilisez les méthodes GetRoot et ToString pour concaténer les valeurs **Num** au format **hierarchyid** , puis mettez à jour la colonne **OrgNode** avec les valeurs hiérarchiques résultantes :  
  
    ```sql  
    WITH paths(path, EmployeeID)   
    AS (  
    -- This section provides the value for the root of the hierarchy  
    SELECT hierarchyid::GetRoot() AS OrgNode, EmployeeID   
    FROM #Children AS C   
    WHERE ManagerID IS NULL   

    UNION ALL   
    -- This section provides values for all nodes except the root  
    SELECT   
    CAST(p.path.ToString() + CAST(C.Num AS varchar(30)) + '/' AS hierarchyid),   
    C.EmployeeID  
    FROM #Children AS C   
    JOIN paths AS p   
       ON C.ManagerID = P.EmployeeID   
    )  
    INSERT HumanResources.NewOrg (OrgNode, O.EmployeeID, O.LoginID, O.ManagerID)  
    SELECT P.path, O.EmployeeID, O.LoginID, O.ManagerID  
    FROM HumanResources.EmployeeDemo AS O   
    JOIN Paths AS P   
       ON O.EmployeeID = P.EmployeeID  
    GO 
    ```  
  
4.  Une colonne **hierarchyid** est plus compréhensible quand vous la convertissez au format caractère. Vérifiez les données de la table **NewOrg** en exécutant le code suivant, qui contient deux représentations de la colonne **OrgNode** :  
  
    ```sql  
    SELECT OrgNode.ToString() AS LogicalNode, *   
    FROM HumanResources.NewOrg   
    ORDER BY LogicalNode;  
    GO  
    ```  
  
    La colonne **LogicalNode** convertit la colonne **hierarchyid** en format texte plus lisible qui représente la hiérarchie. Dans les tâches restantes, vous utiliserez la méthode `ToString()` pour afficher le format logique des colonnes **hierarchyid** .  
  
5.  Supprimez la table temporaire, qui n'est plus nécessaire :  
  
    ```sql  
    DROP TABLE #Children  
    GO  
    ```  
  
## <a name="optimizing-the-neworg-table"></a>Optimisation de la table NewOrg
La table **NewOrd** que vous avez créée dans la tâche [Remplissage d’une table avec des données hiérarchiques existantes](../../relational-databases/tables/lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) contient toutes les informations relatives aux employés et représente la structure hiérarchique à l’aide d’un type de données **hierarchyid** . Cette tâche ajoute de nouveaux index pour prendre en charge les recherches sur la colonne **hierarchyid** .  
  

La colonne **hierarchyid** (**OrgNode**) est la clé primaire de la table **NewOrg** . Quand la table a été créée, elle contenait un index cluster nommé **PK_NewOrg_OrgNode** pour forcer l’unicité de la colonne **OrgNode** . Cet index cluster prend également en charge une recherche à profondeur prioritaire de la table.  
  
  
### <a name="create-index-on-neworg-table-for-efficient-searches"></a>Créer un index sur la table NewOrg pour des recherches efficaces  
  
1.  Pour faciliter les requêtes au même niveau de la hiérarchie, utilisez la méthode [GetLevel](../../t-sql/data-types/getlevel-database-engine.md) pour créer une colonne calculée qui contient le niveau dans la hiérarchie. Créez ensuite un index composite sur le niveau et **Hierarchyid**. Exécutez le code suivant pour créer la colonne calculée et l'index à largeur prioritaire :  
  
    ```sql  
    ALTER TABLE HumanResources.NewOrg   
       ADD H_Level AS OrgNode.GetLevel() ;  
    CREATE UNIQUE INDEX EmpBFInd   
       ON HumanResources.NewOrg(H_Level, OrgNode) ;  
    GO  
    ```  
  
2.  Créez un index unique sur la colonne **EmployeeID** . Il s’agit de la recherche singleton classique d’un seul employé par numéro **EmployeeID** . Exécutez le code suivant pour créer un index sur **EmployeeID**:  
  
    ```sql  
    CREATE UNIQUE INDEX EmpIDs_unq ON HumanResources.NewOrg(EmployeeID) ;  
    GO
    ```  
  
3.  Exécutez le code suivant pour récupérer des données de la table dans l'ordre de chacun des trois index :  
  
    ```sql  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID  
    FROM HumanResources.NewOrg   
    ORDER BY OrgNode;  

    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM HumanResources.NewOrg   
    ORDER BY H_Level, OrgNode;  

    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM HumanResources.NewOrg   
    ORDER BY EmployeeID;  
    GO  
    ```  
  
4.  Comparez les jeux de résultats pour voir comment l'ordre est stocké dans chaque type d'index. Seules les quatre premières lignes de chaque de sortie suivent.  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    Index à profondeur prioritaire : les enregistrements d'employés sont stockés à proximité de leur responsable.  

    ```
    LogicalNode OrgNode H_Level EmployeeID  LoginID
    /   0x  0   1   adventure-works\ken0
    /1/ 0x58    1   2   adventure-works\terri0
    /1/1/   0x5AC0  2   3   adventure-works\roberto0
    /1/1/1/ 0x5AD6  3   4   adventure-works\rob0
    /1/1/2/ 0x5ADA  3   5   adventure-works\gail0
    /1/1/3/ 0x5ADE  3   6   adventure-works\jossef0
    /1/1/4/ 0x5AE1  3   7   adventure-works\dylan0
    /1/1/4/1/   0x5AE158    4   8   adventure-works\diane1
    /1/1/4/2/   0x5AE168    4   9   adventure-works\gigi0
    /1/1/4/3/   0x5AE178    4   10  adventure-works\michael6
    /1/1/5/ 0x5AE3  3   11  adventure-works\ovidiu0
    ```

    Index avec**EmployeeID**prioritaire : les lignes sont stockées dans l’ordre des **EmployeeID** .  

    ```
    LogicalNode OrgNode H_Level EmployeeID  LoginID
    /   0x  0   1   adventure-works\ken0
    /1/ 0x58    1   2   adventure-works\terri0
    /1/1/   0x5AC0  2   3   adventure-works\roberto0
    /1/1/1/ 0x5AD6  3   4   adventure-works\rob0
    /1/1/2/ 0x5ADA  3   5   adventure-works\gail0
    /1/1/3/ 0x5ADE  3   6   adventure-works\jossef0
    /1/1/4/ 0x5AE1  3   7   adventure-works\dylan0
    /1/1/4/1/   0x5AE158    4   8   adventure-works\diane1
    /1/1/4/2/   0x5AE168    4   9   adventure-works\gigi0
    /1/1/4/3/   0x5AE178    4   10  adventure-works\michael6
    /1/1/5/ 0x5AE3  3   11  adventure-works\ovidiu0
    /1/1/5/1/   0x5AE358    4   12  adventure-works\thierry0
    ```
  
> [!NOTE]  
> Pour les diagrammes qui affichent la différence entre un index à profondeur prioritaire et un index à largeur prioritaire, consultez [Données hiérarchiques &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md).  
  
### <a name="drop-the-unnecessary-columns"></a>Supprimer les colonnes inutiles  
  
1.  La colonne **ManagerID** représente la relation employé/responsable, qui est maintenant représentée par la colonne **OrgNode** . Si les autres applications n’ont pas besoin de la colonne **ManagerID** , vous pouvez envisager de la supprimer à l’aide de l’instruction suivante :  
  
    ```sql  
    ALTER TABLE HumanResources.NewOrg DROP COLUMN ManagerID ;  
    GO  
    ```  
  
2.  La colonne **EmployeeID** est également redondante. La colonne **OrgNode** identifie chaque employé de façon univoque. Si les autres applications n’ont pas besoin de la colonne **EmployeeID** , vous pouvez envisager de supprimer l’index puis la colonne, en utilisant le code suivant :  
  
    ```sql  
    DROP INDEX EmpIDs_unq ON HumanResources.NewOrg ;  
    ALTER TABLE HumanResources.NewOrg DROP COLUMN EmployeeID ;  
    GO  
    ```  
  
### <a name="replace-the-original-table-with-the-new-table"></a>Remplacer la table d’origine par la nouvelle table  
  
1.  Si votre table d’origine contenait des index ou contraintes supplémentaires, ajoutez-les à la table **NewOrg** .  
  
2.  Remplacez l’ancienne table **EmployeeDemo** par la nouvelle table. Exécutez le code suivant pour supprimer l'ancienne table, puis renommez la nouvelle table avec l'ancien nom :  
  
    ```sql  
    DROP TABLE HumanResources.EmployeeDemo ;  
    GO  
    sp_rename 'HumanResources.NewOrg', 'EmployeeDemo' ;  
    GO  
    ```  
  
3.  Exécutez le code suivant pour examiner la table finale :  
  
    ```sql  
    SELECT * FROM HumanResources.EmployeeDemo ;  
    ```  
  
## <a name="next-steps"></a>Étapes suivantes
L’article suivant vous apprend à créer et gérer des données dans une table hiérarchique. 

Passez à l’article suivant pour en savoir plus :
> [!div class="nextstepaction"]
> [Étapes suivantes](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)
