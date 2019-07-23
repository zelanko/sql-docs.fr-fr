---
title: Historique des pilotes pour Microsoft SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 05/04/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 05936a9555cacfc88c9219e19bc57772109ed047
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957514"
---
# <a name="driver-history-for-microsoft-sql-server"></a>Historique des pilotes pour Microsoft SQL Server

Cette page décrit les technologies de connexion de données historiques de Microsoft pour la connexion à SQL Server.

## <a name="odbc"></a>ODBC

Il existe trois générations distinctes de fournisseurs ODBC Microsoft pour SQL Server. Le premier pilote ODBC «SQL Server» est encore fourni avec les [composants d’accès aux données Windows](#microsoft-or-windows-data-access-components). Il n’est pas recommandé d’utiliser ce pilote pour un nouveau développement. À partir de SQL Server 2005, le [SQL Server Native Client](#sql-server-native-client) comprend une interface ODBC et est le pilote ODBC fourni avec SQL Server 2005 à SQL Server 2012. Il n’est pas recommandé d’utiliser ce pilote pour un nouveau développement. Après SQL Server 2012, le [Microsoft ODBC Driver for SQL Server](#microsoft-odbc-driver-for-sql-server) est le pilote qui est mis à jour avec les fonctionnalités de serveur les plus récentes à l’avenir.

### <a name="sql-server-native-client"></a>SQL Server Native Client

SQL Server Native Client est une bibliothèque autonome qui est utilisée à la fois pour OLE DB et ODBC. SQL Server Native Client (souvent abrégé SNAC) a été inclus dans SQL Server de 2005 à 2012. SQL Server Native Client peut être utilisé pour les applications qui doivent tirer parti des nouvelles fonctionnalités introduites dans SQL Server 2005 à SQL Server 2012. (Les composants d’accès aux données Microsoft/Windows ne sont pas mis à jour pour ces nouvelles fonctionnalités dans SQL Server.) Pour les nouvelles fonctionnalités au-delà de SQL Server 2012, SQL Server Native Client ne seront pas mis à jour. Passez au Microsoft ODBC Driver for SQL Server ou au pilote Microsoft OLE DB pour SQL Server si vous souhaitez tirer parti des nouvelles fonctionnalités de SQL Server à l’avenir.

Pour obtenir une documentation complète sur le SQL Server Native Client, consultez la [documentation SQL Server Native Client](../relational-databases/native-client/sql-server-native-client-programming.md).

### <a name="microsoft-odbc-driver-for-sql-server"></a>Pilote Microsoft ODBC pour SQL Server

Après SQL Server 2012, le pilote ODBC principal pour SQL Server a été développé et publié en tant que Microsoft ODBC Driver for SQL Server. Pour plus d’informations, consultez la [documentation Microsoft ODBC Driver for SQL Server](./odbc/microsoft-odbc-driver-for-sql-server.md).

## <a name="ole-db"></a>OLE DB

Il existe trois générations distinctes de fournisseurs OLE DB Microsoft pour SQL Server. Le premier Fournisseur Microsoft OLE DB pour SQL Server (SQLOLEDB) est toujours fourni dans le cadre de [Windows Data Access Components](#microsoft-or-windows-data-access-components). Ce fournisseur ne sera pas mis à jour avec de nouvelles fonctionnalités et il n’est pas recommandé d’utiliser ce pilote pour un nouveau développement. À partir de SQL Server 2005, le [SQL Server Native Client](#sql-server-native-client) comprend une interface de fournisseur d’OLE DB (SQLNCLI) et est le fournisseur OLE DB fourni avec SQL Server 2005 à SQL Server 2017. Sa [dépréciation a été annoncée en 2011](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/), et nous vous déconseillons d’utiliser ce pilote pour un nouveau développement. Dans 2017, OLE DB technologie d’accès aux données a été dépréciée par [la suite et une nouvelle version planifiée a été annoncée](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) pour 2018. Le nouveau fournisseur de OLE DB est appelé «Microsoft OLE DB Driver for SQL Server» (MSOLEDBSQL) et est actuellement géré et pris en charge.

## <a name="adonet"></a>ADO.NET

ADO.NET a été introduit avec l’infrastructure Microsoft .NET et continue à être amélioré et maintenu. Il s’agit d’un composant fondamental de l’infrastructure Microsoft .NET. Pour plus d’informations, consultez [Microsoft ADO.net pour SQL Server](ado-net/microsoft-ado-net-for-sql-server.md).

## <a name="jdbc"></a>JDBC

### <a name="microsoft-jdbc-driver-for-sql-server"></a>Pilote Microsoft JDBC pour SQL Server

Introduite dans 2000, le pilote Microsoft JDBC pour SQL Server continue d’être amélioré et géré. Il était Open-source dans 2016. Pour obtenir les informations les plus récentes, notamment sur le téléchargement du pilote, consultez [vue d’ensemble du pilote JDBC](./jdbc/overview-of-the-jdbc-driver.md).

## <a name="php"></a>PHP

### <a name="microsoft-drivers-for-php-for-sql-server"></a>Pilotes Microsoft SQL Server pour PHP

Introduit dans 2009 en tant que projet open source, les pilotes Microsoft pour PHP pour SQL Server continuent à être améliorés et gérés. Pour obtenir les informations les plus récentes, notamment comment télécharger le pilote PHP, consultez [Microsoft drivers for PHP for SQL Server](./php/microsoft-php-driver-for-sql-server.md).

## <a name="nodejs"></a>Node.js

### <a name="microsoft-driver-for-nodejs-for-sql-server"></a>Pilote Microsoft pour node. js pour SQL Server

Le pilote Microsoft pour node. js pour SQL Server permet aux applications node. js sur Microsoft Windows et Microsoft Azure d’accéder à Microsoft SQL Server et à Microsoft Windows Azure SQL Database. Les efforts de développement ne sont plus axés sur ce pilote. Il n’est pas recommandé de créer des applications à l’aide du pilote Microsoft pour node. js pour SQL Server.

Pour plus d’informations sur le pilote Microsoft pour node. js pour SQL Server, consultez [windowsazure/node-SqlServer](https://github.com/Azure/node-sqlserver).

### <a name="tedious"></a>Fastidieux

Microsoft participe actuellement à et prend en charge le module fastidieux Open source dans node. js pour la connectivité à SQL Server à l’aide de JavaScript. Pour plus d’informations, consultez [pilote node. js pour SQL Server](./node-js/node-js-driver-for-sql-server.md).

## <a name="microsoft-or-windows-data-access-components"></a>Composants Microsoft ou Windows Data Access

Microsoft/Windows Data Access Components (MDAC/WDAC) sont fournis avec et pris en charge par Windows pour la compatibilité descendante des applications et ne font pas partie de la pile de technologies SQL Server actuelle. Aucune nouvelle fonctionnalité ne sera ajoutée aux composants dans MDAC/WDAC et il n’est pas recommandé de les utiliser pour le développement de nouvelles applications.

Dans le cadre de ce document, vous pouvez diviser la pile MDAC/WDAC en composants suivants, en fonction de la technologie et des produits:

* **ADO** (y compris ADOMD et ADOX)
* **OLE DB** (y compris les services OLE DB Core, SQL Server fournisseur OLE DB, fournisseur Oracle OLE DB, fournisseur OLE DB pour les pilotes ODBC, fournisseur de la forme de données et Fournisseur de données à distance)
* **ODBC** (y compris le gestionnaire de pilotes ODBC, le pilote ODBC SQL et le pilote ODBC Oracle)

### <a name="mdacwdac-components"></a>Composants MDAC/WDAC

MDAC/WDAC comprend les composants suivants:

* **ODBC:** L’interface Microsoft Open Database Connectivity (ODBC) est une interface de langage de programmation C qui permet aux applications d’accéder aux données à partir d’un grand nombre de systèmes de gestion de base de données (SGBD). Les applications qui utilisent cette API sont limitées à l’accès aux sources de données relationnelles uniquement.
* **OLE DB:** OLE DB est un ensemble d’interfaces COM permettant d’accéder aux données dans différents magasins de données. Des fournisseurs de OLE DB existent pour accéder aux données dans les bases de données, les systèmes de fichiers, les banques de messages, les services d’annuaire, les flux de travail et les magasins de documents.
* **ADO:** ActiveX Data Objects (ADO) fournit un modèle de programmation de haut niveau. Bien qu’un peu moins performant que le codage de OLE DB ou ODBC directement, ADO est simple à apprendre et à utiliser. Il peut être utilisé à partir de langages de script, tels que Microsoft Visual Basic Scripting Edition (VBScript) ou Microsoft JScript.
* **ADOMD:** ADO multidimensionnel (ADOMD) doit être utilisé avec les fournisseurs de données multidimensionnelles telles que Microsoft OLAP fournisseur, également connu sous le fournisseur Microsoft Analysis. Aucune amélioration majeure des fonctionnalités n’a été apportée à ce service depuis MDAC 2,0.
* **ADOX:** Les extensions ADO pour DDL et Security (ADOX) permettent la création et la modification des définitions d’une base de données, d’une table, d’un index ou d’une procédure stockée. Vous pouvez utiliser ADOX avec n’importe quel fournisseur. Le fournisseur Microsoft Jet OLE DB fournit une prise en charge complète d’ADOX, tandis que le fournisseur de OLE DB Microsoft SQL Server offre une prise en charge limitée.
* **Microsoft SQL Server les bibliothèques réseau:** Les bibliothèques réseau SQL Server permettent à SQLOLEDB et SQLODBC de communiquer avec la base de données SQL Server. Les bibliothèques réseau SQL Server suivantes ont été dépréciées dans les versions de MDAC/WDAC: Banyan VINES, AppleTalk, ServerNet, IPX/SPX, Giganet et RPC. Le protocole TCP/IP et les canaux nommés seront toujours pris en charge et disponibles sur le système d’exploitation Windows 64 bits.
* **MSDASQL:** Le fournisseur Microsoft OLE DB pour ODBC (MSDASQL) permet aux applications qui reposent sur OLE DB et ADO (qui utilise OLEDB en interne) pour accéder aux sources de données via un pilote ODBC. MSDASQL est un fournisseur OLEDB qui se connecte à ODBC, plutôt qu’à une base de données. Il s’agit d’un pont entre OLE DB et un pilote ODBC lorsqu’il n’existe aucun fournisseur de OLE DB direct pour une source de données. MSDASQL est livré avec le système d’exploitation Windows, et Windows Server 2008 et Vista SP1 étaient les premières versions de Windows à inclure une version 64 bits de la technologie.

### <a name="deprecated-mdacwdac-components"></a>Composants MDAC/WDAC déconseillés

Ces composants sont toujours pris en charge dans la version actuelle de MDAC/WDAC, mais ils peuvent être supprimés dans les versions ultérieures. Lors du développement de nouvelles applications, Microsoft vous recommande d’éviter d’utiliser ces composants. En outre, lorsque vous mettez à niveau ou modifiez des applications existantes, supprimez toutes les dépendances sur ces composants.

* **SQLOLEDB:** Le fournisseur Microsoft OLE DB pour SQL Server (SQLOLEDB), qui prend en charge les accès à Microsoft SQL Server, a été déconseillé. Sa connectivité aux futures versions de SQL Server peut ne pas être prise en charge. La possibilité de se connecter aux versions antérieures à SQL Server 7 sera supprimée du système d’exploitation après Windows 7. Les nouvelles applications doivent utiliser le pilote Microsoft OLE DB pour SQL Server (MSOLEDBSQL), qui prend en charge les nouvelles fonctionnalités de SQL Server. Les applications existantes doivent migrer vers le pilote de OLE DB Microsoft pour SQL Server également pour améliorer les performances, la fiabilité et la prise en charge. Pour plus d’informations, consultez [mise à jour d’une application vers OLE DB pilote pour SQL Server à partir de MDAC](oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).
* **SQLODBC:** Le pilote ODBC Microsoft SQL Server (SQLODBC), qui prend en charge l’accès à Microsoft SQL Server, est déconseillé. Sa connectivité aux futures versions de SQL Server peut ne pas être prise en charge. La possibilité de se connecter aux versions antérieures à SQL Server 7 sera supprimée du système d’exploitation après Windows 7. Les nouvelles applications doivent utiliser la Microsoft ODBC Driver for SQL Server sur Windows, qui prend en charge les nouvelles fonctionnalités de SQL Server. Les applications existantes doivent migrer vers le Microsoft ODBC Driver for SQL Server également pour améliorer les performances, la fiabilité et la prise en charge. Pour obtenir des informations pertinentes, consultez [mise à jour d’une application vers SQL Server Native Client à partir de MDAC](../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).
* **Microsoft Jet Moteur de base de données 4,0:** À partir de la version 2,6, MDAC ne contient plus de composants jet. En d’autres termes, MDAC 2,6, 2,7 et 2,8 ne contiennent pas Microsoft Jet, le fournisseur Microsoft Jet OLE DB, les pilotes de base de données de bureau ODBC ou DAO (jet Data Access Objects). 

  Il n’existe aucune version 64 bits du Moteur de base de données Jet, le pilote Jet OLEDB, les pilotes ODBC Jet ou Jet DAO disponible. Pour plus d’informations, consultez [l’article 957570 de la Base de connaissances](https://support.microsoft.com/kb/957570). Sur les versions 64 bits de Windows, jet 32 bits s’exécute sous le sous-système Windows WOW64. Pour plus d’informations sur WOW64, consultez la [documentation de MSDN WOW64](/windows/desktop/WinProg64/wow64-implementation-details). Les applications 64 bits natives ne peuvent pas communiquer avec les pilotes jet 32 bits s’exécutant dans WOW64.

  Au lieu de Microsoft Jet, Microsoft recommande d’utiliser [Microsoft SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express) lors du développement d’applications non-Microsoft Access nécessitant une banque de données relationnelle. Ces applications jet nouvelles ou converties peuvent continuer à utiliser Jet avec l’intention d’utiliser les fichiers Microsoft Office 2003 et versions antérieures (. mdb et. xls) pour le stockage des données non principal. Toutefois, pour ces applications, vous devez planifier la migration de jet vers le Moteur de base de données Microsoft Access. Vous pouvez [Télécharger le moteur de base de données Microsoft Access](https://www.microsoft.com/download/details.aspx?id=54920), qui vous permet de lire et d’écrire dans des fichiers préexistants dans Office 2003 (. mdb et. xls) ou avec les formats de fichier Office 2007 (*. accdb, *. xlsm, *. xlsx et *. xlsb).

  > [!IMPORTANT]
  > Veuillez lire le contrat de licence utilisateur final 2007 Office System pour des limitations d’utilisation spécifiques.

  > [!NOTE]
  > SQL Server applications peuvent également accéder au système 2007 Office, et aux versions antérieures, des fichiers de SQL Server des fonctionnalités de connectivité de données et d’intégrations hétérogènes, par le biais du pilote 2007 Office System. En outre, les applications de SQL Server 64 bits peuvent accéder aux fichiers Jet et 2007 Office System 32 bits à l’aide du SQL Server Integration Services 32 bits sur Windows 64 bits.

* **MSDADS:** Avec le fournisseur Microsoft OLE DB pour la mise en forme des données (MSDADS), vous pouvez créer des relations hiérarchiques entre les clés, les champs ou les ensembles de lignes d’une application. Aucune amélioration majeure des fonctionnalités n’a été apportée depuis MDAC 2,1. Ce fournisseur est déconseillé. Microsoft vous recommande d’utiliser XML plutôt que MSDADS.
* **Oracle ODBC et oracle OLE DB:** Le pilote ODBC Microsoft Oracle (Oracle ODBC) et Fournisseur Microsoft OLE DB pour Oracle (Oracle OLE DB) fournissent un accès aux serveurs de base de données Oracle. Ils sont générés à l’aide d’Oracle Call Interface (OCI) version 7 et offrent une prise en charge complète d’Oracle 7. En outre, il utilise l’émulation Oracle 7 pour fournir une prise en charge limitée des bases de données Oracle 8. Oracle ne prend plus en charge les applications qui utilisent des appels OCI version 7. Ces technologies sont déconseillées. Si vous utilisez des sources de données Oracle, vous devez migrer vers le pilote et le fournisseur fournis par Oracle.
* **RDS:** Services de données à distance (RDS) est un mécanisme propriétaire de Microsoft pour accéder à des objets ADO Recordset distants via Internet ou un Intranet. RDS est déconseillé; aucune amélioration majeure des fonctionnalités n’a été apportée à RDS depuis MDAC 2,1. Microsoft a publié le .NET Framework, qui dispose de nombreuses fonctionnalités SOAP et remplace les composants RDS. Tous les composants serveur RDS seront supprimés du système d’exploitation après Windows 7.
* **JRO:** Les objets JRO (jet Replication Objects) sont déconseillés. JRO est utilisé dans les bases de données*ADO avec jet (. mdb) pour créer et compresser des bases de données Jet (. mdb) et effectuer la gestion de la réplication Jet. MDAC 2,7 sera sa dernière version. JRO ne sera pas disponible sur le système d’exploitation Windows 64 bits. JRO n’est pas pris en charge dans le format de fichier*Microsoft Access 2007 (. accdb).
* **prise en charge d’ODBC 16 bits:** Si vous utilisez des applications 16 bits, vous devez migrer vers une application 32 bits. la fonctionnalité 16 bits est déconseillée et est en cours de suppression des systèmes d’exploitation 64 bits. Pour plus d’informations, consultez [l’article 896458 de la Base de connaissances](https://support.microsoft.com/kb/896458).
* **Fournisseur simple OleDb (MSDAOSP):** Le fournisseur simple OLEDB offre une infrastructure permettant de créer rapidement des fournisseurs de OLE DB sur des données simples. MSDAOSP est déconseillé.
* **Bibliothèque de curseurs ODBC:** La bibliothèque de curseurs ODBC (ODBCCR32. dll) fournit des curseurs de données côté client limités. La bibliothèque de curseurs ODBC est dépréciée; votre application peut utiliser des implémentations de curseur côté serveur en remplacement.
* **OLE DB la communication à distance de l’interface out-of-process:** La communication à distance de l’interface OLEDB (msdaps. dll) tentait de permettre l’exécution hors processus des fournisseurs de OLE DB. La communication à distance de l’interface hors processus OLEDB est déconseillée.
* **Bibliothèques réseau SQL AppleTalk et Banyan Vines:** Les bibliothèques réseau Banyan VINES, AppleTalk, ServerNet, IPX/SPX, Giganet et RPC SQL sont déconseillées. Si vous utilisez l’une de ces technologies, vous devez modifier vos applications pour utiliser l’une des autres bibliothèques réseau, telles que TCP/IP et le canal nommé.

### <a name="mdacwdac-releases"></a>Versions MDAC/WDAC

Voici une liste des scénarios de prise en charge des versions antérieures de MDAC/WDAC, en commençant par le plus ancien.

* **Mdac 1,5, mdac 2,0 et mdac 2,1:** Ces versions de MDAC étaient des versions indépendantes qui étaient publiées via Microsoft Windows NT Option Pack, le kit de développement logiciel (SDK) de la plate-forme Microsoft Windows ou le site Web MDAC. Ces versions de MDAC ne sont plus prises en charge.
* **MDAC 2.5:** Cette version de MDAC était incluse dans le système d’exploitation Windows 2000. Les service packs de MDAC 2,5 ont été inclus dans les Service Packs Windows 2000 correspondants.
* **MDAC 2.6:** MDAC 2.6 RTM, SP1 et SP2 ont été inclus avec Microsoft SQL Server 2000 RTM, SP1 et SP2, respectivement. En outre, ces service packs MDAC ont été publiés sur le site Web MDAC conformément à la planification de la publication du Service Pack Microsoft SQL Server 2000. Vous pouvez installer cette version de MDAC et ses service packs sur les plateformes Windows 2000, Windows Millennium Edition, Windows NT, Windows 95 et Windows 98. Cette version de MDAC n’est plus prise en charge.
* **MDAC 2.7:** Cette version de MDAC était fournie avec les systèmes d’exploitation Microsoft Windows XP RTM et SP1. Vous pouvez installer cette version de MDAC et ses service packs sur les plateformes Windows 2000, Windows Millennium, Windows NT et Windows 98. Vous pouvez installer cette version sur la plateforme Windows XP uniquement via le système d’exploitation ou ses packs de services. Cette version de MDAC n’est plus prise en charge.
* **MDAC 2.8:** Cette version de MDAC était inclus avec Windows Server 2003 et Windows XP SP2 et versions ultérieures. Vous pouvez également installer cette version de MDAC et ses service packs sur Windows 2000.

  * La version 32 bits de MDAC 2,8 a également été publiée sur le site Web MDAC au moment où Windows Server 2003 a été publié au client.
  * La version 64 bits de MDAC 2,8 a été publiée avec la version 64 bits de Windows Server 2003 et Windows XP.

* **Composants WDac (Windows Data Access Components):** MDAC a changé son nom en WDAC-«Windows Data Access Components» à compter de Windows Vista et de Windows Server 2008. WDAC est inclus dans le système d’exploitation et n’est pas disponible séparément pour la redistribution. La maintenance de WDAC est soumise au cycle de vie du système d’exploitation.

  les versions 32 bits et 64 bits de WDAC sont fournies avec les versions 32 bits et 64 bits des systèmes d’exploitation Windows, respectivement.

## <a name="obsolete-data-access-technologies"></a>Technologies d’accès aux données obsolètes

Les technologies obsolètes sont des technologies qui n’ont pas été améliorées ou mises à jour dans plusieurs versions de produits et qui seront exclues des futures versions de produits. N’utilisez pas ces technologies lorsque vous écrivez de nouvelles applications. Lorsque vous modifiez des applications existantes écrites à l’aide de ces technologies, envisagez de migrer ces applications vers ADO.NET ou une autre technologie actuelle.

Les composants suivants sont considérés comme obsolètes:

* **DB-Library:** DB-Library est un modèle de programmation spécifiques à SQL Server qui inclut les API C. Il n’y a eu aucune amélioration des fonctionnalités de DB-Library depuis SQL Server 6,5. Sa version finale était avec SQL Server 2000 et ne sera pas déplacée vers le système d’exploitation Windows 64 bits.
* **Embedded SQL (E-SQL):** E-SQL est un modèle de programmation spécifique au SQL Server qui permet d’incorporer des instructions Transact-SQL dans du code Visual C. Aucune amélioration des fonctionnalités n’a été apportée au E-SQL depuis SQL Server 6,5. Sa version finale était avec SQL Server 2000 et ne sera pas déplacée vers le système d’exploitation Windows 64 bits.
* **Objets d’accès aux données (DAO):** DAO permet d’accéder aux bases de données JET (Access). Cette API peut être utilisée à partir de Microsoft Visual Basic, C++Microsoft Visual et des langages de script. Il était inclus avec Microsoft Office 2000 et Office XP. DAO 3,6 est la version finale de cette technologie. Elle ne sera pas disponible sur le système d’exploitation Windows 64 bits.
* **Objets de données distantes (RDO):** RDO a été conçu spécifiquement pour accéder aux sources de données relationnelles ODBC distantes, et facilite l’utilisation de ODBC sans code d’application complexe. Il était fourni avec Microsoft Visual Basic versions 4, 5 et 6. RDO version 2,0 était la dernière version de cette technologie.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
