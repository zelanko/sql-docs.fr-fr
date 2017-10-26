---
title: "Étape 3 : Preuve de concept pour la connexion à SQL via pyodbc | Documents Microsoft"
ms.custom: 
ms.date: 08/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bfd6e52-817d-4f0a-a33d-11466e3f0484
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: ae1fc34c07fe85e8ecea70f9cc582d2d7908676e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/27/2017

---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>Étape 3 : Preuve de concept pour la connexion à SQL à l’aide de pyodbc

Cet exemple doit être considérée comme une preuve de concept uniquement.  L’exemple de code est simplifiée par souci de clarté et ne représente pas nécessairement les meilleures pratiques recommandées par Microsoft.  

**Exécutez l’exemple de script ci-dessous** créer un fichier appelé test.py et ajoutez chaque extrait de code que vous avancez. 

```
> python test.py
```
  
## <a name="step-1--connect"></a>Étape 1 : se connecter  
  
```python

import pyodbc 
server = 'tcp:myserver.database.windows.net' 
database = 'mydb' 
username = 'myusername' 
password = 'mypassword' 
cnxn = pyodbc.connect('DRIVER={ODBC Driver 13 for SQL Server};SERVER='+server+';DATABASE='+database+';UID='+username+';PWD='+ password)
cursor = cnxn.cursor()

```  
  
  
## <a name="step-2--execute-query"></a>Étape 2 : Exécuter la requête  
  
Le cursor.executefunction peut servir à récupérer un jeu de résultats d’une requête par rapport à la base de données SQL. Cette fonction accepte toute requête essentiellement et retourne un jeu de résultats qui peut être répétée sur l’utilisation de cursor.fetchone()
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print row[0] 
    row = cursor.fetchone()

```  
  
## <a name="step-3--insert-a-row"></a>Étape 3 : Insérer une ligne  
  
Dans cet exemple, vous allez apprendre à exécuter une [insérer](../../../t-sql/statements/insert-transact-sql.md) instruction passer en toute sécurité, des paramètres qui protègent votre application à partir de [injection SQL](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) valeur.    
  
  
```python

#Sample insert query
cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New 20', 'SQLEXPRESS New 20', 0, 0, CURRENT_TIMESTAMP )") 
row = cursor.fetchone()

while row: 
    print 'Inserted Product key is ' + str(row[0]) 
    row = cursor.fetchone()
```  
  `      
  ## <a name="next-steps"></a>Étapes suivantes  
  
Pour plus d’informations, consultez la [centre de développement Python](https://azure.microsoft.com/en-us/develop/python/).

