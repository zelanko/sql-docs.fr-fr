---
title: 'Étape 3 : Preuve de concept pour la connexion à SQL avec Ruby | Microsoft Docs'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cac20b18-0a6d-4243-bbda-a5d1b9476441
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9724fb48f6ae896d9026bfec63056070e2180a8e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67992488"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-ruby"></a>Étape 3 : Preuve de concept pour la connexion à SQL à l’aide de Ruby

Cet exemple doit être considéré comme une preuve de concept uniquement.  L’exemple de code est simplifié par souci de clarté et ne représente pas nécessairement les meilleures pratiques recommandées par Microsoft.  
  
## <a name="step-1--connect"></a>Étape 1: se connecter  
  
La fonction [fonction tinytds:: client](https://github.com/rails-sqlserver/tiny_tds) est utilisée pour se connecter à SQL Database.  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
```  
  
## <a name="step-2--execute-a-query"></a>Étape 2 : Exécuter une requête  
  
Copiez et collez le code suivant dans un fichier vide. Appelez IT test. rb. Ensuite, exécutez-la en entrant la commande suivante à partir de votre invite de commandes:  
  
    ruby test.rb  
  
Dans l’exemple de code, la fonction [fonction tinytds:: result](https://github.com/rails-sqlserver/tiny_tds) est utilisée pour récupérer un jeu de résultats à partir d’une requête sur SQL Database. Cette fonction accepte une requête et retourne un jeu de résultats. Le jeu de résultats est itéré à l’aide de [result. Each | row |](https://github.com/rails-sqlserver/tiny_tds).  
  
``` ruby 
    require 'tiny_tds'    
    print 'test'       
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
    results = client.execute("SELECT c.CustomerID, c.CompanyName,COUNT(soh.SalesOrderID) AS OrderCount FROM SalesLT.Customer AS c LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh ON c.CustomerID = soh.CustomerID GROUP BY c.CustomerID, c.CompanyName ORDER BY OrderCount DESC")  
    results.each do |row|  
    puts row  
    end  
```  
  
## <a name="step-3--insert-a-row"></a>Étape 3: insérer une ligne  
  
Dans cet exemple, vous allez apprendre à exécuter une instruction [Insert](../../t-sql/statements/insert-transact-sql.md) en toute sécurité, à transmettre des paramètres qui protègent votre application de la valeur d' [injection SQL](../../relational-databases/tables/primary-and-foreign-key-constraints.md) .    
  
Pour utiliser fonction tinytds avec Azure, il est recommandé d’exécuter plusieurs `SET` instructions pour modifier la façon dont la session active gère des informations spécifiques. Les `SET` instructions recommandées sont fournies dans l’exemple de code. Par exemple, `SET ANSI_NULL_DFLT_ON` permet aux nouvelles colonnes créées d’autoriser les valeurs NULL même si l’état de possibilité de valeur null de la colonne n’est pas explicitement indiqué.  
  
Pour aligner le Microsoft SQL Server format [DateTime](../../t-sql/data-types/datetime-transact-sql.md) , utilisez la fonction [strftime](https://ruby-doc.org/core-2.2.0/Time.html#method-i-strftime) pour effectuer un cast au format DateTime correspondant.  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
    results = client.execute("SET ANSI_NULLS ON")  
    results = client.execute("SET CURSOR_CLOSE_ON_COMMIT OFF")  
    results = client.execute("SET ANSI_NULL_DFLT_ON ON")  
    results = client.execute("SET IMPLICIT_TRANSACTIONS OFF")  
    results = client.execute("SET ANSI_PADDING ON")  
    results = client.execute("SET QUOTED_IDENTIFIER ON")  
    results = client.execute("SET ANSI_WARNINGS ON")  
    results = client.execute("SET CONCAT_NULL_YIELDS_NULL ON")  
    require 'date'  
    t = Time.now  
    curr_date = t.strftime("%Y-%m-%d %H:%M:%S.%L")  
    results = client.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate)  
    OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, '#{curr_date}' )")  
    results.each do |row|  
    puts row  
    end  
```
