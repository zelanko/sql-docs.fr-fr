---
title: 'Leçon 2 : Créer et appliquer une stratégie de normes d’affectation de noms | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: security
ms.prod_service: database-engine
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 87e51f4e-156c-4def-8572-76a15075d75e
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 688a61aeecfb729eeee877e0f8d3e463eaff06c8
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52159037"
---
# <a name="lesson-2-create-and-apply-a-naming-standards-policy"></a>Leçon 2 : Créer et appliquer une stratégie de normes d'affectation de noms
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Certains types de stratégies de la Gestion basée sur des stratégies peuvent créer des déclencheurs afin d'appliquer la future conformité avec la stratégie. Dans cette leçon, vous allez créer une stratégie qui applique une norme d'affectation de noms pour des tables. Ensuite, vous allez tester la stratégie en essayant de créer une table qui enfreint la stratégie.  


## <a name="prerequisites"></a>Conditions préalables requises
Pour suivre ce tutoriel, vous avez besoin de SQL Server Management Studio et d’un accès à un serveur qui exécute SQL Server.

- Installez [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installez [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
  
## <a name="create-the-finance-database"></a>Créer la base de données Finance  
  
1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ouvrez une fenêtre de requête et exécutez l'instruction suivante :  
  
    ```sql  
    CREATE DATABASE Finance ;  
    GO  
    ```  
  
2.  Dans l’Explorateur d’objets, cliquez sur **Bases de données**, puis appuyez sur la touche F5 pour actualiser la liste de bases de données.  


## <a name="create-the-finance-tables-condition"></a>Créer la condition Tables de finance 

1.  Dans l’Explorateur d’objets, développez **Gestion**, **Gestion de la stratégie**, cliquez avec le bouton droit sur **Conditions**, puis cliquez sur **Nouvelle condition**. 

   ![Nouvelle condition](Media/lesson-2-create-and-apply-a-naming-standards-policy/new-condition.png)
  
2.  Dans la boîte de dialogue **Créer une nouvelle condition** , dans la zone **Nom** , tapez **Tables de finance**.  
    1. Dans la liste **Facette** , sélectionnez **Nom en plusieurs parties**. 
    1. Dans la boîte de dialogue **Expression**, dans la zone **Champ**, sélectionnez **@Name**, dans la zone **Opérateur**, sélectionnez **Comme** et dans la zone **Valeur**, tapez ```'fintbl%'``` pour forcer tous les noms de tables à commencer par les lettres **fintbl**.
    1. Dans la page **Description** , tapez **Les noms des tables de finance doivent commencer par fintbl**, puis cliquez sur **OK** pour créer la condition.  

    ![Condition Tables de finance](Media/lesson-2-create-and-apply-a-naming-standards-policy/finance-tables-condition.png)
 
## <a name="create-the-finance-name-policy"></a>Créer la stratégie Nom financier  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur **Stratégies**, puis cliquez sur **Nouvelle stratégie**.  

   ![Nouvelle stratégie](Media/lesson-2-create-and-apply-a-naming-standards-policy/new-policy.png)
  
2.  Dans la boîte de dialogue **Créer une nouvelle stratégie** , dans la zone **Nom** , tapez **Nom financier**.
    1. Dans la liste **Vérifier la condition** , sélectionnez **Tables de finance**. Cette zone se trouve dans la zone **Nom en plusieurs parties** . 
    1. Dans la zone **Par rapport à** est affichée une liste des objets de base de données qui pourraient appliquer cette stratégie. Cochez la case **Toutes les tables**.
    1. Sélectionnez la liste **Activé** . (La case **Activé** ne s’applique pas aux stratégies **À la demande** .)
    1. Dans la liste **Mode d’évaluation** , sélectionnez **Sur modification : empêcher**. Cela applique la stratégie en créant un déclencheur de base de données sur la base de données Finance. 
    1. Dans la liste **Restriction sur le serveur** , sélectionnez **Aucune**. 
    1. Dans la page **Description**, ajoutez la description « Les noms de tables de la base de données Finance doivent contenir 'fintbl%' ». 
    1. Revenez à la page **Général** et dans la zone **Toutes les bases de données**, développez **Toutes les**, puis cliquez sur **Nouvelle condition**.

    ![Créer une stratégie Nom financier](Media/lesson-2-create-and-apply-a-naming-standards-policy/create-new-policy-finance-name.png)
  
6.  Dans la boîte de dialogue **Créer une nouvelle condition** , dans la zone **Nom** , tapez **Base de données de finance**.
    1. Dans la zone **Expression**, complétez l’expression de façon à inclure @Name = 'Finance', puis cliquez sur **OK** pour fermer la page de condition. 
  
    ![Créer une condition 'finance database'](Media/lesson-2-create-and-apply-a-naming-standards-policy/create-new-condition.png)

    > [!NOTE]  
    > Vous devrez peut-être quitter la zone **Valeur** pour activer le bouton **OK** .  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="create-the-finance-policy-category"></a>Créer la catégorie de stratégie Finance  
  
1.  Dans l’Explorateur d’objets, développez **Gestion**, cliquez avec le bouton droit sur **Gestion de la stratégie**, puis cliquez sur **Gérer les catégories**.  

   ![Gérer les catégories](Media/lesson-2-create-and-apply-a-naming-standards-policy/manage-categories.png)
  
2.  Dans la boîte de dialogue **Administration des catégories de stratégie** , sous **Nom**, tapez **Finance** dans la zone vierge, puis décochez **Abonnements à la base de données autorisée**. **Abonnements à la base de données autorisée** force chaque base de données de l’instance à s’abonner aux stratégies appartenant à cette catégorie de stratégie. Dans le cadre de cette leçon, seule la base de données Finance doit s'abonner à la stratégie Nom financier.  

    ![Gérer les catégories de stratégie](Media/lesson-2-create-and-apply-a-naming-standards-policy/manage-policy-categories.png)
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

## <a name="subscribe-to-the-finance-policy-category"></a>Abonner la base de données à la catégorie de stratégie Finance  
  
1.  Dans l’Explorateur d’objets, développez **Bases de données**, cliquez avec le bouton droit sur **Finance**, pointez sur **Stratégies**, puis cliquez sur **Catégories**. 

   ![Catégories de stratégie Finance](Media/lesson-2-create-and-apply-a-naming-standards-policy/finance-categories.png)
  
2.  Cochez la case **Abonné** de la catégorie **Finance** .  

   ![Abonné à la stratégie finance](Media/lesson-2-create-and-apply-a-naming-standards-policy/subscribe-to-finance.png)
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="test-the-enforcement-of-the-finance-name-policy"></a>Tester l’application de la stratégie Nom financier  
  
1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ouvrez une fenêtre de requête. Exécutez les instructions suivantes qui essaient de créer une table qui enfreint la stratégie **Nom financier** . La table enfreint la stratégie car le nom de table ne commence pas par les lettres **fintbl**.  
  
    ```sql  
    USE Finance ;  
    GO  
    CREATE TABLE NewTable  
    (Col1 int) ;  
    GO    
    ```  
  
    Remarquez que la stratégie empêche la création de la table et retourne un message d'information qui indique le nom de la stratégie. 

   ```
     Policy 'Finance Name' has been violated by 'SQLSERVER:\SQL\SQL\SQL2017\Databases\Finance\Tables\dbo.NewTable'.
     This transaction will be rolled back.
     Policy condition: '@Name LIKE 'fintbl%''
     Policy description: 'Tables names in the Finance database must contain 'fintbl%''.
     Additional help: '' : ''
     Statement: 'CREATE TABLE NewTable  
         (Col1 int)'.
     Msg 515, Level 16, State 2, Procedure msdb.sys.sp_syspolicy_execute_policy, Line 69 [Batch Start Line 2]
     Cannot insert the value NULL into column 'target_query_expression', table 'msdb.dbo.syspolicy_policy_execution_history_details_internal'; column does not allow nulls. INSERT fails.
     The statement has been terminated.
   ``` 
  
2.  Pour fournir un nom valide, modifiez le code comme suit et réexécutez l'instruction.  
  
    ```sql  
    USE Finance ;  
    GO  
    CREATE TABLE fintblNewTable  
    (Col1 int) ;  
    GO    
    ```  
  
    Cette fois-ci, la table est créée.  
  
## <a name="apply-the-policy-to-the-whole-server"></a>Appliquer la stratégie à tout le serveur  
  
1.  Actuellement, seule la base de données Finance est abonnée à la catégorie de stratégie Finance. Dans de nombreux cas, il est plus facile d'appliquer la catégorie de stratégie à l'ensemble du serveur. Dans l’Explorateur d’objets, développez **Gestion**, cliquez avec le bouton droit sur **Gestion de la stratégie**, puis cliquez sur **Gérer les catégories**.  
  
2.  Dans la boîte de dialogue **Administration des catégories de stratégie** , recherchez la catégorie Finance et cochez la case **Abonnements à la base de données autorisée** pour la catégorie Finance.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Désormais, la catégorie Finance s’applique à toutes les bases de données, mais la condition que vous avez créée restreint la stratégie Nom financier à la base de données Finance. Cela démontre la manière dont vous pouvez utiliser des combinaisons de conditions complexes pour cibler des stratégies pour une application correcte sur de nombreux serveurs.  
  
## <a name="summary"></a>Résumé  
Ce didacticiel vous a montré comment créer des conditions, des stratégies et des groupes de stratégies de la Gestion basée sur des stratégies et comment appliquer des filtres et vérifier la conformité des cibles de la Gestion basée sur des stratégies.  
  
## <a name="next"></a>Suivant  
Ce didacticiel est terminé. Pour revenir au début, visitez [Tutoriel : Administration de serveurs à l’aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/tutorial-administering-servers-by-using-policy-based-management.md).  
  
Pour obtenir la liste des didacticiels, consultez [Didacticiels pour SQL Server 2016](../../sql-server/tutorials-for-sql-server-2016.md).  
  
## <a name="see-also"></a> Voir aussi  
[Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
