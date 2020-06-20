---
title: Suppression des objets de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- deleting database objects
ms.assetid: dbb94fdf-c85b-477b-8e84-f830d259bade
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 6bd69935dbfac020c4c75bb391e7932009fd4197
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054554"
---
# <a name="deleting-database-objects"></a>Suppression des objets de base de données
  Pour supprimer toutes les traces de ce didacticiel, vous pouvez simplement supprimer la base de données. Cependant, dans cette rubrique, vous allez parcourir les étapes pour inverser chaque action effectuée au cours du didacticiel.  
  
### <a name="removing-permissions-and-objects"></a>Suppression des autorisations et des objets  
  
1.  Avant de supprimer des objets, vérifiez que vous êtes dans la bonne base de données :  
  
    ```  
    USE TestData;  
    GO  
    ```  
  
2.  Utilisez l'instruction `REVOKE` pour supprimer une autorisation d'exécution pour `Mary` sur la procédure stockée :  
  
    ```  
    REVOKE EXECUTE ON pr_Names FROM Mary;  
    GO  
  
    ```  
  
3.  Utilisez l'instruction `DROP` pour supprimer une autorisation pour `Mary` d'accéder à la base de données `TestData` :  
  
    ```  
    DROP USER Mary;  
    GO  
  
    ```  
  
4.  Utilisez l'instruction `DROP` pour supprimer une autorisation pour `Mary` d'accéder à cette instance de [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]:  
  
    ```  
    DROP LOGIN [<computer_name>\Mary];  
    GO  
  
    ```  
  
5.  Utilisez l'instruction `DROP` pour supprimer la procédure stockée `pr_Names`:  
  
    ```  
    DROP PROC pr_Names;  
    GO  
  
    ```  
  
6.  Utilisez l'instruction `DROP` pour supprimer la vue `vw_Names`:  
  
    ```  
    DROP View vw_Names;  
    GO  
  
    ```  
  
7.  Utilisez l'instruction `DELETE` pour supprimer toutes les lignes de la table `Products` :  
  
    ```  
    DELETE FROM Products;  
    GO  
  
    ```  
  
8.  Utilisez l'instruction `DROP` pour supprimer la table `Products` :  
  
    ```  
    DROP Table Products;  
    GO  
  
    ```  
  
9. Vous ne pouvez pas supprimer la base de données `TestData` lorsque vous êtes dans celle-ci ; par conséquent, basculez d'abord le contexte vers une autre base de données, puis utilisez l'instruction `DROP` pour supprimer la base de données `TestData` :  
  
    ```  
    USE MASTER;  
    GO  
    DROP DATABASE TestData;  
    GO  
  
    ```  
  
 Cette étape conclut le didacticiel d'écriture d'instructions [!INCLUDE[tsql](../includes/tsql-md.md)] . N'oubliez pas que ce didacticiel est une brève présentation et ne décrit pas toutes les options des instructions utilisées. La conception et la création d'une structure de base de données efficace et la configuration de l'accès sécurisé aux données nécessitent une base de données plus complexe que celle de ce didacticiel.  
  
## <a name="return-to-sql-server-tools-portal"></a>Revenir au portail des outils SQL Server  
 [Tutoriel : Écriture d’instructions Transact-SQL](tutorial-writing-transact-sql-statements.md)  
  
## <a name="see-also"></a>Voir aussi  
 [REVOKE &#40;&#41;Transact-SQL](/sql/t-sql/statements/revoke-transact-sql)   
 [DROP USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-user-transact-sql)   
 [DROP LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-login-transact-sql)   
 [SUPPRIMER la procédure &#40;&#41;Transact-SQL](/sql/t-sql/statements/drop-procedure-transact-sql)   
 [DROP VIEW &#40;&#41;Transact-SQL](/sql/t-sql/statements/drop-view-transact-sql)   
 [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql)   
 [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql)   
 [DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql)  
  
  
