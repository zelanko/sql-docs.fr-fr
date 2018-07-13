---
title: Exécuter des fonctions définies par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- invoking user-defined functions
- user-defined functions [SQL Server], executing
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2b478d8ca2912d2afbf5dc399dfd465c0aab1c3f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408808"
---
# <a name="execute-user-defined-functions"></a>Exécuter des fonctions définies par l’utilisateur
  Vous pouvez exécuter une fonction définie par l'utilisateur dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour exécuter un défini par l’utilisateur à l’aide de la fonction :**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Dans Transact-SQL, vous pouvez fournir les paramètres à l’aide de *value* ou à l’aide de @*nom_paramètre*=*value.* Un paramètre ne fait pas partie d’une transaction. Ainsi, si vous modifiez l’un d’eux dans une transaction et que vous restaurez cette dernière par la suite, le paramètre ne reprend pas sa valeur initiale. La valeur renvoyée à l'appelant est toujours la valeur au moment du renvoie du module.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Aucune autorisation n'est requise pour exécuter l'instruction EXECUTE. Cependant, des autorisations sont requises sur les éléments sécurisables référencés dans la chaîne EXECUTE. Par exemple, si la chaîne contient une instruction INSERT, l'appelant de l'instruction EXECUTE doit posséder l'autorisation INSERT sur la table cible. Les autorisations sont vérifiées au moment où l'instruction EXECUTE est rencontrée, même si celle-ci est incluse dans un module. Pour plus d’informations, consultez [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-execute-a-user-defined-function"></a>Pour exécuter une fonction définie par l'utilisateur  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Declares a variable and sets it to zero.  
    -- This variable is used to return the results of the function.  
    DECLARE @ret nvarchar(15)= NULL;   
  
    -- Executes the dbo.ufnGetSalesOrderStatusText function.  
    --The function requires a value for one parameter, @Status.   
    EXEC @ret = dbo.ufnGetSalesOrderStatusText @Status= 5;   
    --Returns the result in the message tab.  
    PRINT @ret;  
    ```  
  
 Pour plus d’informations, consultez [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).  
  
  
