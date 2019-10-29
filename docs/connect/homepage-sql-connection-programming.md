---
title: Page d’accueil pour la programmation SQL client | Microsoft Docs
description: Page Hub contenant des liens annotés vers des téléchargements et une documentation pour de nombreuses combinaisons de langues et de systèmes d’exploitation, pour la connexion à SQL Server ou à Azure SQL Database.
author: MightyPen
ms.date: 11/07/2018
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: v-daveng
ms.author: genemi
ms.openlocfilehash: 6961f8c23b4acfd787958cc9a160faf88362b54c
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451852"
---
# <a name="homepage-for-client-programming-to-microsoft-sql-server"></a>Page d’accueil pour la programmation client sur Microsoft SQL Server


Bienvenue dans notre page d’accueil sur la programmation client pour interagir avec Microsoft SQL Server et avec Azure SQL Database dans le Cloud. Cet article fournit les informations suivantes :

- Répertorie et décrit les combinaisons de langue et de pilote disponibles.
    - Des informations sont fournies pour les systèmes d’exploitation Linux (Ubuntu et autres), MacOS et Windows.
- Fournit des liens vers la documentation détaillée de chaque combinaison.
- Affiche les zones et sous-zones de la documentation hiérarchique pour certaines langues, le cas échéant.


#### <a name="azure-sql-database"></a>Azure SQL Database

Dans n’importe quel langage donné, le code qui se connecte à SQL Server est presque identique au code pour la connexion à Azure SQL Database.

Pour plus d’informations sur les chaînes de connexion pour la connexion à Azure SQL Database, consultez :

