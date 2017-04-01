---
title: "Octroi de l&#39;acc&#232;s &#224; un objet de base de donn&#233;es | Microsoft Docs"
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
  - "octroi de l'accès à des objets de base de données"
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Octroi de l&#39;acc&#232;s &#224; un objet de base de donn&#233;es
En tant qu’administrateur, vous pouvez exécuter l’instruction SELECT dans la table **Products** et la vue **vw_Names**, et exécuter la procédure **pr_Names**. Toutefois, Mary ne peut pas le faire. Pour lui octroyer les autorisations nécessaires, utilisez l'instruction GRANT.  
  
### Titre de la procédure  
  
1.  Exécutez l'instruction suivante pour donner à `Mary` l'autorisation `EXECUTE` pour la procédure stockée `pr_Names` .  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
Dans ce scénario, Mary peut accéder uniquement à la table **Products** à l'aide de la procédure stockée. Pour que Mary puisse exécuter une instruction SELECT sur la vue, vous devez exécuter aussi `GRANT SELECT ON vw_Names TO Mary`. Pour supprimer l'accès aux objets de base de données, utilisez l'instruction REVOKE.  
  
> [!NOTE]  
> Si la table, la vue et la procédure stockée n'appartiennent pas au même schéma, l'octroi des autorisations devient plus complexe.  
  
## À propos de GRANT  
Vous devez avoir l'autorisation EXECUTE pour exécuter une procédure stockée. Vous devez avoir les autorisations SELECT, INSERT, UPDATE, et DELETE pour accéder et modifier des données. L'instruction GRANT sert également à autres autorisations, telles que les autorisations de créer des tables.  
  
## Tâche suivante de la leçon  
[Résumé : configuration des autorisations sur des objets de base de données](../t-sql/summary-configuring-permissions-on-database-objects.md)  
  
## Voir aussi  
[GRANT &#40;Transact-SQL&#41;](../t-sql/statements/grant-transact-sql.md)  
[REVOKE &#40;Transact-SQL&#41;](../t-sql/statements/revoke-transact-sql.md)  
  
  
  
