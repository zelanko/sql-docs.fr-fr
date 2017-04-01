---
title: "Ex&#233;cuter des fichiers de script Transact-SQL &#224; l&#39;aide de sqlcmd | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "scripts Transact-SQL"
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
caps.latest.revision: 42
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Ex&#233;cuter des fichiers de script Transact-SQL &#224; l&#39;aide de sqlcmd
 Utilisez **sqlcmd** pour exécuter un fichier de script Transact-SQL. Un fichier de script Transact-SQL est un fichier texte qui peut contenir une combinaison d’instructions Transact-SQL, de commandes **sqlcmd** et de variables de script.  

## Créer un fichier de script  
 Pour créer un fichier de script Transact-SQL simple à l’aide du Bloc-notes, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, sur **Accessoires**, puis cliquez sur **Bloc-notes**.  
  
2.  Copiez et collez le code Transact-SQL suivant dans le Bloc-notes :  
  
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
  
## Exécuter le fichier de script  
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Dans la fenêtre d’invite de commandes, tapez : **sqlcmd -S myServer\instanceName -i C:\myScript.sql**  
  
3.  Appuyez sur Entrée.  
  
 La liste des noms et des adresses des employés de la société [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] apparaît dans la fenêtre d'invite de commandes.  

## Enregistrer la sortie dans un fichier texte
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Dans la fenêtre d’invite de commandes, tapez : **sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt**  
  
3.  Appuyez sur Entrée.  
  
 Aucun résultat n'est retourné dans la fenêtre d'invite de commandes. Le résultat est au contraire envoyé dans le fichier EmpAdds.txt. Vous pouvez vérifier ce résultat en ouvrant le fichier EmpAdds.txt.  
  
## Voir aussi  
 [Démarrer l'utilitaire sqlcmd](../../relational-databases/scripting/start-the-sqlcmd-utility.md)   
 [Utilitaire sqlcmd](../../tools/sqlcmd-utility.md)  
  
  