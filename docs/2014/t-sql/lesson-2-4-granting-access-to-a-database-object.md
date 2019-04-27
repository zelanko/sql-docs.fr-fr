---
title: Octroi de l’accès à un objet de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 19381b0c5dbe690a60b2c536a8da759205c08c31
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62643445"
---
# <a name="granting-access-to-a-database-object"></a>Octroi de l'accès à un objet de base de données
  En tant qu’administrateur, vous pouvez exécuter l’instruction SELECT dans la table **Products** et la vue **vw_Names**, et exécuter la procédure **pr_Names**. Toutefois, Mary ne peut pas le faire. Pour lui octroyer les autorisations nécessaires, utilisez l'instruction GRANT.  
  
### <a name="procedure-title"></a>Titre de la procédure  
  
1.  Exécutez l'instruction suivante pour donner à `Mary` l'autorisation `EXECUTE` pour la procédure stockée `pr_Names` .  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
 Dans ce scénario, Mary peut accéder uniquement à la table **Products** à l'aide de la procédure stockée. Pour que Mary puisse exécuter une instruction SELECT sur la vue, vous devez exécuter aussi `GRANT SELECT ON vw_Names TO Mary`. Pour supprimer l'accès aux objets de base de données, utilisez l'instruction REVOKE.  
  
> [!NOTE]  
>  Si la table, la vue et la procédure stockée n'appartiennent pas au même schéma, l'octroi des autorisations devient plus complexe.  
  
## <a name="about-grant"></a>À propos de GRANT  
 Vous devez avoir l'autorisation EXECUTE pour exécuter une procédure stockée. Vous devez avoir les autorisations SELECT, INSERT, UPDATE, et DELETE pour accéder et modifier des données. L'instruction GRANT sert également à autres autorisations, telles que les autorisations de créer des tables.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Résumé : Configuration des autorisations sur des objets de base de données](lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="see-also"></a>Voir aussi  
 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)   
 [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql)  
  
  
