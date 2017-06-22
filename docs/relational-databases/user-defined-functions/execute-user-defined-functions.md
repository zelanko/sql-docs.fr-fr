---
title: "Exécuter des fonctions définies par l’utilisateur | Microsoft Docs"
ms.custom: 
ms.date: 10/24/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-udf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invoking user-defined functions
- user-defined functions [SQL Server], executing
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 08287922d15adabd1128da2edbb1caa65bc3f85f
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="execute-user-defined-functions"></a>Exécuter des fonctions définies par l’utilisateur
  Exécuter une fonction définie par l’utilisateur à l’aide de Transact-SQL
  

> **Remarque :** Consultez la rubrique de la  [fonction définie par l’utilisateur](https://msdn.microsoft.com/library/ms191007.aspx) et [Créer une fonction (Transact SQL)](https://msdn.microsoft.com/library/ms186755.aspx) pour en savoir plus sur les fonctions définies par l’utilisateur. 
  
 
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Dans Transact-SQL, vous pouvez fournir les paramètres à l’aide de *value* ou à l’aide de @*nom_paramètre*=*value.* Un paramètre ne fait pas partie d’une transaction. Ainsi, si vous modifiez l’un d’eux dans une transaction et que vous restaurez cette dernière par la suite, le paramètre ne reprend pas sa valeur initiale. La valeur renvoyée à l'appelant est toujours la valeur au moment du renvoie du module.  
  
###  <a name="Security"></a> Sécurité  
  
 Aucune autorisation n’est requise pour exécuter l’instruction [EXECUTE](https://msdn.microsoft.com/library/ms188332.aspx) . Cependant, des autorisations **sont requises** sur les éléments sécurisables référencés dans la chaîne EXECUTE. Par exemple, si la chaîne contient une instruction [INSERT](https://msdn.microsoft.com/library/ms174335.aspx) , l’appelant de l’instruction EXECUTE doit posséder l’autorisation INSERT sur la table cible. Les autorisations sont vérifiées au moment où l'instruction EXECUTE est rencontrée, même si celle-ci est incluse dans un module. Pour plus d’informations, consultez [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md).  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
### <a name="example"></a>Exemple 
  
Cet exemple utilise la fonction scalaire `ufnGetSalesOrderStatusText` disponible dans la plupart des éditions de `AdventureWorks`.  L’objectif de la fonction est de retourner une valeur de texte pour l’état des ventes à partir d’un entier donné.  Faites varier l’exemple en passant des nombres entiers de 1 à 7 au paramètre **\@Status** .
  
~~~tsql
USE [AdventureWorks2016CTP3]
GO  

-- Declare a variable to return the results of the function. 
DECLARE @ret nvarchar(15);   

-- Execute the function while passing a value to the @status parameter
EXEC @ret = dbo.ufnGetSalesOrderStatusText 
    @Status = 5; 

-- View the returned value.  The Execute and Select statements must be executed at the same time.  
SELECT N'Order Status: ' + @ret; 

-- Result:
-- Order Status: Shipped
~~~
  
  
  

