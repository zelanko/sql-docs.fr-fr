---
title: "V&#233;rifier et s&#39;abonner &#224; la strat&#233;gie Nom financier | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-query-tuning"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 126b4c4c-2a1c-4701-a0ad-8de23fbd7306
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# V&#233;rifier et s&#39;abonner &#224; la strat&#233;gie Nom financier
Dans cette tâche, vous allez configurer la base de données Finance de manière à l'abonner à la catégorie de stratégies Finance. Ensuite, vous allez tester la stratégie Nom financier.  
  
### Pour abonner la base de données à la catégorie de stratégies Finance  
  
1.  Dans l’Explorateur d’objets, développez **Bases de données**, cliquez avec le bouton droit sur **Finance**, pointez sur **Stratégies**, puis cliquez sur **Catégories**.  
  
2.  Cochez la case **Abonné** de la catégorie **Finance**.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Pour tester l'application de la stratégie Nom financier  
  
1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ouvrez une fenêtre de requête. Exécutez les instructions suivantes qui essaient de créer une table qui enfreint la stratégie **Nom financier**. La table enfreint la stratégie car le nom de table ne commence pas par les lettres **fintbl**.  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE NewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
    Remarquez que la stratégie empêche la création de la table et retourne un message d'information qui indique le nom de la stratégie.  
  
2.  Pour fournir un nom valide, modifiez le code comme suit et réexécutez l'instruction.  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE fintblNewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
    Cette fois-ci, la table est créée.  
  
### Pour appliquer la stratégie à tout le serveur  
  
1.  Actuellement, seule la base de données Finance est abonnée à la catégorie de stratégie Finance. Dans de nombreux cas, il est plus facile d'appliquer la catégorie de stratégie à l'ensemble du serveur. Dans l’Explorateur d’objets, développez **Gestion**, cliquez avec le bouton droit sur **Gestion de la stratégie**, puis cliquez sur **Gérer les catégories**.  
  
2.  Dans la boîte de dialogue **Administration des catégories de stratégie**, recherchez la catégorie Finance et cochez la case **Abonnements à la base de données autorisée** pour la catégorie Finance.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Désormais, la catégorie Finance s’applique à toutes les bases de données, mais la condition que vous avez créée restreint la stratégie Nom financier à la base de données Finance. Cela démontre la manière dont vous pouvez utiliser des combinaisons de conditions complexes pour cibler des stratégies pour une application correcte sur de nombreux serveurs.  
  
## Résumé  
Ce didacticiel vous a montré comment créer des conditions, des stratégies et des groupes de stratégies de la Gestion basée sur des stratégies et comment appliquer des filtres et vérifier la conformité des cibles de la Gestion basée sur des stratégies.  
  
## Suivant  
Ce didacticiel est terminé. Pour revenir au début, cliquez sur [Didacticiel : Administration de serveurs à l’aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/tutorial-administering-servers-by-using-policy-based-management.md).  
  
Pour obtenir la liste des didacticiels, consultez [Didacticiels pour SQL Server 2016](../../sql-server/tutorials-for-sql-server-2016.md).  
  
## Voir aussi  
[Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
  
