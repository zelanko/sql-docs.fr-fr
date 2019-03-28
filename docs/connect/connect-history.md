---
title: Historique des pilotes pour Microsoft SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 05/04/2018
ms.prod: sql
ms.reviewer: genemi
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daveng
manager: craigg
ms.openlocfilehash: e6656b2df8eb635686dd5702d9b60a644a04e29b
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511616"
---
# <a name="driver-history-for-microsoft-sql-server"></a>Historique des pilotes pour Microsoft SQL Server

Cette page décrit les technologies de connexion de données d’historique de Microsoft pour la connexion à SQL Server.

## <a name="odbc"></a>ODBC

Il existe trois générations distinctes des pilotes Microsoft ODBC pour SQL Server. Le premier pilote ODBC de « SQL Server » est toujours fourni dans le cadre de [Windows Data Access Components](#microsoft-or-windows-data-access-components). Il n’est pas recommandé d’utiliser ce pilote pour un nouveau développement. À compter de SQL Server 2005, le [SQL Server Native Client](#sql-server-native-client) inclut une interface ODBC et le pilote ODBC fourni avec SQL Server 2005 via SQL Server 2012. Il n’est pas recommandé d’utiliser ce pilote pour un nouveau développement. Après SQL Server 2012, le [Microsoft ODBC Driver for SQL Server](#microsoft-odbc-driver-for-sql-server) est le pilote est mis à jour avec les fonctionnalités du serveur les plus récentes à l’avenir.

### <a name="sql-server-native-client"></a>SQL Server Native Client

SQL Server Native Client est une bibliothèque autonome qui est utilisée pour OLE DB et ODBC. SQL Server Native Client (SNAC souvent abrégé) a été inclus dans SQL Server 2005 à l’année 2012. SQL Server Native Client peut être utilisé pour les applications qui doivent tirer parti des nouvelles fonctionnalités introduites dans SQL Server 2005 via SQL Server 2012. (Microsoft/Windows Data Access Components ne sont pas mis à jour pour ces nouvelles fonctionnalités dans SQL Server.) Nouvelles fonctionnalités au-delà de SQL Server 2012, SQL Server Native Client ne sera pas être mis à jour. Basculez vers le pilote Microsoft ODBC pour SQL Server ou le pilote Microsoft OLE DB pour SQL Server si vous souhaitez tirer parti des nouvelles fonctionnalités de SQL Server à l’avenir.

Pour obtenir une documentation complète de SQL Server Native Client, consultez le [documentation de SQL Server Native Client](../relational-databases/native-client/sql-server-native-client-programming.md).

### <a name="microsoft-odbc-driver-for-sql-server"></a>Pilote Microsoft ODBC pour SQL Server

Après SQL Server 2012, principal ODBC driver for SQL Server a été développé et publié en tant que le pilote Microsoft ODBC pour SQL Server. Pour plus d’informations, consultez le [pilote Microsoft ODBC pour la documentation de SQL Server](./odbc/microsoft-odbc-driver-for-sql-server.md).

## <a name="ole-db"></a>OLE DB

Il existe trois générations distinctes des fournisseurs OLE DB Microsoft pour SQL Server. Le premier « Microsoft OLE DB fournisseur pour SQL Server » (SQLOLEDB) est toujours fourni dans le cadre de [Windows Data Access Components](#microsoft-or-windows-data-access-components). Ce fournisseur n’est pas mis à jour avec de nouvelles fonctionnalités et il n’est pas recommandé d’utiliser ce pilote pour un nouveau développement. À compter de SQL Server 2005, le [SQL Server Native Client](#sql-server-native-client) inclut une interface de fournisseur OLE DB (SQLNCLI) et est le fournisseur OLE DB livrés avec SQL Server 2005 à SQL Server 2017. Il a été [annoncées comme déconseillées dans 2011](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) et il n’est pas recommandé d’utiliser ce pilote pour un nouveau développement. En 2017, technologie d’accès aux données OLE DB a été par la suite [annuler la dépréciation et une nouvelle version planifiée a été annoncée](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) pour 2018. Le nouveau fournisseur OLE DB est appelé le « Microsoft OLE DB Driver pour SQL Server » (MSOLEDBSQL) et est actuellement géré et pris en charge.

## <a name="adonet"></a>ADO.NET

ADO.NET a été introduit avec le Microsoft .NET Framework et continue à être amélioré et conservées. Il est un composant principal de Microsoft .NET Framework. Pour plus d’informations, consultez [Microsoft ADO.NET pour SQL Server](ado-net/microsoft-ado-net-for-sql-server.md).

## <a name="jdbc"></a>JDBC

### <a name="microsoft-jdbc-driver-for-sql-server"></a>Pilote Microsoft JDBC pour SQL Server

Introduite dans 2000, Microsoft JDBC Driver for SQL Server continue améliorée et la maintenance. Il s’agissait d’open source en 2016. Pour plus d’informations, y compris comment télécharger le pilote, consultez [vue d’ensemble du pilote JDBC](./jdbc/overview-of-the-jdbc-driver.md).

## <a name="php"></a>PHP

### <a name="microsoft-drivers-for-php-for-sql-server"></a>Pilotes Microsoft SQL Server pour PHP

Le Microsoft Drivers for PHP for SQL Server apparu en 2009 comme un projet open source, continuer à être amélioré et conservées. Pour plus d’informations, y compris comment télécharger le pilote PHP, consultez [Microsoft Drivers for PHP for SQL Server](./php/microsoft-php-driver-for-sql-server.md).

## <a name="nodejs"></a>Node.js

### <a name="microsoft-driver-for-nodejs-for-sql-server"></a>Pilote Microsoft pour Node.js pour SQL Server

Microsoft Driver for Node.js pour SQL Server permet aux applications de Node.js sur Microsoft Windows et Microsoft Windows Azure pour accéder à Microsoft SQL Server et Microsoft Windows Azure SQL Database. Les efforts de développement sont ne sont plus ciblées sur ce pilote. Il n’est pas recommandé pour créer des applications à l’aide de Microsoft Driver pour Node.js pour SQL Server.

Pour plus d’informations sur Microsoft Driver pour Node.js pour SQL Server, consultez [WindowsAzure / nœud-sqlserver](https://github.com/Azure/node-sqlserver).

### <a name="tedious"></a>Fastidieux

Actuellement, Microsoft contribue à et prend en charge le module fastidieux open source Node.js pour la connectivité à SQL Server à l’aide de JavaScript. Pour plus d’informations, consultez [pilote Node.js pour SQL Server](./node-js/node-js-driver-for-sql-server.md).

## <a name="microsoft-or-windows-data-access-components"></a>Microsoft ou Windows Data Access Components

Microsoft/Windows Data Access Components (MDAC/WDAC) sont fournis avec et pris en charge par Windows pour l’application vers l’arrière compatibilité et ne font pas partie de la pile de technologies SQL Server actuelle. Aucune nouvelle fonctionnalité ne sera être ajoutée aux composants dans MDAC/WDAC et il n’est pas recommandé de les utiliser pour le développement de nouvelles applications.

Dans le cadre de ce document, vous pouvez diviser la pile MDAC/WDAC en les composants suivants, selon les produits et technologies :

* **ADO** (y compris ADOMD et ADOX)
* **OLE DB** (y compris les Services principaux OLE DB, fournisseur OLE DB SQL Server, fournisseur Oracle OLE DB, le fournisseur OLE DB pour pilotes ODBC, forme fournisseur de données et à distance du fournisseur de données)
* **ODBC** (y compris le Gestionnaire de pilotes ODBC, pilote SQL ODBC et pilote ODBC pour Oracle)

### <a name="mdacwdac-components"></a>Composants MDAC/WDAC

MDAC/WDAC comprend les composants suivants :

* **ODBC :** l’interface de Microsoft Open Database Connectivity (ODBC) est une interface de programmation en langage C qui permet aux applications d’accéder aux données à partir d’un éventail de systèmes de gestion de base de données (SGBD). Les applications qui utilisent cette API sont limitées à l’accès aux sources de données relationnelle uniquement.
* **OLE DB :** OLE DB est un ensemble d’interfaces COM pour l’accès aux données dans un large éventail de magasins de données. Fournisseurs OLE DB existent pour l’accès aux données dans les bases de données, systèmes de fichiers, les banques de messages, services d’annuaire, le workflow et banques de documents.
* **ADO :** ActiveX Data Objects (ADO) fournit un modèle de programmation de haut niveau. Bien qu’un peu moins performante que de coder directement à OLE DB ou ODBC, ADO est simple à apprendre et à utiliser. Il peut être utilisé à partir de langages de script, tels que Microsoft Visual Basic Scripting Edition (VBScript) ou Microsoft JScript.
* **ADOMD:** ADO multidimensionnel (ADOMD) doit être utilisé avec les fournisseurs de données multidimensionnelles telles que Microsoft OLAP fournisseur, également connu sous le fournisseur Microsoft Analysis. Aucun principales améliorations fonctionnelles n’apportées à ce dernier depuis MDAC 2.0.
* **ADOX :** Extensions ADO pour DDL et de sécurité (ADOX) activer la création et la modification des définitions d’une base de données, une table, un index ou une procédure stockée. Vous pouvez utiliser ADOX avec n’importe quel fournisseur. Le fournisseur Microsoft Jet OLE DB fournit une prise en charge complète pour ADOX, tandis que le fournisseur OLE DB Microsoft SQL Server fournit la prise en charge limitée.
* **Bibliothèques de réseau Microsoft SQL Server :** les bibliothèques réseau du serveur SQL autoriser SQLOLEDB et SQLODBC communiquer avec la base de données SQL Server. Les bibliothèques de réseau SQL Server suivantes ont été déconseillés dans les versions MDAC/WDAC : Banyan Vines, AppleTalk, ServerNet, IPX/SPX, Giganet et RPC. TCP/IP et canaux nommés continueront à être pris en charge et sont disponibles sur le système d’exploitation de Windows 64 bits.
* **MSDASQL:** Le fournisseur Microsoft OLE DB pour ODBC (MSDASQL) permet aux applications qui reposent sur OLE DB et ADO (qui utilise OLEDB en interne) pour accéder aux sources de données via un pilote ODBC. MSDASQL est un fournisseur OLEDB qui se connecte à ODBC, au lieu d’une base de données. Il est conçu comme un pont à partir d’OLE DB à un pilote ODBC lorsqu’il n’existe aucun fournisseur OLE DB direct pour une source de données. MSDASQL est fourni avec le système d’exploitation Windows et Windows Server 2008 et Vista SP1 ont été que le premier Windows libère pour inclure une version 64 bits de la technologie.

### <a name="deprecated-mdacwdac-components"></a>Composants MDAC/WDAC obsolètes

Ces composants sont toujours pris en charge dans la version actuelle de MDAC/WDAC, mais ils peuvent être supprimés dans les versions futures. Lorsque vous développez de nouvelles applications, Microsoft vous recommande d’éviter d’utiliser ces composants. En outre, lorsque vous mettez à niveau ou modifiez des applications existantes, supprimez toute dépendance sur ces composants.

* **SQLOLEDB:** Le fournisseur Microsoft OLE DB pour SQL Server (SQLOLEDB), qui prend en charge les accès à Microsoft SQL Server, a été déconseillé. Sa connectivité vers les versions ultérieures de SQL Server ne peut pas être pris en charge. La possibilité de se connecter aux versions antérieures à SQL Server 7 sera retiré le système d’exploitation après Windows 7. Nouvelles applications doivent utiliser le pilote Microsoft OLE DB pour SQL Server (MSOLEDBSQL), qui prend en charge les nouvelles fonctionnalités de SQL Server. Les applications existantes doivent migrer vers le pilote Microsoft OLE DB pour SQL Server aussi bien pour meilleures performances, fiabilité et prise en charge. Pour plus d’informations, consultez [mise à jour d’une Application vers OLE DB Driver pour SQL Server à partir de MDAC](oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).
* **SQLODBC :** le Microsoft SQL Server ODBC Driver (SQLODBC), qui prend en charge les accès à Microsoft SQL Server, a été déconseillée. Sa connectivité vers les versions ultérieures de SQL Server ne peut pas être pris en charge. La possibilité de se connecter aux versions antérieures à SQL Server 7 sera retiré le système d’exploitation après Windows 7. Nouvelles applications doivent utiliser le pilote Microsoft ODBC pour SQL Server sur Windows, qui prend en charge les nouvelles fonctionnalités de SQL Server. Les applications existantes doivent migrer vers le pilote Microsoft ODBC pour SQL Server aussi bien pour meilleures performances, fiabilité et prise en charge. Pour obtenir des informations pertinentes, consultez [mise à jour d’une Application vers SQL Server Native Client à partir de MDAC](../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).
* **Moteur de base de données Microsoft Jet 4.0 :** depuis la version 2.6, MDAC ne contient plus de composants Jet. En d’autres termes, MDAC 2.6, 2.7 et 2.8 ne contiennent pas Microsoft Jet, le fournisseur Microsoft Jet OLE DB, les pilotes de base de données ODBC Desktop ou Jet objets DAO (Data Access). 

  Aucune version 64 bits du moteur de base de données Jet, le pilote OLE DB de Jet, les pilotes Jet ODBC ou DAO de Jet n’est disponible. Pour plus d’informations, consultez [l’article 957570 de la Base de connaissances](https://support.microsoft.com/kb/957570). Dans les versions 64 bits de Windows, Jet de 32 bits s’exécute sous le sous-système WOW64 de Windows. Pour plus d’informations sur WOW64, consultez la [MSDN WOW64 documentation](/windows/desktop/WinProg64/wow64-implementation-details). Applications 64 bits natives ne peuvent pas communiquer avec les pilotes Jet de 32 bits s’exécutant dans WOW64.

  Au lieu de Microsoft Jet, Microsoft recommande d’utiliser [Microsoft SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express) lors du développement de nouvelles applications non Microsoft Access nécessitant un magasin de données relationnelles. Ces applications Jet nouveau ou converties peuvent continuer à utiliser Jet avec à l’aide de Microsoft Office 2003 et les fichiers antérieurs (.mdb et .xls) pour le stockage de données non primaire. Toutefois, pour ces applications, vous devez planifier migrer de Jet vers le moteur de base de données Microsoft Access. Vous pouvez [télécharger le moteur de base de données Microsoft Access](https://www.microsoft.com/download/details.aspx?id=54920), qui vous permet de lire et écrire dans les fichiers existants dans Office 2003 (.mdb et .xls) ou les formats de fichier Office 2007 (*.accdb ; *.xlsm ; *.xlsx et *.xlsb).

  > [!IMPORTANT]
  > Veuillez lire le contrat de licence utilisateur final de 2007 Office System pour les restrictions d’utilisation spécifiques.

  > [!NOTE]
  > Applications SQL Server peuvent également accéder à Office System 2007 et précédemment, les fichiers à partir de la connectivité de données hétérogènes de SQL Server et Integration Services, les fonctionnalités via le pilote du système Office 2007. En outre, les applications de SQL Server 64 bits peuvent accéder à Jet de 32 bits et des fichiers Office System 2007 à l’aide de 32 bits SQL Server Integration Services (SSIS) sur 64 bits Windows.

* **MSDADS :** avec le fournisseur Microsoft OLE DB pour les données de mise en forme (MSDADS), vous pouvez créer des relations hiérarchiques entre les clés, des champs ou des ensembles de lignes dans une application. Aucun principales améliorations fonctionnelles n’ont été apportées depuis MDAC 2.1. Ce fournisseur a été déconseillé. Microsoft recommande d’utiliser XML, au lieu de MSDADS.
* **Oracle ODBC et OLE DB pour Oracle :** le pilote Microsoft Oracle ODBC (ODBC Oracle) et le fournisseur Microsoft OLE DB pour Oracle (Oracle OLE DB) fournissent un accès aux serveurs de base de données Oracle. Ils sont générés à l’aide de l’Interface OCI (Oracle Call) version 7 et fournissent une prise en charge complète pour Oracle 7. En outre, il utilise une émulation de Oracle 7 pour fournir la prise en charge limitée pour les bases de données Oracle 8. Oracle prend en charge n’est plus les applications qui utilisent des appels de la version 7 OCI. Ces technologies sont déconseillés. Si vous utilisez des sources de données Oracle, vous devez migrer au fournisseur et le pilote Oracle.
* **RDS:** Services de données à distance (RDS) est un mécanisme propriétaire de Microsoft pour accéder à des objets ADO Recordset distants via Internet ou un Intranet. Services Bureau à distance est déconseillé ; Aucun principales améliorations fonctionnelles n’apportées à des services Bureau à distance depuis MDAC 2.1. Microsoft a publié le .NET Framework, qui dispose de fonctionnalités étendues de SOAP et remplace les composants des services Bureau à distance. Tous les composants de serveur Services Bureau à distance seront supprimés à partir du système d’exploitation après Windows 7.
* **JRO :** objets de réplication Jet (JRO) est déconseillée. JRO est utilisé au sein d’ADO avec Jet (*.mdb) bases de données pour créer et de compresser les bases de données Jet (.mdb) et d’effectuer la gestion de la réplication Jet. MDAC 2.7 sera sa dernière version. JRO ne sera pas disponible sur le système d’exploitation de Windows 64 bits. JRO n’est pas pris en charge dans le format de fichier Microsoft Access 2007 (*.accdb).
* **prise en charge de 16 bits ODBC :** si vous utilisez des applications 16 bits, vous devez migrer vers une application 32 bits. fonctionnalités de 16 bits sont déconseillée et sont en cours de suppression à partir de systèmes d’exploitation 64 bits. Pour plus d’informations, consultez [l’article 896458 de la Base de connaissances](https://support.microsoft.com/kb/896458).
* **Fournisseur OLEDB Simple (MSDAOSP) :** fournisseur Simple OLE DB offre une infrastructure permettant de créer rapidement des fournisseurs OLE DB sur les données simples. MSDAOSP est déconseillée.
* **Bibliothèque de curseurs ODBC :** bibliothèque de curseurs ODBC (ODBCCR32.dll) fournit les curseurs côté client des données limitées. Bibliothèque de curseurs ODBC est déconseillée ; votre application peut utiliser des implémentations de curseur côté serveur en remplacement.
* **Communication à distance de Interface OLE DB Out-of-Process :** remoting OLEDB Interface (msdaps.dll) a eu une tentative pour permettre aux fournisseurs OLE DB exécuter en dehors du processus. Communication à distance OLEDB Out-of-Process Interface est déconseillée.
* **AppleTalk et bibliothèques de réseau Banyan Vines SQL :** The Banyan Vines, AppleTalk, ServerNet, IPX/SPX, Giganet et RPC SQL bibliothèques réseau sont déconseillés. Si vous utilisez l’un de ces technologies, vous devez modifier vos applications pour utiliser une des autres bibliothèques réseau, tels que TCP/IP et canaux nommés.

### <a name="mdacwdac-releases"></a>Versions MDAC/WDAC

Voici une liste des scénarios de prise en charge des versions antérieures de MDAC/WDAC, en commençant par la première.

* **MDAC 1.5, MDAC 2.0 et 2.1 de MDAC :** ces versions de MDAC ont été mises en production indépendants qui ont été publiées par Microsoft Windows NT Option Pack, le SDK de plate-forme Microsoft Windows ou le site Web de MDAC. Ces versions de MDAC ne sont plus prises en charge.
* **MDAC 2.5:** Cette version de MDAC était incluse dans le système d’exploitation Windows 2000. Service packs de MDAC 2.5 étaient inclus avec Windows 2000 service packs correspondants.
* **MDAC 2.6:** MDAC 2.6 RTM, SP1 et SP2 ont été inclus avec Microsoft SQL Server 2000 RTM, SP1 et SP2, respectivement. En outre, ces MDAC service packs ont été publiés sur le site Web de MDAC conformément à la planification de la version du service pack Microsoft SQL Server 2000. Vous pouvez installer cette version de MDAC et ses service packs sur des plates-formes Windows 2000, Windows Millennium Edition, Windows NT, Windows 95 et Windows 98. Cette version de MDAC n’est plus est pris en charge.
* **MDAC 2.7:** Cette version de MDAC était fournie avec les systèmes d’exploitation Microsoft Windows XP RTM et SP1. Vous pouvez installer cette version de MDAC et ses service packs sur des plates-formes Windows 2000, Windows Millennium, Windows NT et Windows 98. Vous pouvez installer cette version sur la plateforme Windows XP uniquement via le système d’exploitation ou de ses packs de services. Cette version de MDAC n’est plus est pris en charge.
* **MDAC 2.8:** Cette version de MDAC était inclus avec Windows Server 2003 et Windows XP SP2 et versions ultérieures. Vous pouvez également installer cette version de MDAC et ses service packs Windows 2000.

  * La version 32 bits de MDAC 2.8 également publiée sur le site Web de MDAC en même temps que Windows Server 2003 a été livré au client.
  * La version 64 bits de MDAC 2.8 a été publiée avec la version 64 bits de Windows Server 2003 et Windows XP.

* **Windows Data Access Components (WDAC) :** MDAC appelle désormais WDAC - « Windows Data Access Components » en commençant par Windows Vista et Windows Server 2008. WDAC est inclus dans le système d’exploitation et n’est pas disponible pour la redistribution séparément. Facilité de maintenance pour WDAC est susceptible du cycle de vie du système d’exploitation.

  versions 32 bits et 64 bits de WDAC sont publiées avec les versions 32 bits et 64 bits des systèmes d’exploitation Windows, respectivement.

## <a name="obsolete-data-access-technologies"></a>Technologies d’accès aux données obsolètes

Technologies obsolètes sont des technologies pas améliorés ou mis à jour dans plusieurs versions de produit et qui doivent être exclus de versions ultérieures du produit. N’utilisez pas ces technologies lorsque vous écrivez de nouvelles applications. Lorsque vous modifiez des applications existantes qui sont écrits à l’aide de ces technologies, envisagez de migrer ces applications sur ADO.NET ou une autre technologie actuelle.

Les composants suivants sont considérés comme obsolètes :

* **DB-Library:** DB-Library est un modèle de programmation spécifiques à SQL Server qui inclut les API C. Des améliorations ont été aucune fonctionnalité à la bibliothèque de base de données depuis SQL Server 6.5. Sa version finale était avec SQL Server 2000, et il ne sera pas déplacée au système d’exploitation Windows 64 bits.
* **Embedded SQL (E-SQL) :** E-SQL est un modèle de programmation spécifiques à SQL Server qui permet des instructions Transact-SQL d’être incorporés dans le code Visual C. Aucune amélioration de fonctionnalité n’ont été apportées à l’E-SQL depuis SQL Server 6.5. Sa version finale était avec SQL Server 2000, et il ne sera pas déplacée au système d’exploitation Windows 64 bits.
* **Data Access Objects (DAO) :** DAO fournit l’accès aux bases de données JET (accès). Cette API peut être utilisée à partir de Microsoft Visual Basic, Microsoft Visual C++ et les langages de script. Il était inclus dans Microsoft Office 2000 et Office XP. DAO 3.6 est la version finale de cette technologie. Il ne sera pas disponible sur le système d’exploitation de Windows 64 bits.
* **Objets de données à distance (RDO) :** RDO a été conçu spécifiquement pour accéder aux sources de données relationnelles distantes ODBC et le rendre plus facile à utiliser ODBC sans code d’application complexes. Il était inclus dans les versions de Microsoft Visual Basic 4, 5 et 6. RDO version 2.0 était la version finale de cette technologie.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
