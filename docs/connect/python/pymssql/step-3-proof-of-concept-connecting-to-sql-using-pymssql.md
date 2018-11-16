---
title: 'Étape 3 : Preuve de concept pour se connecter à SQL à l’aide de pymssql | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2246ddeb-7c2f-46f3-8a91-cdd718d39b40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ef8c981dea064595433568a89088e800d81876e7
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606819"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pymssql"></a>Étape 3 : Preuve de concept pour se connecter à SQL à l’aide de pymssql
[!INCLUDE[Driver_Python_Download](../../../includes/driver_python_download.md)]

Cet exemple doit être considérée comme une preuve de concept uniquement.  L’exemple de code est simplifié par souci de clarté et ne représente pas nécessairement les meilleures pratiques recommandées par Microsoft.  
  
## <a name="step-1--connect"></a>Étape 1 : se connecter  
  
Le [pymssql.connect](https://pymssql.org/en/latest/ref/pymssql.html) fonction est utilisée pour se connecter à la base de données SQL.  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
```  
  
  
## <a name="step-2--execute-query"></a>Étape 2 : Exécution de requête  
  
Le [cursor.execute](https://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.execute) fonction peut être utilisée pour récupérer un jeu de résultats d’une requête par rapport à la base de données SQL. Essentiellement, cette fonction accepte n’importe quelle requête et retourne un jeu de résultats qui peut être itéré à l’utilisation de [Cursor.fetchone ()](https://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.fetchone).  
  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute('SELECT c.CustomerID, c.CompanyName,COUNT(soh.SalesOrderID) AS OrderCount FROM SalesLT.Customer AS c LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh ON c.CustomerID = soh.CustomerID GROUP BY c.CustomerID, c.CompanyName ORDER BY OrderCount DESC;')  
    row = cursor.fetchone()  
    while row:  
        print str(row[0]) + " " + str(row[1]) + " " + str(row[2])     
        row = cursor.fetchone()  
```  
  
## <a name="step-3--insert-a-row"></a>Étape 3 : Insérer une ligne  
  
Dans cet exemple, vous verrez comment exécuter un [insérer](../../../t-sql/statements/insert-transact-sql.md) instruction en toute sécurité, passer des paramètres pour protéger votre application à partir de [injection SQL](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) valeur.    
  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express', 'SQLEXPRESS', 0, 0, CURRENT_TIMESTAMP)")  
    row = cursor.fetchone()  
    while row:  
        print "Inserted Product ID : " +str(row[0])  
        row = cursor.fetchone()  
    conn.commit()
    conn.close()
```  
  
## <a name="step-4--rollback-a-transaction"></a>Étape 4 : Restaurer une transaction  
  
Cet exemple de code illustre l’utilisation de transactions dans lesquelles vous :  
  
* Commencer une transaction  
* Insérer une ligne de données  
* Restaurer votre transaction pour annuler l’insertion  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("BEGIN TRANSACTION")  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, CURRENT_TIMESTAMP)")  
    conn.rollback()  
    conn.close()
```  
    
  ## <a name="next-steps"></a>Étapes suivantes  
  
Pour plus d’informations, consultez le [centre de développement Python](https://azure.microsoft.com/develop/python/).
