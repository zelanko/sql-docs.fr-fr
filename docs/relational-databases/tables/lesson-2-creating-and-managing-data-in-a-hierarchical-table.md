---
description: 'Leçon 2 : Création et gestion de données dans une table hiérarchique'
title: 'Leçon 2 : Création et gestion de données dans une table hiérarchique | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 95f55cff-4abb-4c08-97b3-e3ae5e8b24e2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0a774ce3918388e8df23de43a01b8b0930f9336d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460221"
---
# <a name="lesson-2-create-and-manage-data-in-a-hierarchical-table"></a>Leçon 2 : Créer et gérer des données dans une table hiérarchique
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
 Dans la leçon 1, vous avez modifié une table existante pour utiliser le type de données **hierarchyid** et vous avez rempli la colonne**hierarchyid** avec la représentation des données existantes. Dans cette leçon, vous allez utiliser les méthodes hiérarchiques pour créer une nouvelle table et y insérer des données. Puis, toujours à l'aide de méthodes hiérarchiques, vous interrogerez et manipulerez ces données. 

## <a name="prerequisites"></a>Prérequis  
Pour suivre ce tutoriel, vous avez besoin de SQL Server Management Studio, de l’accès à un serveur qui exécute SQL Server et d’une base de données AdventureWorks.

