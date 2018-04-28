---
title: 'Étape 3 : Preuve de concept pour la connexion à SQL via pyodbc | Documents Microsoft'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: python
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4bfd6e52-817d-4f0a-a33d-11466e3f0484
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 389ab8cc4c25b586b75abce440ee985bcdff4d01
ms.sourcegitcommit: beaad940c348ab22d4b4a279ced3137ad30c658a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>Étape 3 : Preuve de concept pour la connexion à SQL à l’aide de pyodbc

Cet exemple doit être considéré comme une preuve de concept uniquement.  L’exemple de code est simplifié par souci de clarté et ne représente pas nécessairement les meilleures pratiques recommandées par Microsoft.  

**Exécutez l’exemple de script ci-dessous** créer un fichier appelé test.py et ajoutez chaque extrait de code que vous avancez. 

```
> python test.py
```
  
## <a name="step-1--connect"></a>Étape 1 : se connecter  
  
```python

import pyodbc 
# Some other example server values are
# server = 'localhost\sqlexpress' # for a named instance
# server = 'myserver,port' # to specify an alternate port
server = 'tcp:myserver.database.windows.net' 
database = 'mydb' 
username = 'myusername' 
password = 'mypassword' 
cnxn = pyodbc.connect('DRIVER={ODBC Driver 17 for SQL Server};SERVER='+server+';DATABASE='+database+';UID='+username+';PWD='+ password)
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
  
Dans cet exemple, vous allez apprendre à passer en toute sécurité une commande [INSERT](../../../t-sql/statements/insert-transact-sql.md), en passant des valeurs en paramètres qui protègeront votre application à partir des tentatives [d'injection SQL](../../../relational-databases/tables/primary-and-foreign-key-constraints.md).    
  
  
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
