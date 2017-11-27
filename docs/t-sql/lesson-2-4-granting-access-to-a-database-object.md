---
title: "Accorder l’accès à un objet de base de données | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5ccbacfe52541c59e12b992220f40806cae46bca
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lesson-2-4---granting-access-to-a-database-object"></a>Leçon 2-4-accorder l’accès à un objet de base de données
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]En tant qu’administrateur, vous pouvez exécuter l’instruction SELECT à partir de la **produits** table et la **vw_Names** afficher et exécuter le **pr_Names** procédure ; Cependant, Mary ne peut pas. Pour lui octroyer les autorisations nécessaires, utilisez l'instruction GRANT.  
  
### <a name="procedure-title"></a>Titre de la procédure  
  
1.  Exécutez l'instruction suivante pour donner à `Mary` l'autorisation `EXECUTE` pour la procédure stockée `pr_Names` .  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
Dans ce scénario, Mary peut accéder uniquement à la table **Products** à l'aide de la procédure stockée. Pour que Mary puisse exécuter une instruction SELECT sur la vue, vous devez exécuter aussi `GRANT SELECT ON vw_Names TO Mary`. Pour supprimer l'accès aux objets de base de données, utilisez l'instruction REVOKE.  
  
> [!NOTE]  
> Si la table, la vue et la procédure stockée n'appartiennent pas au même schéma, l'octroi des autorisations devient plus complexe.  
  
## <a name="about-grant"></a>À propos de GRANT  
Vous devez avoir l'autorisation EXECUTE pour exécuter une procédure stockée. Vous devez avoir les autorisations SELECT, INSERT, UPDATE, et DELETE pour accéder et modifier des données. L'instruction GRANT sert également à autres autorisations, telles que les autorisations de créer des tables.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
[Résumé : configuration des autorisations sur des objets de base de données](../t-sql/lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="see-also"></a>Voir aussi  
[GRANT &#40;Transact-SQL&#41;](../t-sql/statements/grant-transact-sql.md)  
[REVOKE &#40;Transact-SQL&#41;](../t-sql/statements/revoke-transact-sql.md)  
  
  
  
