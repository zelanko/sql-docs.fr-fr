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
manager: craigg
ms.openlocfilehash: 9eed37349152b48ab49859b44cc23cb463d8541b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47801377"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-ruby"></a>Étape 3 : Preuve de concept pour la connexion à SQL à l’aide de Ruby

Cet exemple doit être considérée comme une preuve de concept uniquement.  L’exemple de code est simplifié par souci de clarté et ne représente pas nécessairement les meilleures pratiques recommandées par Microsoft.  
  
## <a name="step-1--connect"></a>Étape 1 : se connecter  
  
Le [TinyTDS::Client](https://github.com/rails-sqlserver/tiny_tds) fonction est utilisée pour se connecter à la base de données SQL.  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
```  
  
## <a name="step-2--execute-a-query"></a>Étape 2 : Exécuter une requête  
  
Copiez et collez le code suivant dans un fichier vide. Appelez-le test.rb. Puis, exécutez-le en entrant la commande suivante à partir de l’invite de commandes :  
  
    ruby test.rb  
  
Dans l’exemple de code, le [TinyTds::Result](https://github.com/rails-sqlserver/tiny_tds) fonction est utilisée pour récupérer un jeu de résultats d’une requête par rapport à la base de données SQL. Cette fonction accepte une requête et retourne un jeu de résultats. Le jeu de résultats est itéré en utilisant la touche [result.each do | ligne |](https://github.com/rails-sqlserver/tiny_tds).  
  
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
  
## <a name="step-3--insert-a-row"></a>Étape 3 : Insérer une ligne  
  
Dans cet exemple, vous verrez comment exécuter un [insérer](../../t-sql/statements/insert-transact-sql.md) instruction en toute sécurité, passer des paramètres pour protéger votre application à partir de [injection SQL](../../relational-databases/tables/primary-and-foreign-key-constraints.md) valeur.    
  
Pour utiliser TinyTDS avec Azure, il est recommandé d’exécuter plusieurs `SET` instructions pour modifier la façon dont la session en cours gère des informations spécifiques. Recommandé `SET` instructions sont fournies dans l’exemple de code. Par exemple, `SET ANSI_NULL_DFLT_ON` permet aux nouvelles colonnes créées pour autoriser les valeurs null même si l’état de possibilité de valeur null de la colonne n’est pas défini explicitement.  
  
Pour s’aligner avec le serveur Microsoft SQL Server [datetime](../../t-sql/data-types/datetime-transact-sql.md) mettre en forme, utilisez la [strftime](http://ruby-doc.org/core-2.2.0/Time.html#method-i-strftime) fonction pour convertir au format datetime correspondant.  
  
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
