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
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798316"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>Étape 3 : Preuve de concept pour se connecter à SQL à l’aide de pyodbc

Cet exemple doit être considéré comme une preuve de concept uniquement.  L’exemple de code est simplifié par souci de clarté et ne représente pas nécessairement les meilleures pratiques recommandées par Microsoft.  

**Exécuter l’exemple de script ci-dessous**  Créez un fichier appelé test.py et ajoutez chaque extrait de code au fur et à mesure. 

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
  
  
## <a name="step-2--execute-query"></a>Étape 2 : exécuter la requête  
  
La fonction Cursor. ExecuteFunction peut être utilisée pour récupérer un jeu de résultats à partir d’une requête sur SQL Database. Cette fonction accepte essentiellement toute requête et retourne un jeu de résultats qui peut être itéré avec l’utilisation de Cursor. fetchOne ().
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print(row[0])
    row = cursor.fetchone()

```  
  
## <a name="step-3--insert-a-row"></a>Étape 3 : insérer une ligne  
  
Dans cet exemple, vous allez apprendre à exécuter une instruction [Insert](../../../t-sql/statements/insert-transact-sql.md) en toute sécurité, à transmettre des paramètres qui protègent votre application de la valeur d' [injection SQL](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) .    
  
  
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
Si votre version du pilote ODBC est 17,1 ou une version ultérieure, vous pouvez utiliser le mode interactif AAD du pilote ODBC via pyODBC.
Cette option interactive AAD fonctionne si Python et pyODBC permettent au pilote ODBC de s’afficher dans la boîte de dialogue.
Cette option est disponible uniquement sur le système d’exploitation Windows.

### <a name="example-connection-string-for-aad-interactive-authentication"></a>Exemple de chaîne de connexion pour l’authentification interactive AAD

Voici un exemple de chaîne de connexion ODBC qui spécifie l’authentification interactive AAD :

- `server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

Pour plus d’informations sur les options d’authentification AAD du pilote ODBC, consultez l’article suivant :

- [Utilisation d’Azure Active Directory avec ODBC Driver](../../odbc/using-azure-active-directory.md#new-andor-modified-dsn-and-connection-string-keywords)

## <a name="next-steps"></a>Étapes suivantes
  
Pour plus d’informations, consultez le [Centre de développement python](https://azure.microsoft.com/develop/python/).
