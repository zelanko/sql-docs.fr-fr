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
ms.openlocfilehash: 27b56a20a0456bef04553c614432bde270d8e98d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67935772"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pymssql"></a>Étape 3 : Preuve de concept pour se connecter à SQL à l’aide de pymssql
[!INCLUDE[Driver_Python_Download](../../../includes/driver_python_download.md)]

Cet exemple doit être considéré comme une preuve de concept uniquement.  L’exemple de code est simplifié par souci de clarté et ne représente pas nécessairement les meilleures pratiques recommandées par Microsoft.  
  
## <a name="step-1--connect"></a>Étape 1: se connecter  
  
La fonction [pymssql. Connect](https://pymssql.org/en/latest/ref/pymssql.html) est utilisée pour se connecter à SQL Database.  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
```  
  
  
## <a name="step-2--execute-query"></a>Étape 2: exécuter la requête  
  
La fonction [Cursor. Execute](https://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.execute) peut être utilisée pour récupérer un jeu de résultats à partir d’une requête sur SQL Database. Cette fonction accepte essentiellement toute requête et retourne un jeu de résultats qui peut être itéré avec l’utilisation de [Cursor. fetchOne ()](https://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.fetchone).  
  
  
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
  
## <a name="step-3--insert-a-row"></a>Étape 3: insérer une ligne  
  
Dans cet exemple, vous allez apprendre à exécuter une instruction [Insert](../../../t-sql/statements/insert-transact-sql.md) en toute sécurité, à transmettre des paramètres qui protègent votre application de la valeur d' [injection SQL](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) .    
  
  
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
  
## <a name="step-4--rollback-a-transaction"></a>Étape 4: restaurer une transaction  
  
Cet exemple de code illustre l’utilisation de transactions dans lesquelles vous:  
  
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
  
Pour plus d’informations, consultez le [Centre de développement python](https://azure.microsoft.com/develop/python/).
