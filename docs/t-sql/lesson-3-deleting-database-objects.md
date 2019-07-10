---
title: 'Tutoriel T-SQL : Supprimer des objets de base de données | Microsoft Docs'
ms.custom: ''
ms.date: 07/30/2018
ms.prod: sql
ms.technology: t-sql
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- deleting database objects
ms.assetid: ecf26dd5-4535-4ed6-86fc-c73f9d9dedec
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2b155862bd9983bc8b93b6088bfa6d5df254ffe7
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67579380"
---
# <a name="lesson-3-delete-database-objects"></a>Leçon 3 : Supprimer des objets de base de données
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
Cette brève leçon supprime les objets que vous avez créés aux leçons 1 et 2, et supprime la base de données.  
  
Avant de supprimer des objets, vérifiez que vous êtes dans la bonne base de données :
  
  ```sql  
  USE TestData;  
  GO  
  ```  

## <a name="revoke-stored-procedure-permissions"></a>Révoquer les autorisations de procédure stockée
  
Utilisez l'instruction `REVOKE` pour supprimer une autorisation d'exécution pour `Mary` sur la procédure stockée :
  
  ```sql  
  REVOKE EXECUTE ON pr_Names FROM Mary;  
  GO  
  ```  
  
## <a name="drop-permissions"></a>Supprimer les autorisations

1. Utilisez l'instruction `DROP` pour supprimer une autorisation pour `Mary` d'accéder à la base de données `TestData` :
  
   ```sql  
   DROP USER Mary;  
   GO  
   ```  


2. Utilisez l'instruction `DROP` pour supprimer une autorisation pour `Mary` d'accéder à cette instance de [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]:
  
   ```sql  
   DROP LOGIN [<computer_name>\Mary];  
   GO   
   ```  
  
3. Utilisez l'instruction `DROP` pour supprimer la procédure stockée `pr_Names`:  
  
   ```sql  
   DROP PROC pr_Names;  
   GO   
   ```  
  
4. Utilisez l'instruction `DROP` pour supprimer la vue `vw_Names`:  
  
   ```sql  
   DROP VIEW vw_Names;  
   GO  
   ```  

## <a name="delete-table"></a>Supprimer la table
  
1. Utilisez l'instruction `DELETE` pour supprimer toutes les lignes de la table `Products` :  
  
    ```sql  
    DELETE FROM Products;  
    GO  
    ```  
  
2.  Utilisez l'instruction `DROP` pour supprimer la table `Products` :  
  
    ```sql  
    DROP TABLE Products;  
    GO    
    ```  

## <a name="remove-database"></a>Supprimer la base de données
  
Vous ne pouvez pas supprimer la base de données `TestData` lorsque vous êtes dans celle-ci ; par conséquent, basculez d'abord le contexte vers une autre base de données, puis utilisez l'instruction `DROP` pour supprimer la base de données `TestData` :  
  
  ```sql  
  USE MASTER;  
  GO  
  DROP DATABASE TestData;  
  GO   
  ```  
  
Cette étape conclut le didacticiel d'écriture d'instructions [!INCLUDE[tsql](../includes/tsql-md.md)] . N'oubliez pas que ce didacticiel est une brève présentation et ne décrit pas toutes les options des instructions utilisées. La conception et la création d'une structure de base de données efficace et la configuration de l'accès sécurisé aux données nécessitent une base de données plus complexe que celle de ce didacticiel.  

  
  
