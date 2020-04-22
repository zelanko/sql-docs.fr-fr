---
title: 'Étape 3 : Connexion à SQL avec pyodbc'
description: L’étape 3 est une preuve de concept, qui montre comment vous pouvez vous connecter à SQL Server à l’aide de Python et pyODBC. Les exemples de base illustrent la sélection et l’insertion de données.
ms.custom: ''
ms.date: 03/01/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4bfd6e52-817d-4f0a-a33d-11466e3f0484
author: arob98
ms.author: angrobe
ms.openlocfilehash: 971f89f9748ab8f31c234f872e817b0b474dcbe0
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528473"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>Étape 3 : Preuve de concept pour se connecter à SQL à l’aide de pyodbc

Cet exemple est une preuve de concept. L’exemple de code est simplifié par souci de clarté et ne représente pas nécessairement les meilleures pratiques recommandées par Microsoft.  

Pour commencer, exécutez l’exemple de script suivant. Créez un fichier nommé test.py, puis ajoutez les extraits de code au fur et à mesure. 

```
> python test.py
```
  
## <a name="connect"></a>Se connecter  
  
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
  
  
## <a name="run-query"></a>Exécuter une requête  
  
La fonction cursor.execute peut être utilisée pour récupérer un jeu de résultats d'une requête à partir d'une base de données SQL. Cette fonction accepte une requête et retourne un jeu de résultats, que l’on peut parcourir avec cursor.fetchone().
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print(row[0])
    row = cursor.fetchone()

```  
  
## <a name="insert-a-row"></a>Insérer une ligne  
  
Cet exemple montre comment exécuter une instruction [INSERT](../../../t-sql/statements/insert-transact-sql.md) en toute sécurité et passer des paramètres qui protègent l’application contre [l’injection de code SQL](../../../relational-databases/tables/primary-and-foreign-key-constraints.md).    
  
  
```python
#Sample insert query
cursor.execute("""
INSERT INTO SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) 
VALUES (?,?,?,?,?)""",
'SQL Server Express New 20', 'SQLEXPRESS New 20', 0, 0, CURRENT_TIMESTAMP) 
cnxn.commit()
row = cursor.fetchone()

while row: 
    print('Inserted Product key is ' + str(row[0]))
    row = cursor.fetchone()
```  

## <a name="azure-active-directory-and-the-connection-string"></a>Azure Active Directory et la chaîne de connexion

pyODBC utilise le pilote Microsoft ODBC pour SQL Server.
Si vous utilisez la version 17.1 ou une version ultérieure du pilote ODBC, vous pouvez vous servir de son mode interactif Azure Active Directory par le biais de pyODBC.
Cette option interactive fonctionne si Python et pyODBC autorisent le pilote ODBC à afficher la boîte de dialogue. Elle n’est disponible que sur les systèmes d’exploitation Windows. 

### <a name="example-connection-string-for-azure-active-directory-interactive-authentication"></a>Exemple de chaîne de connexion pour l’authentification interactive Azure Active Directory

L’exemple suivant fournit une chaîne de connexion ODBC qui spécifie l’authentification interactive Azure Active Directory :

`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

Pour plus d’informations sur les options d’authentification du pilote ODBC, consultez [Utilisation d’Azure Active Directory avec le pilote ODBC](../../odbc/using-azure-active-directory.md#new-andor-modified-dsn-and-connection-string-keywords).

## <a name="next-steps"></a>Étapes suivantes
  
Pour plus d’informations, consultez le [Centre pour développeurs Python](https://azure.microsoft.com/develop/python/).
