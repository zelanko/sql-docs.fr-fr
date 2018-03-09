---
title: "Bibliothèques de connectivité et frameworks | Documents Microsoft"
description: "Répertorie les pilotes de connectivité que les applications clientes peuvent utiliser différentes langues pour se connecter à Microsoft SQL Server exécuté localement ou dans le cloud, sur Linux, Windows ou Docker et également à la base de données SQL Azure et Azure SQL Data Warehouse."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.workload: Inactive
ms.openlocfilehash: 0e5a08655bcfea396bcf599ef65e7a8e1f126575
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>Les bibliothèques de connectivité et des infrastructures pour Microsoft SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Extraire le [didacticiels de mise en route](http://aka.ms/sqldev) rapidement mise en route avec des langages tels que c#, Java, Node.js, PHP et Python de programmation et générer une application à l’aide de SQL Server sur Linux ou Windows ou Docker sur macOS.

Le tableau suivant répertorie les bibliothèques de connectivité ou *pilotes* que les applications clientes peuvent utiliser à partir d’une variété de langages de se connecter à et utiliser Microsoft SQL Server exécuté localement ou dans le cloud, Linux, Windows ou Docker et également à Azure SQL Database et Azure SQL Data Warehouse. 

| Langage | Plateforme | Ressources supplémentaires | Télécharger | Découvrir |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Microsoft ADO.NET pour SQL Server](http://msdn.microsoft.com/library/mt657768.aspx) | [Télécharger](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [Bien démarrer](https://www.microsoft.com/en-us/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows, Linux, macOS | [Microsoft JDBC Driver pour SQL Server](http://msdn.microsoft.com/library/mt484311.aspx) | [Télécharger](http://go.microsoft.com/fwlink/?LinkId=245496) |  [Bien démarrer](https://www.microsoft.com/en-us/sql-server/developer-get-started/java/ubuntu)
| PHP | Windows, Linux, macOS| [Pilote SQL PHP pour SQL Server](http://msdn.microsoft.com/library/dn865013.aspx) | Système d'exploitation : <br/> \* [Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \* [Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \* [macOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [Bien démarrer](https://www.microsoft.com/en-us/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows, Linux, macOS | [Node.js Driver for SQL Server](../connect/node-js/node-js-driver-for-sql-server.md) |  [Bien démarrer](https://www.microsoft.com/en-us/sql-server/developer-get-started/node/ubuntu)
| Python | Windows, Linux, macOS | [Pilote SQL Python](../connect/python/python-driver-for-sql-server.md) <br/> \* [pyodbc](http://msdn.microsoft.com/library/mt763257.aspx) |  [Bien démarrer](https://www.microsoft.com/en-us/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows, Linux, macOS | [Pilote Ruby pour SQL Server](../connect/ruby/ruby-driver-for-sql-server.md) | [Bien démarrer](https://www.microsoft.com/en-us/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows, Linux, macOS | [Pilote Microsoft ODBC pour SQL Server](https://msdn.microsoft.com/en-us/library/mt654048(v=sql.1).aspx) | [Télécharger](https://msdn.microsoft.com/en-us/library/mt654048(v=sql.1).aspx) |  

Le tableau suivant répertorie quelques exemples d’infrastructures de relationnelle mappage ORM (Object) et des infrastructures web qui permet aux applications de client avec Microsoft SQL Server exécuté localement ou dans le cloud, sur Linux, Windows ou Docker et également à la base de données SQL Azure et Entrepôt de données SQL Azure. 

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
