---
title: Exécuter des fichiers de script Transact-SQL à l'aide de sqlcmd
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1c6d747fe98e08ee21305525302563d1c8025aa2
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703684"
---
# <a name="run-transact-sql-script-files-using-sqlcmd"></a>Exécuter des fichiers de script Transact-SQL à l'aide de sqlcmd
  Vous pouvez utiliser `sqlcmd` pour exécuter un fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)]. Un fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)] est un fichier texte qui contient une combinaison d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)], de commandes `sqlcmd` et de variables de script.  
  
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
  
1.  Ouvrir une fenêtre d’invite de commandes.  
  
2.  Dans la fenêtre d’invite de commandes, entrez ce qui suit : `sqlcmd -S myServer\instanceName -i C:\myScript.sql`  
  
3.  Appuyez sur Entrée.  
  
 La liste des noms et des adresses des employés de la société [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] apparaît dans la fenêtre d'invite de commandes.  
  
### <a name="to-save-this-output-to-a-text-file"></a>Pour enregistrer ce résultat dans un fichier texte  
  
1.  Ouvrir une fenêtre d’invite de commandes.  
  
2.  Dans la fenêtre d’invite de commandes, entrez ce qui suit : `sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`  
  
3.  Appuyez sur Entrée.  
  
 Aucun résultat n'est retourné dans la fenêtre d'invite de commandes. Le résultat est au contraire envoyé dans le fichier EmpAdds.txt. Vous pouvez vérifier ce résultat en ouvrant le fichier EmpAdds.txt.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer l’utilitaire sqlcmd](sqlcmd-start-the-utility.md)   
 [Utilitaire sqlcmd](../../tools/sqlcmd-utility.md)  
  
  
