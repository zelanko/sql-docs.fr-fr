---
title: "Bibliothèques de connexions de bases de données Microsoft SQL | Documents Microsoft"
description: "Fournit des liens de téléchargement pour les modules qui permettent la connexion à Microsoft SQL Server et de la base de données SQL Azure, à partir d’une variété de langages de programmation du client."
author: MightyPen
ms.service: 
ms.prod: sql-server
ms.technology: dbe-data-tier-apps
ms.custom: develop apps
ms.workload: data-management
ms.topic: article
ms.date: 08/09/2017
ms.author: genemi
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 191d24de433ed6b156c1c02730eb6304bf4d683e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Modules de connexion pour les bases de données Microsoft SQL

Cet article fournit des liens de téléchargement pour les modules de connexion ou *pilotes* que votre programme client peut utiliser pour interagir avec [Microsoft SQL Server](../index.md)et son double dans le cloud [Azure Base de données SQL](http://docs.microsoft.com/azure/sql-database/). Les pilotes sont disponibles pour une variété de langages de programmation, en cours d’exécution sur les systèmes d’exploitation suivants :

- Linux (Ubuntu)
- MacOS
- Windows


#### <a name="oop-to-relational-mismatch"></a>Incompatibilité de programmation orientée objet-relationnel

*Relationnelle*: les programmes clients qui sont écrits dans un langage orienté objet de programmation (OOP) souvent utilisent les pilotes SQL qui retournent des données interrogées dans un format qui n’est plus relationnel qu’orientée objet. À l’aide d’ADO.NET en c# est un exemple. L’incompatibilité de format relationnel OOP rend parfois plus difficile à écrire et à comprendre le code de programmation orientée objet.

*ORM*: autres pilotes ou des infrastructures retournent des données interrogées au format OOP, ce qui évite l’incompatibilité. Ces pilotes fonctionnent par attendu que les classes ont été définies pour faire correspondre les colonnes de données de tables SQL particulières. Le pilote effectue ensuite les *mappage relationnel objet* (ORM) pour retourner des données interrogées comme une instance d’une classe. Microsoft Entity Framework (EF) pour c# et mettre en veille prolongée pour Java, sont deux exemples.

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


| Langage | Téléchargez le pilote SQL |
| :------- | :---------------------- |
| C#       | [ADO.NET](http://www.microsoft.com/net/download/)<br /><br />[.NET core,-Ubuntu Linux](https://www.microsoft.com/net/core#Ubuntu)<br />[.NET core, pour MacOS](https://www.microsoft.com/net/core#macos)<br />[.NET core, pour Windows](https://www.microsoft.com/net/core) |
| C++      | [ODBC 13.1](http://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server) |
| Java     | [JDBC](http://go.microsoft.com/fwlink/?LinkId=245496)<br />[Télécharger 6.2](http://www.microsoft.com/download/details.aspx?id=55539) |
| Node.js  | [Pilote Node.js, des instructions d’installation](http://docs.microsoft.com/sql/connect/node-js/step-1-configure-development-environment-for-node-js-development) |
| PHP      | *Système d'exploitation :*<br /><br />[Pilote Windows PHP](http://www.microsoft.com/download/details.aspx?id=20098)<br />[Pilote Ubuntu ou MacOS PHP, à partir de Github](http://github.com/Microsoft/msphpsql/tree/dev#install-unix) |
| Python   | [pyodbc, des instructions d’installation](http://docs.microsoft.com/sql/connect/python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development)<br />[Télécharger ODBC 13.1](http://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server) |
| Ruby     | [Pilote Ruby, des instructions d’installation](https://docs.microsoft.com/sql/connect/ruby/step-1-configure-development-environment-for-ruby-development)<br />[Page de téléchargement Ruby](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |


<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>Pilotes pour un accès ORM


Le tableau suivant répertorie des exemples d’infrastructures relationnelle mappage ORM (Object) qui les applications clientes utilisent pour se connecter aux bases de données Microsoft SQL.


| Langage | Téléchargement du pilote ORM |
| :------- | :------------------ |
| C# | [Entity Framework Core](http://docs.microsoft.com/ef/core/)<br />[Entity Framework (6.x ou version ultérieure)](http://docs.microsoft.com/ef/) |
| Java | [Mise en veille prolongée ORM](http://hibernate.org/orm)|
| PHP | [ORM parlant, inclus dans l’installation de Laravel](http://laravel.com/docs/) |
| Node.js | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | [Django](http://www.djangoproject.com/) |
| Ruby | [Ruby sur Rails](http://rubyonrails.org/) |
| &nbsp; | <br /> |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Pages Web d’une application de build


[http://aka.ms/sqldev](http://aka.ms/sqldev) permet d’accéder à un ensemble de nos *-générer une application* des pages Web. Les pages Web fournissent des informations sur les nombreuses combinaisons de programmation de langue, système d’exploitation et le pilote de connexion SQL. Parmi les informations fournies par les pages Web générer une application sont les éléments suivants :

- Plus d’informations sur la prise en main depuis le début, pour chaque combinaison de langue + opér sys + pilote.
    - Instructions pour installer les derniers pilotes de connexion SQL.
- Exemples de code pour chacun des éléments suivants :
    - Exemples de code objet-relationnel.
    - Exemples de code ORM.
    - Démonstrations d’index ColumnStore pour des performances beaucoup plus rapides.


#### <a name="first-page-of-build-an-app-webpages"></a>Première page, des pages Web de générer une application

![Pages Web générer une application, capture d’écran de première page][image-ref-163-buildanapp-webpages-first-page]


#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Menu Java - Ubuntu, des pages Web de générer une application

![Pages Web générer une application, les menus Java Ubuntu][image-ref-167-buildanapp-webpages-menu-java-ubuntu]


&nbsp;


## <a name="related-links"></a>Liens connexes

- [Exemples de code pour la connexion à la base de données SQL Azure dans le cloud, avec Java et d’autres langages](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java).


<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png

