---
title: Bibliothèques et frameworks de connectivité
description: Répertorie les pilotes de connectivité que les applications clientes peuvent utiliser dans différents langages pour se connecter à Microsoft SQL Server s’exécutant localement ou dans le cloud, sur Linux, Windows ou Docker, ainsi qu’à Azure SQL Database et à Azure SQL Data Warehouse.
author: VanMSFT
ms.author: vanto
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.openlocfilehash: a4ed76cde2cd8ff8b9d862b981dcbed2361c6ae8
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "73049740"
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>Bibliothèques et frameworks de connectivité pour Microsoft SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Consultez les [Didacticiels de prise en main](https://aka.ms/sqldev) pour commencer rapidement à utiliser des langages de programmation tels que C#, Java, Node.js, PHP et Python et créer une application à l’aide de SQL Server sur Linux, Windows ou Docker sur macOS.

Le tableau suivant répertorie les bibliothèques de connectivité ou les *pilotes* que les applications clientes peuvent utiliser dans différents langages pour se connecter à Microsoft SQL Server s’exécutant localement ou dans le cloud, sur Linux, Windows ou Docker, ainsi qu’à Azure SQL Database et à Azure SQL Data Warehouse. 

| Langage | Plateforme | Ressources supplémentaires | Téléchargement | Découvrir |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Microsoft ADO.NET pour SQL Server](/sql/connect/ado-net/microsoft-ado-net-sql-server) | [Télécharger](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [Bien démarrer](https://www.microsoft.com/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows, Linux, macOS | [Pilote JDBC Microsoft pour SQL Server](https://msdn.microsoft.com/library/mt484311.aspx) | [Télécharger](https://go.microsoft.com/fwlink/?LinkId=245496) |  [Bien démarrer](https://www.microsoft.com/sql-server/developer-get-started/java/ubuntu)
| PHP | Windows, Linux, macOS| [PHP SQL Driver pour SQL Server](../connect/php/microsoft-php-driver-for-sql-server.md) | Système d’exploitation : <br/> \* [Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \* [Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \* [macOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [Bien démarrer](https://www.microsoft.com/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows, Linux, macOS | [Pilote Node.js pour SQL Server](../connect/node-js/node-js-driver-for-sql-server.md) |  [Bien démarrer](https://www.microsoft.com/sql-server/developer-get-started/node/ubuntu)
| Python | Windows, Linux, macOS | [Pilote Python SQL](../connect/python/python-driver-for-sql-server.md) <br/> \* [pyodbc](https://msdn.microsoft.com/library/mt763257.aspx) |  [Bien démarrer](https://www.microsoft.com/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows, Linux, macOS | [Pilote Ruby pour SQL Server](../connect/ruby/ruby-driver-for-sql-server.md) | [Bien démarrer](https://www.microsoft.com/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows, Linux, macOS | [Pilote ODBC Microsoft pour SQL Server](https://msdn.microsoft.com/library/mt654048(v=sql.1).aspx) | [Télécharger](https://msdn.microsoft.com/library/mt654048(v=sql.1).aspx) |  

Le tableau suivant répertorie quelques exemples de frameworks de mappage d’objet relationnel (ORM) et de frameworks web que les applications clientes peuvent utiliser pour se connecter à Microsoft SQL Server s’exécutant localement ou dans le cloud sur Linux, Windows ou Docker, ainsi qu’à Azure SQL Database et à Azure SQL Data Warehouse. 

| Langage | Plateforme | ORM |
| :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Entity Framework](https://docs.microsoft.com/ef)<br>[Entity Framework Core](https://docs.microsoft.com/ef/core/index) |
| Java | Windows, Linux, macOS |[Mettre en veille prolongée](https://hibernate.org/orm)|
| PHP | Windows, Linux | [Laravel (Eloquent)](https://laravel.com/docs/5.0/eloquent) |
| Node.js | Windows, Linux, macOS | [Sequelize ORM](https://docs.sequelizejs.com) |
| Python | Windows, Linux, macOS |[Django](https://www.djangoproject.com/) |
| Ruby | Windows, Linux, macOS | [Ruby on rails](https://rubyonrails.org/) |

## <a name="related-links"></a>Liens connexes
- [Pilotes SQL Server](https://msdn.microsoft.com/library/mt654049.aspx) pour la connexion à partir d’applications clientes
