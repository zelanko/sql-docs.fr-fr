---
title: Bibliothèques de connexions pour les bases de données Microsoft SQL | Microsoft Docs
description: Fournit des liens de téléchargement pour les modules qui permettent de se connecter à Microsoft SQL Server et Azure SQL Database, à partir de différents langages de programmation client.
author: MightyPen
ms.prod: sql
ms.technology: ''
ms.custom: ''
ms.topic: article
ms.date: 06/18/2018
ms.author: genemi
ms.openlocfilehash: 71254b937c4c0173af9e1549efb98a0b42f65e02
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632816"
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Modules de connexion pour les bases de données Microsoft SQL

Cet article fournit des liens vers des modules de connexion ou des *pilotes* que vos programmes clients peuvent utiliser pour interagir avec [Microsoft SQL Server](../relational-databases/database-features.md)et avec sa représentation dans le Cloud [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/). Les pilotes sont disponibles pour un large éventail de langages de programmation, s’exécutant sur les systèmes d’exploitation suivants :

- Linux
- MacOS
- Windows

#### <a name="oop-to-relational-mismatch"></a>Incompatibilité de la OOP à la relation

*Relationnel*: les programmes clients écrits dans un langage de programmation orientée objet utilisent souvent des pilotes SQL qui retournent des données interrogées dans un format qui est plus relationnel que orienté objet. C#l’utilisation de ADO.NET en est un exemple. Le format OOP-Relational incompatibilité rend parfois le code OOP plus difficile à écrire et à comprendre.

*ORM*: d’autres pilotes ou frameworks renvoient des données interrogées au format OOP, ce qui évite l’incompatibilité. Ces pilotes fonctionnent en espérant que les classes ont été définies pour correspondre aux colonnes de données de tables SQL particulières. Le pilote effectue ensuite le *mappage objet/relationnel* (ORM) pour retourner les données interrogées sous la forme d’une instance d’une classe. Le Entity Framework Microsoft (EF) pour C#et le mode veille prolongée pour Java, sont deux exemples.

Le présent article consacre des sections distinctes à ces deux types de pilotes de connexion.

<a name="anchor-20-drivers-relational-access" />

## <a name="drivers-for-relational-access"></a>Pilotes pour l’accès relationnel


<!--
Each given Microsoft Download Center page should be enhanced
with a link to the next NEWER version page, on the day that the
original page is no longer the latest because the newer page is being added.
But this policy is not agreed on or observed,
putting the links in the following table at risk for being outdated.

PHP driver in Github.com also uses this FWLink:  https://go.microsoft.com/fwlink/?LinkID=518036 ,
although the FWLink is less precise than is https://github.com/Microsoft/msphpsql/tree/dev#install-unix .
-->

| Langue | Télécharger le pilote SQL |
| :------- | :---------------------- |
| C# | [ADO.NET](https://www.microsoft.com/net/download/)<br />[Microsoft.Data.SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/)<br /><br />[.NET Core, pour Linux-Ubuntu](https://www.microsoft.com/net/core#Ubuntu)<br />[.NET Core, pour MacOS](https://www.microsoft.com/net/core#macos)<br />[.NET Core, pour Windows](https://www.microsoft.com/net/core) |
| C++ | [ODBC](./odbc/download-odbc-driver-for-sql-server.md)<br /><br />[OLE DB](./oledb/download-oledb-driver-for-sql-server.md) |
| Java | [JDBC](./jdbc/download-microsoft-jdbc-driver-for-sql-server.md) |
| Node.js | [Pilote node. js, instructions d’installation](./node-js/step-1-configure-development-environment-for-node-js-development.md) |
| PHP | [PHP](./php/download-drivers-php-sql-server.md) |
| Python | [pyodbc, instructions d’installation](./python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development.md)<br />[Télécharger ODBC](./odbc/download-odbc-driver-for-sql-server.md) |
| Ruby | [Pilote Ruby, instructions d’installation](./ruby/step-1-configure-development-environment-for-ruby-development.md)<br />[Page de téléchargement de Ruby](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |

<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>Pilotes pour l’accès ORM


Le tableau suivant répertorie des exemples de frameworks ORM (Object relationnel Mapping) que les applications clientes utilisent pour se connecter aux bases de données Microsoft SQL.


| Langue | Téléchargement du pilote ORM |
| :------- | :------------------ |
| C# | [Entity Framework Core](https://docs.microsoft.com/ef/core/)<br />[Entity Framework (6. x ou version ultérieure)](https://docs.microsoft.com/ef/) |
| Java | [Mettre en veille prolongée](https://hibernate.org/orm)|
| PHP | [Éloquence ORM, inclus dans l’installation de Laravel](https://laravel.com/docs/) |
| Node.js | [Sequelize ORM](https://docs.sequelizejs.com) |
| Python | [Django](https://www.djangoproject.com/) |
| Ruby | [Ruby on rails](https://rubyonrails.org/) |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Créer des pages Web d’application
[https://aka.ms/sqldev](https://aka.ms/sqldev) vous amène à un ensemble de pages Web de *Build-a-app* . Les pages Web fournissent des informations sur les nombreuses combinaisons du langage de programmation, du système d’exploitation et du pilote de connexion SQL. Parmi les informations fournies par les pages Web de génération-a-app, citons les éléments suivants :

- Détails sur la prise en main du tout début, pour chaque combinaison de langue + système d’exploitation + pilote.
    - Instructions pour l’installation des derniers pilotes de connexion SQL.
- Exemples de code pour chacun des éléments suivants :
    - Exemples de code relationnel objet.
    - Exemples de code ORM.
    - Démonstrations d’index ColumnStore pour des performances beaucoup plus rapides.

#### <a name="first-page-of-build-an-app-webpages"></a>Première page, des pages Web Build-a-app
![Page Web de génération-a-app, capture d’écran de la première page][image-ref-163-buildanapp-webpages-first-page]

#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Menu pour Java-Ubuntu, des pages Web de génération-a-app
![Build-a-app Web, menu Java Ubuntu][image-ref-167-buildanapp-webpages-menu-java-ubuntu]

&nbsp;

## <a name="related-links"></a>Liens connexes
- [Exemples de code pour la connexion à Azure SQL Database dans le Cloud, avec Java et d’autres langages](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java).

<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
