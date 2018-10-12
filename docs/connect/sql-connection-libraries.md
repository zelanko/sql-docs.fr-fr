---
title: Bibliothèques de connexions de bases de données Microsoft SQL | Microsoft Docs
description: Fournit des liens de téléchargement pour les modules qui permettent la connexion à Microsoft SQL Server et de la base de données SQL Azure, à partir d’une variété de langages de programmation côté client.
author: MightyPen
ms.prod: sql
ms.technology: ''
ms.custom: ''
ms.topic: article
ms.date: 06/18/2018
ms.author: genemi
ms.openlocfilehash: fa070ecfed9d962dc2716e5b72eaf690eff0fe7f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806088"
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Modules de connexion pour les bases de données Microsoft SQL

Cet article fournit des liens de téléchargement pour les modules de connexion ou *pilotes* que vos programmes clients peuvent utiliser pour interagir avec [Microsoft SQL Server](../relational-databases/database-features.md)et avec sa représentation dans le cloud [Azure Base de données SQL](http://docs.microsoft.com/azure/sql-database/). Pilotes sont disponibles pour un large éventail de langages de programmation, en cours d’exécution sur les systèmes d’exploitation suivants :

- Linux (Ubuntu)
- MacOS
- Windows

#### <a name="oop-to-relational-mismatch"></a>Incompatibilité de la programmation orientée objet-relationnel

*Relationnelles*: les programmes clients qui sont écrits dans un langage orienté objet de programmation (OOP) souvent utilisent les pilotes SQL qui retournent des données interrogées dans un format plus relationnelles qu’orientée objet. C# à l’aide d’ADO.NET est un exemple. La programmation orientée objet-relationnel incompatibilité de format est parfois plus difficile à écrire et à comprendre le code de programmation orientée objet.

*ORM*: autres pilotes ou les infrastructures de retournent des données interrogées dans le format de la programmation orientée objet, éviter l’incompatibilité. Ces pilotes fonctionnent en attend que les classes ont été définies pour correspondre aux colonnes de données des tables SQL particuliers. Le pilote effectue ensuite les *mapping objet-relationnel* (ORM) pour retourner des données interrogées en tant qu’instance d’une classe. Entity Framework (EF de Microsoft) pour c# et la mise en veille prolongée pour Java, sont deux exemples.

Cet article consacre des sections distinctes pour ces deux types de pilotes de connexion.

<a name="anchor-20-drivers-relational-access" />

## <a name="drivers-for-relational-access"></a>Pilotes pour un accès relationnel


<!--
Each given Microsoft Download Center page should be enhanced
with a link to the next NEWER version page, on the day that the
original page is no longer the latest because the newer page is being added.
But this policy is not agreed on or observed,
putting the links in the following table at risk for being outdated.

PHP driver in Github.com also uses this FWLink:  http://go.microsoft.com/fwlink/?LinkID=518036 ,
although the FWLink is less precise than is http://github.com/Microsoft/msphpsql/tree/dev#install-unix .
-->

| Langue | Téléchargez le pilote SQL |
| :------- | :---------------------- |
| C# | [ADO.NET](http://www.microsoft.com/net/download/)<br /><br />[.NET core, pour Linux Ubuntu](https://www.microsoft.com/net/core#Ubuntu)<br />[.NET core, pour MacOS](https://www.microsoft.com/net/core#macos)<br />[.NET core, pour Windows](https://www.microsoft.com/net/core) |
| C++ | [ODBC](./odbc/download-odbc-driver-for-sql-server.md)<br /><br />[OLE DB](./oledb/download-oledb-driver-for-sql-server.md) |
| Java | [JDBC](./jdbc/download-microsoft-jdbc-driver-for-sql-server.md) |
| Node.js | [Pilote Node.js, instructions d’installation](./node-js/step-1-configure-development-environment-for-node-js-development.md) |
| PHP | [PHP](./php/download-drivers-php-sql-server.md) |
| Python | [pyodbc, instructions d’installation](./python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development.md)<br />[Télécharger ODBC](./odbc/download-odbc-driver-for-sql-server.md) |
| Ruby | [Pilote Ruby, instructions d’installation](./ruby/step-1-configure-development-environment-for-ruby-development.md)<br />[Page de téléchargement de Ruby](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |

<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>Pilotes pour l’accès aux ORM


Le tableau suivant répertorie des exemples d’infrastructures objet mappage relationnel (ORM) qui les applications clientes utilisent pour se connecter aux bases de données Microsoft SQL.


| Langue | Téléchargement du pilote ORM |
| :------- | :------------------ |
| C# | [Entity Framework Core](http://docs.microsoft.com/ef/core/)<br />[Entity Framework (6.x ou version ultérieure)](http://docs.microsoft.com/ef/) |
| Java | [Mise en veille prolongée ORM](http://hibernate.org/orm)|
| PHP | [Parlant ORM, inclus dans l’installation de Laravel](http://laravel.com/docs/) |
| Node.js | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | [Django](http://www.djangoproject.com/) |
| Ruby | [Ruby on Rails](http://rubyonrails.org/) |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Pages Web d’une application générée
[http://aka.ms/sqldev](http://aka.ms/sqldev) vous accédez à un ensemble de *une application générée* pages Web. Les pages Web fournissent des informations sur les nombreuses combinaisons de langage de programmation, système d’exploitation et pilote de connexion SQL. Parmi les informations fournies par les pages Web d’une application générée contient les éléments suivants :

- Plus d’informations sur la prise en main dès le début, pour chaque combinaison de langue, système d’exploitation + pilote.
    - Instructions pour installer les derniers pilotes de connexion SQL.
- Exemples de code pour chacun des éléments suivants :
    - Exemples de code objet-relationnel.
    - Exemples de code ORM.
    - ColumnStore index des démonstrations de performances beaucoup plus rapides.

#### <a name="first-page-of-build-an-app-webpages"></a>Première page, des pages Web d’une application générée
![Pages Web d’une application générée, première capture d’écran de la page][image-ref-163-buildanapp-webpages-first-page]

#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Menu pour Java - Ubuntu, de pages Web d’une application générée
![Une application générée des pages Web menu Java Ubuntu][image-ref-167-buildanapp-webpages-menu-java-ubuntu]

&nbsp;

## <a name="related-links"></a>Liens connexes
- [Exemples pour la connexion à la base de données SQL Azure dans le cloud, avec Java et d’autres langages de code](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java).

<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