- Installez [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installez [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Téléchargez les [exemples de bases de données AdventureWorks2017](https://docs.microsoft.com/sql/samples/adventureworks-install-configure).

Les instructions de restauration de bases de données dans SSMS se trouvent ici : [Restaurer une base de données](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).   
  
## <a name="create-a-table-using-the-hierarchyid-data-type"></a>Créer une table à l’aide du type de données hierarchyid
L'exemple suivant crée une table nommée EmployeeOrg qui inclut des données sur les employés ainsi que leur hiérarchie de création de rapports. Cet exemple crée la table dans la base de données AdventureWorks2017, mais c’est facultatif. Pour que l'exemple reste simple, cette table ne comporte que cinq colonnes :  
  
-   OrgNode est une colonne **hierarchyid** qui stocke la relation hiérarchique.   
-   OrgLevel est une colonne calculée en fonction de la colonne OrgNode qui stocke chaque niveau de nœuds dans la hiérarchie. Elle sera utilisée pour un index à largeur prioritaire.  
-   EmployeeID contient le numéro d'identification d'employé qui est habituellement utilisé pour les applications telles que les salaires. Dans le nouveau développement d'applications, les applications peuvent utiliser la colonne OrgNode ; cette colonne EmployeeID séparée n'est donc pas nécessaire.   
-   EmpName contient le nom de l'employé.    
-   Titre contient le titre de l'employé.  

## <a name="create-the-employeeorg-table"></a>Créer la table EmployeeOrg  
  
1.  Dans une fenêtre de l'Éditeur de requête, exécutez le code suivant pour créer la table `EmployeeOrg` . Lorsque la colonne `OrgNode` est définie comme clé primaire avec un index cluster, un index à profondeur prioritaire est créé :  
  
    ```sql  
    USE AdventureWorks2017 ;  
    GO  
    
    if OBJECT_ID('HumanResources.EmployeeOrg') is not null
     drop table HumanResources.EmployeeOrg 
         
    CREATE TABLE HumanResources.EmployeeOrg  
    (  
       OrgNode hierarchyid PRIMARY KEY CLUSTERED,  
       OrgLevel AS OrgNode.GetLevel(),  
       EmployeeID int UNIQUE NOT NULL,  
       EmpName varchar(20) NOT NULL,  
       Title varchar(20) NULL  
    ) ;  
    GO  
    ```  
  
2.  Exécutez le code suivant pour créer un index composite sur les colonnes `OrgLevel` et `OrgNode` afin de prendre en charge des recherches à largeur prioritaire efficaces :  
  
    ```sql  
    CREATE UNIQUE INDEX EmployeeOrgNc1   
    ON HumanResources.EmployeeOrg(OrgLevel, OrgNode) ;  
    GO  
    ```  
  
La table est maintenant prête à recevoir les données. La tâche suivante remplira la table à l'aide de méthodes hiérarchiques.   

## <a name="populate-a-hierarchical-table-using-hierarchical-methods"></a>Remplir une table hiérarchique en utilisant des méthodes hiérarchiques
AdventureWorks2017 a 8 employés travaillant au service Marketing. La hiérarchie des employés se présente comme suit :  
  
**David**, **EmployeeID** 6, est le directeur du marketing. **David**est le supérieur de trois spécialistes en marketing :  
  
-   **Sariya**, **EmployeeID** 46  
  
-   **John**, **EmployeeID** 271  
  
-   **Jill**, **EmployeeID** 119  
  
**Sariya** est la supérieure de l’assistante marketing**Wanida** ( **EmployeeID**269) et **John** est le supérieur de l’assistante marketing**Mary** ( **EmployeeID**272).  
  
### <a name="insert-the-root-of-the-hierarchy-tree"></a>Insérer la racine de la structure hiérarchique  
  
1.  L’exemple suivant permet d’insérer **David** (directeur du marketing) à la table, à la racine de la structure hiérarchique. La colonne **OrdLevel** est une colonne calculée. Par conséquent, elle ne fait pas partie de l'instruction INSERT. La méthode [GetRoot()](../../t-sql/data-types/getroot-database-engine.md) est utilisée pour remplir ce premier enregistrement en tant que racine de la structure hiérarchique.  
  
    ```sql  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES (hierarchyid::GetRoot(), 6, 'David', 'Marketing Manager') ;  
    GO  
    ```  
  
2.  Exécutez le code suivant pour examiner la ligne initiale de la table :  
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```sql  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    ```  
  
Comme dans la leçon précédente, nous allons utiliser la méthode `ToString()` pour convertir le type de données **hierarchyid** dans un format plus compréhensible.  
  
### <a name="insert-a-subordinate-employee"></a>Insérer un employé subordonné  
  
1.  **David** est le supérieur de **Sariya**. Pour insérer le nœud de **Sariya** , vous devez créer une valeur **OrgNode** appropriée de type de données **hierarchyid**. Le code suivant permet de créer une variable de type de données **hierarchyid** et de la remplir avec la valeur racine OrgNode de la table. Il utilise ensuite cette variable avec la méthode [GetDescendant()](../../t-sql/data-types/getdescendant-database-engine.md) pour insérer une ligne qui est un nœud subordonné. `GetDescendant` nécessite deux arguments. Vérifiez les valeurs d'argument des options suivantes :  
  
    -   Si parent est NULL, `GetDescendant` retourne NULL.  
    -   Si parent n'est pas NULL et que enfant1 et enfant2 sont NULL, `GetDescendant` retourne un enfant de parent.  
    -   Si parent et enfant1 ne sont pas NULL et que enfant2 est NULL, `GetDescendant` retourne un enfant de parent supérieur à enfant1.   
    -   Si parent et enfant2 ne sont pas NULL et que enfant1 est NULL, `GetDescendant` retourne un enfant de parent inférieur à enfant2.   
    -   Si parent, enfant1 et enfant 2 ne sont pas NULL, `GetDescendant` retourne un enfant de parent supérieur à enfant1 et inférieur à enfant2.  
  
    Le code suivant utilise les arguments `(NULL, NULL)` du parent racine parce qu'il n'y pas encore de ligne dans la table, à l'exception de la racine. Exécutez le code suivant pour insérer **Sariya**:  
  
    ```sql  
    DECLARE @Manager hierarchyid   
    SELECT @Manager = hierarchyid::GetRoot()  
    FROM HumanResources.EmployeeOrg ;  
  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES  
    (@Manager.GetDescendant(NULL, NULL), 46, 'Sariya', 'Marketing Specialist') ;  
  
    ```  
  
2.  Répétez la requête à partir de la première procédure pour interroger la table et voir comment les entrées apparaissent :  
  
    ```sql  
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
  
### <a name="create-a-procedure-for-entering-new-nodes"></a>Créer une procédure pour entrer de nouveaux nœuds  
  
1.  Pour simplifier l’entrée des données, créez la procédure stockée suivante pour ajouter des employés à la table **EmployeeOrg** . La procédure accepte les valeurs d'entrée relatives à l'employé ajouté. Cela inclut **l’EmployeeID** du directeur du nouvel employé, le numéro **d’EmployeeID** du nouvel employé ainsi que leurs prénoms et titres respectifs. La procédure utilise `GetDescendant()` ainsi que la méthode [GetAncestor()](../../t-sql/data-types/getancestor-database-engine.md) . Exécutez le code suivant pour créer la procédure :  
  
    ```sql  
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
  
    ```sql  
    EXEC AddEmp 6, 271, 'John', 'Marketing Specialist' ;  
    EXEC AddEmp 6, 119, 'Jill', 'Marketing Specialist' ;  
    EXEC AddEmp 46, 269, 'Wanida', 'Marketing Assistant' ;  
    EXEC AddEmp 271, 272, 'Mary', 'Marketing Assistant' ;  
    ```  
  
3.  Réexécutez la requête suivante pour vérifier les lignes de la table **EmployeeOrg** :  
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```sql  
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

## <a name="query-a-hierarchical-table-using-hierarchy-methods"></a>Interroger une table hiérarchique à l’aide de méthodes hiérarchiques
Maintenant que la table HumanResources.EmployeeOrg est entièrement remplie, cette tâche vous indiquera comment interroger la hiérarchie à l'aide de certaines des méthodes hiérarchiques.  
  
### <a name="find-subordinate-nodes"></a>Rechercher des nœuds subordonnés  
  
1.  Sariya a un employé subordonné. Pour rechercher les subordonnés de Sariya, exécutez la requête suivante qui utilise la méthode [IsDescendantOf](../../t-sql/data-types/isdescendantof-database-engine.md) :  
  
    ```sql  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.IsDescendantOf(@CurrentEmployee ) = 1 ;  
    ```  
  
    Le résultat répertorie Sariya et Wanida. Sariya est répertoriée car elle est la descendante au niveau 0. Wanida est la descendante au niveau 1.  
  
2.  Vous pouvez également créer des requêtes sur ces informations à l’aide de la méthode [GetAncestor](../../t-sql/data-types/getancestor-database-engine.md) . `GetAncestor` prend un argument pour le niveau que vous tentez de retourner. Étant donné que Wanida est un niveau plus bas que Sariya, utilisez `GetAncestor(1)` comme indiqué dans le code suivant :  
  
    ```sql  
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
  
    ```sql  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 6 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(2) = @CurrentEmployee  
    ```  
  
    Cette fois-ci, le résultat répertorie également Mary, deux niveaux plus bas, dont David est également le supérieur.  
  
## <a name="use-getroot-and-getlevel"></a>Utiliser GetRoot et GetLevel  
  
1.  À mesure que la hiérarchie s'agrandit, il devient plus difficile de déterminer l'emplacement des membres dans la hiérarchie. La méthode [GetLevel](../../t-sql/data-types/getlevel-database-engine.md) permet de déterminer le nombre de niveaux sous chaque ligne dans la hiérarchie. Exécutez le code suivant pour consulter les niveaux de toutes les lignes :  
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode.GetLevel() AS EmpLevel, *  
    FROM HumanResources.EmployeeOrg ;  
    GO  
  
    ```  
  
2.  La méthode [GetRoot](../../t-sql/data-types/getroot-database-engine.md) permet de rechercher le nœud racine dans la hiérarchie. Le code suivant retourne la ligne unique qui est la racine :  
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode = hierarchyid::GetRoot() ;  
    GO  
  
    ```  
   
  
## <a name="reorder-data-in-a-hierarchical-table-using-hierarchical-methods"></a>Réorganiser des données dans une table hiérarchique à l'aide de méthodes hiérarchiques
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
La réorganisation d'une hiérarchie est une tâche de maintenance courante. Dans cette tâche, nous utiliserons une instruction UPDATE avec la méthode [GetReparentedValue](../../t-sql/data-types/getreparentedvalue-database-engine.md) pour déplacer en premier lieu une seule ligne vers un nouvel emplacement dans la hiérarchie. Puis, nous déplacerons la totalité d'une sous-arborescence vers un nouvel emplacement.  
  
La méthode `GetReparentedValue` accepte deux arguments. Le premier argument décrit la partie de la hiérarchie à modifier. Par exemple, si une hiérarchie est **/1/4/2/3/** et que vous souhaitez modifier la section **/1/4/** , la hiérarchie devient **/2/1/2/3/**, laissant les deux derniers nœuds (**2/3 /**) inchangés. Les nœuds à modifier (**/1/4/**) doivent être spécifiés comme premier argument. Le deuxième argument fournit le nouveau niveau de hiérarchie, dans notre exemple **/2/1/**. Les deux arguments ne doivent pas nécessairement contenir le même nombre de niveaux.  
  
### <a name="move-a-single-row-to-a-new-location-in-the-hierarchy"></a>Déplacer une ligne unique vers un nouvel emplacement dans la hiérarchie  
  
1.  Sariya est actuellement la supérieure de Wanida. Dans cette procédure, vous déplacez Wanida du nœud **/1/1/,** où elle se trouve actuellement, pour que Jill soit sa supérieure. Son nouveau nœud deviendra ainsi **/3/1/** . **/1/** sera donc le premier argument et **/3/** le second. Ceux-ci correspondent aux valeurs **OrgNode** de Sariya et de Jill. Exécutez le code suivant pour déplacer Wanida de l'organisation de Sariya vers celle de Jill :  
  
    ```sql  
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
  
    ```sql  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
    Wanida se trouve maintenant au nœud **/3/1/**.  
  
### <a name="reorganize-a-section-of-a-hierarchy"></a>Réorganiser une section d’une hiérarchie  
  
1.  Pour montrer comment déplacer simultanément un plus grand nombre de personnes, exécutez d'abord le code suivant pour ajouter un subalterne interne à Wanida :  
  
    ```sql  
    EXEC AddEmp 269, 291, 'Kevin', 'Marketing Intern'  ;  
    GO  
    ```  
  
2.  Kevin est désormais le subalterne de Wanida, elle-même subalterne de Jill, elle-même subalterne de David. Cela signifie que Kevin est au niveau **/3/1/1/**. Pour déplacer tous les subalternes de Jill vers un nouveau responsable, nous allons mettre à jour tous les nœuds qui ont **/3/** comme valeur **OrgNode** vers une nouvelle valeur. Exécutez le code suivant pour mettre à jour Wanida de sorte que Sariya soit sa supérieure, en conservant Kevin comme subalterne de Wanida :  
  
    ```sql  
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
  
    ```sql  
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
/1/1/1/      0x5AD0  3        291        Kevin   Marketing Intern  
/2/          0x68    1        271        John    Marketing Specialist  
/2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
/3/          0x78    1        119        Jill    Marketing Specialist  
```  
  
La totalité de l'arborescence de l'organisation dont Jill était la supérieure (Wanida et Kevin) a maintenant Sariya comme supérieure.  
  
Pour obtenir une procédure stockée qui réorganise une section d’une hiérarchie, consultez la section « Déplacement de sous-arborescences » de [Déplacement de sous-arborescences](../../relational-databases/hierarchical-data-sql-server.md#BKMK_MovingSubtrees).  
  