- [Utilisez .net Core (C#) pour interroger une base de données SQL Azure](/azure/sql-database/sql-database-connect-query-dotnet-core).
- Autres Azure SQL Database qui sont proches de l’article précédent dans la table des matières, à propos des autres langages. Par exemple, consultez [utilisation de PHP pour interroger une base de données SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php).


#### <a name="build-an-app-webpages"></a>Créer des pages Web d’application

Nos pages Web de *Build-a-app* présentent des exemples de code, ainsi que des informations de configuration, dans un autre format. Pour plus d’informations, consultez plus loin dans cet article la [section intitulée *créer un site Web d’application*](#an-204-aka-ms-sqldev).



<a name="an-050-languages-clients" />

## <a name="languages-and-drivers-for-client-programs"></a>Langues et pilotes pour les programmes clients


Dans le tableau suivant, chaque image de langage est un lien vers des détails sur l’utilisation de la langue avec SQL Server. Chaque lien accède à une section ultérieure de cet article.

| &nbsp; | &nbsp; | &nbsp; |
| :-- | :-- | :-- |
| [logo deC# ![][image-ref-320-csharp]](#an-110-ado-net-docu) &nbsp; | &nbsp; [![ORM Entity Framework de .NET Framework][image-ref-333-ef]](#an-116-csharp-ef-orm) | &nbsp; [![Logo Java][image-ref-330-java]](#an-130-jdbc-docu) |
| [logo &nbsp; ![Node. js][image-ref-340-node]](#an-140-node-js-docu) | &nbsp; [ **`ODBC for C++`** ](#an-160-odbc-cpp-docu)<br/>[![cpp-big-plus][image-ref-322-cpp]](#an-160-odbc-cpp-docu) | [logo de ![PHP][image-ref-360-php]](#an-170-php-docu) &nbsp; |
| &nbsp; [![Logo Python][image-ref-370-python]](#an-180-python-docu) | [logo de ![Ruby][image-ref-380-ruby]](#an-190-ruby-docu) &nbsp; | &nbsp; ... |
| &nbsp; | &nbsp; | <br />|


#### <a name="downloads-and-installs"></a>Téléchargements et installations

L’article suivant est consacré au téléchargement et à l’installation de divers pilotes de connexion SQL pour une utilisation par les langages de programmation :

- [Pilotes SQL Server](sql-server-drivers.md)



<a name="an-110-ado-net-docu" />

## <a name="c-logoimage-ref-320-csharp-c-using-adonet"></a>![C#logo][image-ref-320-csharp] C#utilisation de ADO.NET

Les langages managés .NET, C# tels que et Visual Basic, sont les utilisateurs les plus courants de ADO.net. *ADO.net* est un nom informel pour un sous-ensemble de classes .NET Framework.

#### <a name="code-examples"></a>Exemples de code

|||
| :-- | :-- |
| [Preuve de concept pour se connecter à SQL à l’aide d’ADO.NET](./ado-net/step-3-connect-sql-ado-net.md) | Un petit exemple de code axé sur la connexion et l’interrogation de SQL Server. |
| [Connexion résiliente à SQL avec ADO.NET](./ado-net/step-4-connect-resiliently-sql-ado-net.md) | Logique de nouvelle tentative dans un exemple de code, car les connexions peuvent parfois rencontrer des moments de perte de connectivité.<br /><br />La logique de nouvelle tentative s’applique bien aux connexions gérées via Internet dans n’importe quelle base de données Cloud, par exemple pour Azure SQL Database. |
| [Azure SQL Database : démonstration de l’utilisation de .NET Core sur Windows/Linux/macOS pour créer un C# programme, pour se connecter et interroger](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core) | Exemples : Azure SQL Database |
| [Build-a-App : C#, ADO.net, Windows](https://www.microsoft.com/sql-server/developer-get-started/csharp/win/) | Informations de configuration, ainsi que des exemples de code. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Documentation

|||
| :-- | :-- |
| [C#utilisation de ADO.NET](./ado-net/index.md)| Racine de notre documentation. |
| [Espace de noms : System. Data](https://docs.microsoft.com/dotnet/api/system.data) | Ensemble de classes utilisé pour ADO.NET. |
| [Namespace: System.Data.SqlClient](https://docs.microsoft.com/dotnet/api/system.data.SqlClient) | Ensemble des classes qui sont le plus directement au centre de ADO.NET. |
| &nbsp; | <br /> |



<a name="an-116-csharp-ef-orm" />

## <a name="entity-framework-logoimage-ref-333-ef-entity-framework-ef-with-cx23"></a>![Logo Entity Framework][image-ref-333-ef] Entity Framework (EF) avec C&#x23;

Entity Framework (EF) fournit un mappage objet/relationnel (ORM). Avec ORM, votre code source de programmation orientée objet (OOP) facilite la manipulation des données récupérées à partir d’une base de données SQL relationnelle.

EF a des relations directes ou indirectes avec les technologies suivantes :

- .NET Framework
- [LINQ to SQL](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/linq/)ou [LINQ to Entities](https://docs.microsoft.com/dotnet/framework/data/adonet/ef/language-reference/linq-to-entities)
- Améliorations de la syntaxe du langage, telles que l’opérateur C# **=>** dans.
- Programmes pratiques qui génèrent du code source pour les classes qui mappent aux tables de votre base de données SQL. Par exemple, [EdmGen. exe](https://docs.microsoft.com/dotnet/framework/data/adonet/ef/edm-generator-edmgen-exe).


#### <a name="original-ef-and-new-ef"></a>EF d’origine et nouveau EF

La [page de démarrage de Entity Framework](https://docs.microsoft.com/ef/) présente EF avec une description similaire à ce qui suit :

- Entity Framework est un mappeur objet-relationnel (O/RM) qui permet aux développeurs .NET de travailler avec une base de données à l’aide d’objets .NET. Cela élimine la nécessité de la plupart du code source d’accès aux données que les développeurs doivent généralement écrire.

*Entity Framework* est un nom partagé par deux branches de code source distinctes. Une branche EF est plus ancienne et son code source peut désormais être géré par le public. L’autre EF est une nouveauté. Les deux EFs sont décrits ci-après :

|     |     |
| :-- | :-- |
| [EF 6.x](https://docs.microsoft.com/ef/ef6/) | Microsoft a lancé EF en août 2008. En mars 2015, Microsoft a annoncé qu’EF 6. x était la dernière version de Microsoft. Microsoft a publié le code source dans le domaine public.<br /><br />Initialement, EF faisait partie de .NET Framework. Mais EF 6. x a été supprimé de .NET Framework.<br /><br />[Code source EF 6. x sur GitHub, dans le référentiel *ASPNET/EntityFramework6*](https://github.com/aspnet/EntityFramework6) |
| [EF Core](https://docs.microsoft.com/ef/core/) | Microsoft a publié le EF Core récemment développé en juin 2016. EF Core est conçu pour améliorer la flexibilité et la portabilité. EF Core peuvent s’exécuter sur des systèmes d’exploitation autres que Microsoft Windows. Et EF Core pouvez interagir avec les bases de données au-delà des Microsoft SQL Server et des autres bases de données relationnelles.<br /><br />**Exemples de code ADOX**<br />[Prise en main avec Entity Framework Core](https://docs.microsoft.com/ef/core/get-started/index)<br />[Prise en main de EF Core sur .NET Framework avec une base de données existante](https://docs.microsoft.com/ef/core/get-started/full-dotnet/existing-db) |
| &nbsp; | <br /> |

EF et les technologies associées sont puissants et sont beaucoup à apprendre pour le développeur qui souhaite maîtriser l’ensemble de la zone.

&nbsp;



<a name="an-130-jdbc-docu" />

## <a name="java-logoimage-ref-330-java-java-and-jdbc"></a>![Logo Java][image-ref-330-java] Java et JDBC

Microsoft fournit un pilote Java Database Connectivity (JDBC) à utiliser avec SQL Server (ou avec Azure SQL Database, bien sûr). Il s’agit d’un pilote JDBC de type 4 offrant une connectivité de base de données par le biais des interfaces de programmation d’applications (API) JDBC standard.

#### <a name="code-examples"></a>Exemples de code

|||
| :-- | :-- |
| [Exemples de code](./jdbc/code-samples/index.md) | Exemples de code qui enseignent les types de données, les jeux de résultats et les données volumineuses. |
| [Exemple d’URL de connexion](./jdbc/connection-url-sample.md) | Décrit comment utiliser une URL de connexion pour se connecter à SQL Server. Utilisez-la ensuite pour utiliser une instruction SQL pour récupérer des données. |
| [Exemple de source de données](./jdbc/data-source-sample.md) | Décrit comment utiliser une source de données pour se connecter à SQL Server. Utilisez ensuite une procédure stockée pour récupérer des données. |
| [Utilisation de Java pour interroger une base de données SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java) | Exemples : Azure SQL Database |
| [Créer des applications Java à l’aide de SQL Server sur Ubuntu](https://www.microsoft.com/sql-server/developer-get-started/java/ubuntu/) | Informations de configuration, ainsi que des exemples de code. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Documentation

La documentation JDBC comprend les principales fonctionnalités suivantes :

|||
| :-- | :-- |
| [Java Database Connectivity (JDBC)](./jdbc/index.md) | Racine de notre documentation JDBC. |
| [Référence](./jdbc/reference/index.md) | Interfaces, classes et membres. |
| [Guide de programmation pour le pilote JDBC SQL](./jdbc/programming-guide-for-jdbc-sql-driver.md) | Informations de configuration, ainsi que des exemples de code. |
| &nbsp; | <br /> |



<a name="an-140-node-js-docu" />

## <a name="nodejs-logoimage-ref-340-node-nodejs"></a>![Logo node. js][image-ref-340-node] Node.js

Avec node. js, vous pouvez vous connecter à SQL Server à partir de Windows, Linux ou Mac. La racine de notre documentation node. js est [ici](./node-js/index.md).

Le pilote de connexion node. js pour SQL Server est implémenté en JavaScript. Il s’agit d’une implémentation C# du protocole TDS, qui est pris en charge par toutes les versions récentes de SQL Server. Le pilote est un projet open source, [disponible sur GitHub](https://tediousjs.github.io/tedious/).

#### <a name="code-examples"></a>Exemples de code

|||
| :-- | :-- |
| [Preuve de concept pour se connecter à SQL à l’aide de Node.js](./node-js/step-3-proof-of-concept-connecting-to-sql-using-node-js.md) | Le code source ne permet pas de se connecter à SQL Server et d’exécuter une requête. |
| [Base de données SQL Azure : utiliser node. js pour interroger](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | Exemple pour Azure SQL Database dans le Cloud. |
| [Créer des applications node. js à utiliser SQL Server sur macOS](https://www.microsoft.com/sql-server/developer-get-started/node/mac/) | Informations de configuration, ainsi que des exemples de code. |
| &nbsp; | <br /> |



<a name="an-160-odbc-cpp-docu" />

## <a name="odbc-for-c"></a>ODBC pourC++ 

![Logo ODBC][image-ref-350-odbc] ![cpp-big-plus][image-ref-322-cpp]

Open Database Connectivity (ODBC) a été développé au cours des années 90 et .NET Framework. ODBC est conçu pour être indépendant de tout système de base de données particulier et indépendamment du système d’exploitation.

Au fil des années, de nombreux pilotes ODBC ont été créés et publiés par des groupes au sein et en dehors de Microsoft. La plage de pilotes implique plusieurs langages de programmation client. La liste des cibles de données va bien au-delà de SQL Server.

D’autres pilotes de connectivité utilisent ODBC en interne.

#### <a name="code-example"></a>Exemple de code

- [Exemple de code C++, utilisant ODBC](../odbc/reference/sample-odbc-program.md)

#### <a name="documentation-outline"></a>Structure de la documentation

Le contenu ODBC de cette section se concentre sur l’accès à SQL Server ou Azure SQL Database C++, à partir de. Le tableau suivant répertorie un plan approximatif de la documentation principale pour ODBC.


| Domaine | Sous-zone | Description |
| :--- | :------ | :---------- |
| [ODBC pourC++](./odbc/index.md) | Racine de notre documentation. |
| [Linux-Mac](./odbc/linux-mac/index.md) | &nbsp; | Informations sur l’utilisation d’ODBC sur les systèmes d’exploitation Linux ou MacOS. |
| [Windows](./odbc/windows/index.md)     | &nbsp; | Informations sur l’utilisation d’ODBC sur le système d’exploitation Windows. |
| [Administration](../odbc/admin/index.md) | &nbsp; | Outil d’administration pour la gestion des sources de données ODBC. |
| [Microsoft](../odbc/microsoft/index.md)  | &nbsp; | Différents pilotes ODBC qui sont créés et fournis par Microsoft. |
| [Conceptuel et référence](../odbc/reference/index.md) | &nbsp; | Informations conceptuelles sur l’interface ODBC, en plus de la référence traditionnelle. |
| &nbsp; " | [Annexes](../odbc/reference/appendixes/index.md)    | Tables de transition d’État, bibliothèque de curseurs ODBC, etc. |
| &nbsp; " | [Développer l’application](../odbc/reference/develop-app/index.md)  | Fonctions, Handles et bien plus encore. |
| &nbsp; " | [Développer des pilotes](../odbc/reference/develop-driver/index.md) | Comment développer votre propre pilote ODBC, si vous disposez d’une source de données spécialisée. |
| &nbsp; " | [Installer](../odbc/reference/install/index.md) | Installation ODBC, sous-clés et bien plus encore. |
| &nbsp; " | [Syntaxe](../odbc/reference/syntax/index.md)   | API pour l’installation, le programme d’installation, la traduction et l’accès aux données. |
| &nbsp; | &nbsp; | <br /> |



<a name="an-170-php-docu" />

## <a name="php-logoimage-ref-360-php-php"></a>![Logo PHP][image-ref-360-php] PHP

Vous pouvez utiliser PHP pour interagir avec SQL Server. La racine de notre documentation PHP est [ici](./php/index.md).

#### <a name="code-examples"></a>Exemples de code

|||
| :-- | :-- |
| [Preuve de concept pour se connecter à SQL à l’aide de PHP](./php/step-3-proof-of-concept-connecting-to-sql-using-php.md) | Un petit exemple de code axé sur la connexion et l’interrogation de SQL Server. |
| [Connexion résiliente à SQL avec PHP](./php/step-4-connect-resiliently-to-sql-with-php.md) | Logique de nouvelle tentative dans un exemple de code, car les connexions via Internet et le Cloud peuvent parfois rencontrer des moments de perte de connectivité. |
| [Base de données SQL Azure : utiliser PHP pour interroger](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php) | Exemples : Azure SQL Database |
| [Créer des applications PHP pour utiliser SQL Server sur RHEL](https://www.microsoft.com/sql-server/developer-get-started/php/rhel/) | Informations de configuration, ainsi que des exemples de code. |
| &nbsp; | <br /> |



<a name="an-180-python-docu" />

## <a name="python-logoimage-ref-370-python-python"></a>![Logo Python][image-ref-370-python] Python


Vous pouvez utiliser Python pour interagir avec SQL Server.

#### <a name="code-examples"></a>Exemples de code

|||
| :-- | :-- |
| [Preuve de concept pour la connexion à SQL avec Python à l’aide de pyodbc](./python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc.md) | Un petit exemple de code axé sur la connexion et l’interrogation de SQL Server. |
| [Base de données SQL Azure : utiliser Python pour interroger](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-python) | Exemples : Azure SQL Database |
| [Créer des applications PHP pour utiliser SQL Server sur SLES](https://www.microsoft.com/sql-server/developer-get-started/python/sles/) | Informations de configuration, ainsi que des exemples de code. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Documentation

| Domaine | Description |
| :--- | :---------- |
| [Python à SQL Server](./python/index.md) | Racine de notre documentation. |
| [pymssql driver](./python/pymssql/index.md) | Microsoft ne gère pas ou ne teste pas le pilote pymssql.<br /><br />Le pilote de connexion pymssql est une interface simple pour les bases de données SQL, à utiliser dans les programmes Python. Pymssql s’appuie sur FreeTDS pour fournir une interface de l’API de base de code Python (PEP-249) à Microsoft SQL Server. |
| [pilote pyodbc](./python/pyodbc/index.md)   | Le pilote de connexion pyodbc est un module python Open source qui facilite l’accès aux bases de données ODBC. Elle implémente la spécification 2,0 de l’API de base de informations, mais est compressée avec encore plus de commodité Python. |
| &nbsp; | <br /> |


<a name="an-190-ruby-docu" />

## <a name="ruby-logoimage-ref-380-ruby-ruby"></a>![Logo Ruby][image-ref-380-ruby] Ruby

Vous pouvez utiliser Ruby pour interagir avec SQL Server. La racine de notre documentation Ruby est [ici](./ruby/index.md).

#### <a name="code-examples"></a>Exemples de code

|||
| :-- | :-- |
| [Preuve de concept pour la connexion à SQL avec Ruby](./ruby/step-3-proof-of-concept-connecting-to-sql-using-ruby.md) | Un petit exemple de code axé sur la connexion et l’interrogation de SQL Server. |
| [Base de données SQL Azure : utilisez Ruby pour interroger](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ruby) | Exemples : Azure SQL Database |
| [Créer des applications Ruby pour utiliser SQL Server sur MacOS](https://www.microsoft.com/sql-server/developer-get-started/ruby/mac/) | Informations de configuration, ainsi que des exemples de code. |
| &nbsp; | <br /> |



<a name="an-204-aka-ms-sqldev" />

## <a name="build-an-app-website-for-sql-client-developmenthttpswwwmicrosoftcomsql-serverdeveloper-get-started"></a>[Créer un site Web d’application, pour le développement de clients SQL](https://www.microsoft.com/sql-server/developer-get-started/)


Sur nos pages Web [*Build-a-app*](https://www.microsoft.com/sql-server/developer-get-started/) , vous pouvez choisir parmi une longue liste de langages de programmation pour la connexion à SQL Server. Et votre programme client peut exécuter un grand nombre de systèmes d’exploitation.

*Build-a-app* insiste sur la simplicité et l’exhaustivité du développeur qui vient de commencer. Ce processus est expliqué ci-dessous.

1. Guide pratique pour installer Microsoft SQL Server
2. Comment télécharger et installer des outils et des pilotes.
3. Comment effectuer les configurations nécessaires, en fonction de votre système d’exploitation choisi.
4. Comment compiler le code source fourni.
5. Comment exécuter le programme.

Voici quelques contours approximatifs des détails fournis sur le site Web :

#### <a name="java-on-ubuntu"></a>MRO sur Ubuntu

1. Configurer votre environnement
    - Étape 1.1 : installer SQL Server
    - Étape 1,2 installation de Java
    - Étape 1,3 installation du kit de développement Java (JDK)
    - Étape 1,4 installation de Maven
2. Créer une application Java avec SQL Server
    - Étape 2,1 création d’une application Java qui se connecte à SQL Server et exécute des requêtes
    - Étape 2,2 création d’une application Java qui se connecte à SQL Server à l’aide de la mise en veille prolongée du Framework populaire
3. Rendez votre application Java plus rapide sur 100X
    - Étape 3,1 création d’une application Java pour illustrer les index ColumnStore

#### <a name="python-on-windows"></a>Python sur Windows :

1. Configurer votre environnement
    - Étape 1.1 : installer SQL Server
    - Installez Python 1.2 :
    - Étape 1,3 installation du pilote ODBC et de l’utilitaire de ligne de commande SQL pour SQL Server
2. Créer une application Python avec SQL Server
    - Étape 2,1 installation du pilote Python pour SQL Server
    - Étape 2,2 création d’une base de données pour votre application
    - Étape 2,3 création d’une application Python qui se connecte à SQL Server et exécute des requêtes
3. Rendez votre application python plus rapide sur 100X
    - Étape 3,1 création d’une nouvelle table avec 5 millions à l’aide de sqlcmd
    - Étape 3,2 création d’une application Python qui interroge cette table et mesure le temps nécessaire
    - Étape 3,3 mesurer le temps nécessaire à l’exécution de la requête
    - Étape 3,4 ajout d’un index ColumnStore à votre table
    - Étape 3,5 mesurer le temps nécessaire à l’exécution de la requête avec un index ColumnStore

Les captures d’écran suivantes vous donnent une idée de ce à quoi ressemble notre site Web de documentation de développement SQL.

#### <a name="choose-a-language"></a>Choisir un langage :

![Site Web de développement SQL, prise en main][image-ref-390-aka-ms-sqldev-choose-language]

&nbsp;

#### <a name="choose-an-operating-system"></a>Ajouter un système d'exploitation

![Site Web de développement SQL, Java Ubuntu][image-ref-400-aka-ms-sqldev-java-ubuntu]

&nbsp;



## <a name="other-development"></a>Autres développements


Cette section fournit des liens sur d’autres options de développement. Il s’agit notamment de l’utilisation de ces mêmes langages pour le développement Azure en général. Les informations vont au-delà du ciblage juste Azure SQL Database et Microsoft SQL Server.

#### <a name="developer-hub-for-azure"></a>Hub de développeur pour Azure

- [Hub de développeur pour Azure](https://docs.microsoft.com/azure/)
- [Azure pour les développeurs .NET](https://docs.microsoft.com/dotnet/azure/)
- [Azure pour les développeurs Java](https://docs.microsoft.com/java/azure/)
- [Azure pour les développeurs node. js](https://docs.microsoft.com/nodejs/azure/)
- [Azure pour les développeurs python](https://docs.microsoft.com/python/azure/)
- [Créer une application Web PHP dans Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-php)

#### <a name="other-languages"></a>Autres langages

- [Créer des applications Go à l’aide de SQL Server sur Windows](https://www.microsoft.com/sql-server/developer-get-started/go/windows/)



<!-- Image references. -->

[image-ref-322-cpp]: ./media/homepage-sql-connection-drivers/gm-cpp-4point-p61f.png
[image-ref-320-csharp]: ./media/homepage-sql-connection-drivers/gm-csharp-c10c.png
[image-ref-333-ef]: ./media/homepage-sql-connection-drivers/gm-entity-framework-ef20d.png
[image-ref-330-java]: ./media/homepage-sql-connection-drivers/gm-java-j18c.png
[image-ref-340-node]: ./media/homepage-sql-connection-drivers/gm-node-n30.png
[image-ref-350-odbc]: ./media/homepage-sql-connection-drivers/gm-odbc-ic55826-o35.png
[image-ref-360-php]: ./media/homepage-sql-connection-drivers/gm-php-php60.png
[image-ref-370-python]: ./media/homepage-sql-connection-drivers/gm-python-py72.png
[image-ref-380-ruby]: ./media/homepage-sql-connection-drivers/gm-ruby-un-r82.png
[image-ref-390-aka-ms-sqldev-choose-language]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-400-aka-ms-sqldev-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png

