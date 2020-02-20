---
title: 'Étape 3 : Preuve de concept pour se connecter à SQL à l’aide de pyodbc | Microsoft Docs'
ms.custom: ''
ms.date: 10/09/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4bfd6e52-817d-4f0a-a33d-11466e3f0484
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0e241d84ebc60acceafe09b1a9240711a72d2067
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "72798316"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>Étape 3 : Preuve de concept pour se connecter à SQL à l’aide de pyodbc

Cet exemple être considéré comme une preuve de concept uniquement.  L’exemple de code est simplifié par souci de clarté et ne représente pas nécessairement les meilleures pratiques recommandées par Microsoft.  

**Exécutez l’exemple de script ci-dessous** pour créer un fichier appelé test.py, puis ajoutez chaque extrait de code au fur et à mesure. 

```
> python test.py
```
  
## <a name="step-1--connect"></a>Étape 1 :  Se connecter  
  
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
  
  
## <a name="step-2--execute-query"></a>Étape 2 :  Exécuter la requête  
  
La fonction cursor.execute peut être utilisée pour récupérer un jeu de résultats d'une requête à partir d'une base de données SQL. Cette fonction accepte n'importe quelle requête et renvoie un jeu de résultats qui peut être itéré à l'aide de cursor.fetchone()
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print(row[0])
    row = cursor.fetchone()

```  
  
## <a name="step-3--insert-a-row"></a>Étape 3 :  Insérer une ligne  
  
Dans cet exemple, vous allez découvrir comment exécuter une instruction [INSERT](../../../t-sql/statements/insert-transact-sql.md) en toute sécurité, passer des paramètres pour protéger votre application de la valeur [Injection SQL](../../../relational-databases/tables/primary-and-foreign-key-constraints.md).    
  
  
```python

#Sample insert query
cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New 20', 'SQLEXPRESS New 20', 0, 0, CURRENT_TIMESTAMP )") 
cnxn.commit()
row = cursor.fetchone()

while row: 
    print 'Inserted Product key is ' + str(row[0]) 
    row = cursor.fetchone()
```  

## <a name="azure-active-directory-aad-and-the-connection-string"></a>Azure Active Directory (AAD) et la chaîne de connexion

pyODBC utilise le pilote Microsoft ODBC pour SQL Server.
Si la version du pilote ODBC est 17.1 ou une version ultérieure, vous pouvez utiliser le mode interactif AAD du pilote ODBC via pyODBC.
Cette option AAD interactive fonctionne si Python et pyODBC autorisent le pilote ODBC à afficher la boîte de dialogue.
Cette option est disponible uniquement sur le système d'exploitation Windows.

### <a name="example-connection-string-for-aad-interactive-authentication"></a>Exemple de chaîne de connexion pour l’authentification interactive AAD

Voici un exemple de chaîne de connexion ODBC qui spécifie l’authentification interactive AAD :

- `server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

Pour plus d’informations sur les options d’authentification AAD du pilote ODBC, consultez l’article suivant :

- [Utilisation d’Azure Active Directory avec ODBC Driver](../../odbc/using-azure-active-directory.md#new-andor-modified-dsn-and-connection-string-keywords)

## <a name="next-steps"></a>Étapes suivantes
  
Pour plus d’informations, consultez le [Centre pour développeurs Python](https://azure.microsoft.com/develop/python/).
