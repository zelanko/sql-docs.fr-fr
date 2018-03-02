---
title: "Bibliothèques de connectivité et frameworks | Documents Microsoft"
description: "Répertorie les pilotes de connectivité que les applications clientes peuvent utiliser différentes langues pour se connecter à Microsoft SQL Server exécuté localement ou dans le cloud, sur Linux, Windows ou Docker et également à la base de données SQL Azure et Azure SQL Data Warehouse."
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.workload: Inactive
ms.openlocfilehash: 765fb054ab4fb5332df7b2f9d2e202188f621b67
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>Les bibliothèques de connectivité et des infrastructures pour Microsoft SQL Server

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Consultez nos [didacticiels de mise en route](http://aka.ms/sqldev) pour démarrer rapidement avec des langages de programmation tels que c#, Java, Node.js, PHP et Python et générer une application à l’aide de SQL Server sur Linux, Windows ou Docker sous macOS.

Le tableau ci-dessous répertorie les bibliothèques de connectivité ou *pilotes* que les applications clientes peuvent utiliser à partir d’une variété de langages pour se connecter et utiliser Microsoft SQL Server en local ou dans le cloud, sous Linux, Windows ou Docker ainsi qu'avec SQL Azure Database et Azure SQL Data Warehouse. 

| Langage | Plateforme | Ressources supplémentaires | Télécharger | Découvrir |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Microsoft ADO.NET pour SQL Server](http://msdn.microsoft.com/library/mt657768.aspx) | [Télécharger](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [Prise en main](https://www.microsoft.com/en-us/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows, Linux, macOS | [Microsoft JDBC Driver pour SQL Server](http://msdn.microsoft.com/library/mt484311.aspx) | [Télécharger](http://go.microsoft.com/fwlink/?LinkId=245496) |  [Prise en main](https://www.microsoft.com/en-us/sql-server/developer-get-started/java/ubuntu)
| PHP | Windows, Linux, macOS| [Pilote SQL PHP pour SQL Server](http://msdn.microsoft.com/library/dn865013.aspx) | Système d'exploitation : <br/> \*[Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \*[Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \*[macOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [Prise en main](https://www.microsoft.com/en-us/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows, Linux, macOS | [Node.js Driver for SQL Server](../connect/node-js/node-js-driver-for-sql-server.md) |  [Prise en main](https://www.microsoft.com/en-us/sql-server/developer-get-started/node/ubuntu)
| Python | Windows, Linux, macOS | [Pilote SQL Python](../connect/python/python-driver-for-sql-server.md) <br/> \*[pyodbc](http://msdn.microsoft.com/library/mt763257.aspx) |  [Prise en main](https://www.microsoft.com/en-us/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows, Linux, macOS | [Pilote Ruby pour SQL Server](../connect/ruby/ruby-driver-for-sql-server.md) | [Prise en main](https://www.microsoft.com/en-us/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows, Linux, macOS | [Pilote Microsoft ODBC pour SQL Server](https://msdn.microsoft.com/en-us/library/mt654048(v=sql.1).aspx) | [Télécharger](https://msdn.microsoft.com/en-us/library/mt654048(v=sql.1).aspx) |  

Le tableau ci-dessous répertorie quelques exemples de frameworks de  mapping objet-relationnel (ORM) et des frameworks web que les applications clientes peuvent utiliser avec Microsoft SQL Server en local ou dans le cloud, sur Linux, Windows ou Docker ainsi qu'avec SQL Azure Database et Azure SQL Data Warehouse. 

| Langage | Plateforme | ORM(s) |
| :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Entity Framework](https://docs.microsoft.com/en-us/ef)<br>[Entity Framework Core](https://docs.microsoft.com/en-us/ef/core/index) |
| Java | Windows, Linux, macOS |[Mise en veille prolongée ORM](http://hibernate.org/orm)|
| PHP | Windows, Linux | [Laravel (parlant)](https://laravel.com/docs/5.0/eloquent) |
| Node.js | Windows, Linux, macOS | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | Windows, Linux, macOS |[Django](https://www.djangoproject.com/) |
| Ruby | Windows, Linux, macOS | [Ruby sur Rails](http://rubyonrails.org/) |

## <a name="related-links"></a>Liens connexes
- [Pilotes SQL Server](http://msdn.microsoft.com/library/mt654049.aspx) pour la connexion à partir d’applications clientes
