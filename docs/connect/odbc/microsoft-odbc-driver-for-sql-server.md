---
title: Pilote Microsoft ODBC pour SQL Server | Documents Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f2ae91b-06af-4c9a-9d24-062df7bc4662
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e867bb283434a6a7ae515823b370c73e4df4e131
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-odbc-driver-for-sql-server"></a>Pilote Microsoft ODBC pour SQL Server

![Téléchargement-bas encerclé](../../ssdt/media/download.png)[pour télécharger le pilote ODBC](../sql-connection-libraries.md#anchor-20-drivers-relational-access)

ODBC est l’API d’accès de données native principale pour les applications écrites en C et C++ pour SQL Server. Il existe un pilote ODBC pour la plupart des sources de données. Autres langues que vous peuvent utiliser ODBC incluent COBOL, Perl, PHP et Python. ODBC est largement utilisé dans les scénarios d’intégration de données.

Le pilote ODBC est fourni avec des outils comme [ **sqlcmd** ](https://msdn.microsoft.com/library/ms162773.aspx) et [ **bcp**](https://msdn.microsoft.com/library/ms162802.aspx). Le **sqlcmd** utilitaire vous permet d’exécuter des instructions Transact-SQL, des procédures système et des scripts SQL. Le **bcp** utilitaire copie en bloc des données entre une instance de Microsoft SQL Server et un fichier de données dans un format que vous choisissez. Vous pouvez utiliser **bcp** pour importer un grand nombre de nouvelles lignes dans des tables SQL Server ou pour exporter des données de tables dans les fichiers de données.  

## <a name="code-example-in-c"></a>Exemple de code en C++

Nous avons un fichier de petite .zip qui contient le code source d’un programme C++ qui utilise ODBC :

- [Exemple de code C++, l’utilisation d’ODBC](../../odbc/reference/sample-odbc-program.md)

## <a name="download"></a>Télécharger

- ![Téléchargement-bas encerclé](../../ssdt/media/download.png)[pour télécharger le pilote ODBC](../sql-connection-libraries.md#anchor-20-drivers-relational-access)

## <a name="documentation"></a>Documentation  

### <a name="linux-and-macos"></a>Linux et Mac OS

- [Installation du pilote](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Connexion avec **bcp**](../../connect/odbc/linux-mac/connecting-with-bcp.md)
- [Connexion avec **sqlcmd**](../../connect/odbc/linux-mac/connecting-with-sqlcmd.md)
- [À l’aide de l’authentification intégrée (Kerberos)](../../connect/odbc/linux-mac/using-integrated-authentication.md)
- [Mots clés de chaîne de connexion et les noms de Source de données](../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md)
- [Suivi d’accès aux données](../../connect/odbc/linux-mac/data-access-tracing-with-the-odbc-driver-on-linux.md)
- [Forum aux Questions](../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)
- [Installation du Gestionnaire de pilotes](../../connect/odbc/linux-mac/installing-the-driver-manager.md)
- [Problèmes connus](../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)
- [Instructions de programmation](../../connect/odbc/linux-mac/programming-guidelines.md)
- [Notes de publication](../../connect/odbc/linux-mac/release-notes.md)
- [Prise en charge de la haute disponibilité et récupération d’urgence](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)

### <a name="windows"></a>Windows

- [Exemple d’exécution asynchrone (méthode de notification)](../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)
- [Résilience de connexion du pilote ODBC Windows](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)
- [Le regroupement de connexions prenant en charge les pilotes](../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)
- [Fonctionnalités et modifications de comportement](../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)
- [Notes de publication](../../connect/odbc/windows/release-notes.md)
- [Configuration système requise, installation et fichiers de pilote](../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)

### <a name="features"></a>Fonctionnalités

- [Fournisseurs de magasins de clés personnalisé](../../connect/odbc/custom-keystore-providers.md)
- [SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-features.md) (les fonctionnalités disponibles s’appliquent également, sans OLEDB, le pilote ODBC pour SQL Server)
- [À l’aide de toujours chiffré](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
- [À l’aide d’Azure Active Directory](../../connect/odbc/using-azure-active-directory.md)
- [À l’aide de la résolution IP réseau Transparent](../../connect/odbc/using-transparent-network-ip-resolution.md)

## <a name="community"></a>Communauté  
- [Blog de l’équipe Microsoft ODBC Driver for SQL Server](http://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [Forum d'accès aux données SQL Server](http://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  

