---
title: Exécuter des fichiers de script Transact-SQL à l’aide de sqlcmd | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
caps.latest.revision: 41
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4aa1fd4418e4758ca41cce9d3aeba70838a0dce0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37260405"
---
# <a name="run-transact-sql-script-files-using-sqlcmd"></a>Exécuter des fichiers de script Transact-SQL à l'aide de sqlcmd
  Vous pouvez utiliser `sqlcmd` pour exécuter un fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)]. Un [!INCLUDE[tsql](../../includes/tsql-md.md)] fichier de script est un fichier texte qui peut contenir une combinaison de [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions, `sqlcmd` commandes et variables de script.  
  
 Pour créer un fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)] simple à l'aide du Bloc-notes, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, sur **Accessoires**, puis cliquez sur **Bloc-notes**.  
  
2.  Copiez et collez le code [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant dans le Bloc-notes :  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT p.FirstName + ' ' + p.LastName AS 'Employee Name',  
    a.AddressLine1, a.AddressLine2 , a.City, a.PostalCode   
    FROM Person.Person AS p   
       INNER JOIN HumanResources.Employee AS e   
            ON p.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.BusinessEntityAddress bea   
            ON bea.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.Address AS a   
            ON a.AddressID = bea.AddressID;  
    GO  
    ```  
  
3.  Enregistrez le fichier sous **myScript.sql** sur le lecteur C.  
  
### <a name="to-run-the-script-file"></a>Pour exécuter le fichier de script  
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Dans la fenêtre d’invite de commandes, tapez : `sqlcmd -S myServer\instanceName -i C:\myScript.sql`  
  
3.  Appuyez sur Entrée.  
  
 La liste des noms et des adresses des employés de la société [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] apparaît dans la fenêtre d'invite de commandes.  
  
### <a name="to-save-this-output-to-a-text-file"></a>Pour enregistrer ce résultat dans un fichier texte  
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Dans la fenêtre d’invite de commandes, tapez : `sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`  
  
3.  Appuyez sur Entrée.  
  
 Aucun résultat n'est retourné dans la fenêtre d'invite de commandes. Le résultat est au contraire envoyé dans le fichier EmpAdds.txt. Vous pouvez vérifier ce résultat en ouvrant le fichier EmpAdds.txt.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer l'utilitaire sqlcmd](sqlcmd-start-the-utility.md)   
 [sqlcmd Utility](../../tools/sqlcmd-utility.md)  
  
  
