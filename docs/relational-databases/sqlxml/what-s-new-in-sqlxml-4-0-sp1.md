---
title: Nouveautés&#39;dans SQLXML 4,0 SP1
description: Affichez un résumé des mises à jour et améliorations de SQLXML 4,0 SP1 avec des liens vers des informations plus détaillées.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- registry keys [SQLXML]
- SQLNCLI, SQLXML
- what's new [SQLXML]
- SQLXML, what's new
- migrating SQLXML applications
- redistributing SQLXML
- SQL Server Native Client, SQLXML
- side-by-side installations [SQLXML]
ms.assetid: 48f7720b-1705-402d-93ce-097ff1737877
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cdb176233f3490daa428e7cf6bb8f7c9b0b58255
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85665606"
---
# <a name="what39s-new-in-sqlxml-40-sp1"></a>Nouveautés&#39;dans SQLXML 4,0 SP1
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0 SP1 inclut différentes mises à jour et améliorations. Cette rubrique résume les mises à jour et fournit, le cas échéant, des liens vers des pages contenant des informations plus détaillées. SQLXML 4.0 SP1 fournit des améliorations supplémentaires pour prendre en charge les nouveaux types de données présentés dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]. Cette rubrique traite des sujets suivants :  
  
-   Installation de SQLXML 4.0 SP1  
  
-   Problèmes liés à l'installation côte à côte  
  
-   SQLXML 4.0 et MSXML  
  
-   Redistribution de SQLXML 4.0  
  
-   Prise en charge de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  
  
-   Prise en charge des types de données introduits dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
-   Modifications apportées au chargement en masse XML pour SQLXML 4.0  
  
-   Modifications apportées aux clés de Registre pour SQLXML 4.0  
  
-   Problèmes de migration  
  
## <a name="installing-sqlxml-40-sp1"></a>Installation de SQLXML 4.0 SP1  
 Avant [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 était fourni avec SQL Server et faisait partie de l'installation par défaut de toutes les versions de SQL Server, à l'exception de SQL Server Express. À partir de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], la dernière version de SQLXML (SQLXML 4.0 SP1) n'est plus incluse dans SQL Server. Pour installer SQLXML 4,0 SP1, téléchargez-le à partir de l' [emplacement d’installation de sqlxml 4,0 SP1](https://www.microsoft.com/download/details.aspx?id=30403).  
  
 Les fichiers SQLXML 4.0 SP1 sont installés à l'emplacement suivant :  
  
 `%PROGRAMFILES%\SQLXML 4.0\`  
  
> [!NOTE]  
>  Tous les paramètres du Registre appropriés pour SQLXML 4.0 sont définis dans le cadre de la procédure d'installation.  
  
 Pour permettre l'exécution des applications SQLXML 32 bits sous WOW64 (Windows on Windows64) sur les systèmes d'exploitation Windows 64 bits, exécutez le package SQLXML 4.0 SP1 64 bits, nommé sqlxml4.msi, qui se trouve sur le Centre de téléchargement.  
  
#### <a name="uninstalling-sqlxml-40-sp1"></a>Désinstallation de SQLXML 4.0 SP1  
 Il existe des clés de Registre partagées entre SQLXML 3.0 SP3, SQLXML 4.0 et SQLXML 4.0 SP1. Si les versions ultérieures de SQLXML sont désinstallées sur le même ordinateur qui contient SQLXML 3.0 SP3, il est possible que vous deviez réinstaller SQLXML 3.0 SP3.  
  
## <a name="side-by-side-installation-issues"></a>Problèmes liés à l'installation côte à côte  
 La procédure d'installation de SQLXML 4.0 ne supprime pas les fichiers installés par les versions antérieures de SQLXML. Par conséquent, les DLL de différentes installations de SQLXML avec des versions distinctes peuvent figurer sur votre ordinateur. Vous pouvez exécuter les installations côte à côte. SQLXML 4.0 inclut des PROGID dépendants et indépendants de la version. Toutes les applications de production doivent utiliser des PROGID dépendants de la version.  
  
## <a name="sqlxml-40-sp1-and-msxml"></a>SQLXML 4.0 SP1 et MSXML  
 SQLXML 4.0 n'installe pas MSXML. SQLXML 4.0 utilise MSXML 6.0, qui est installé dans le cadre de l'installation de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure.  
  
## <a name="redistributing-sqlxml-40-sp1"></a>Redistribution de SQLXML 4.0 SP1  
 Vous pouvez distribuer SQLXML 4.0 SP1 en utilisant le package du programme d'installation redistribuable. Une façon d'installer plusieurs packages dans ce qui paraît à l'utilisateur être une installation unique consiste à utiliser la technologie des programmes de chaînage et d'amorçage. Pour plus d'informations, consultez Création d'un package de programme d'amorçage personnalisé pour Visual Studio 2005 et Ajout de composants requis personnalisés.  
  
 Si votre application vise une plateforme autre que celle sur laquelle elle a été développée, vous pouvez télécharger les versions de sqlncli.msi pour x64, Itanium et x86 à partir du Centre de téléchargement Microsoft.  
  
 Il existe également des programmes d'installation de redistribution séparés pour MSXML 6.0 (msxml6.msi). Ceux-ci se trouvent sur le CD d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'emplacement suivant :  
  
 `%CD%\Setup\`  
  
 Ces fichiers d'installation peuvent être utilisés pour installer MSXML 6.0 directement à partir du CD. Ils peuvent également être utilisés pour redistribuer librement MSXML 6.0 et SQLXML 4.0 SP1 avec vos propres applications personnalisées.  
  
 Vous devrez également redistribuer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client si vous l'utilisez comme fournisseur de données avec votre application. Pour plus d’informations, consultez [Installation de SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md).  
  
## <a name="support-for-sql-server-native-client"></a>Prise en charge de SQL Server Native Client  
 SQLXML 4,0 prend en charge les fournisseurs SQLOLEDB et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Nous vous recommandons d’utiliser la même version du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , car [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est développé pour prendre en charge tous les nouveaux types de données fournis avec le serveur, tels que les types de données **date, Time**, **datetime2**et **DateTimeOffset** dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et pris en charge par [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est une technologie d'accès aux données qui a été introduite dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Elle associe le fournisseur SQLOLEDB et le pilote SQLODBC dans une même bibliothèque de liens dynamiques (DLL), tout en proposant également de nouvelles fonctionnalités distinctes des composants MDAC (Microsoft Data Access Components).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client peut être utilisé pour créer des applications ou améliorer des applications existantes qui doivent tirer parti des fonctionnalités introduites dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui ne sont pas prises en charge par SQLOLEDB et SQLODBC dans MDAC et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Par exemple, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est requis pour que les fonctionnalités SQLXML côté client, telles que for XML, utilisent le type de données **XML** . Pour plus d’informations, consultez [mise en forme XML côté Client &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md), [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)et [programmation de SQL Server Native Client](../../relational-databases/native-client/sql-server-native-client-programming.md).  
  
> [!NOTE]  
>  SQLXML 4.0 n'assure pas une compatibilité descendante complète avec SQLXML 3.0. En raison de quelques résolutions de bogue et d'autres modifications fonctionnelles, en particulier la suppression de la prise en charge de l'interface ISAPI SQLXML, vous ne pouvez pas utiliser de répertoires virtuels IIS avec SQLXML 4.0. Bien que la plupart des applications s'exécutent avec des modifications mineures, vous devez les tester avant de les mettre en production avec SQLXML 4.0.  
  
## <a name="support-for-data-types-introduced-in-sql-server-2005-and-sql-server-2008"></a>Prise en charge des types de données introduits dans SQL Server 2005 et SQL Server 2008  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]a introduit le type de données **XML** et SQLXML 4,0 prend en charge le type de données **XML** . Pour plus d’informations, consultez [prise en charge du type de données XML dans SQLXML 4,0](../../relational-databases/sqlxml/xml-data-type-support-in-sqlxml-4-0.md).  
  
 Pour obtenir des exemples d’utilisation du type de données **XML** dans SQLXML lors du mappage de vues XML, le chargement en masse XML ou l’exécution de codes XML, reportez-vous aux exemples fournis dans les rubriques suivantes.  
  
-   [Mappage par défaut d'éléments et d'attributs XSD à des tables et des colonnes](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
-   [Insertion de données à l'aide de codes de mise à jour (updategrams) XML](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
  
-   [Exemples du chargement en masse de documents XML](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]a introduit les types de données **date, Time**, **datetime2**et **DateTimeOffset** . SQLXML 4.0 SP1 activera ces quatre nouveaux types de données sous la forme de types scalaires intégrés lors d'une utilisation avec le fournisseur OLE DB [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client (SQLNCLI11), fourni avec [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="xml-bulk-load-changes-for-sqlxml-40-sp1"></a>Modifications apportées au chargement en masse XML pour SQLXML 4.0 SP1  
  
-   Pour SQLXML 4,0, le champ de dépassement SchemaGen est créé à l’aide du type de données **XML** . Pour plus d’informations, consultez [SQL Server modèle objet de chargement en masse XML](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/sql-server-xml-bulk-load-object-model-sqlxml-4-0.md).  
  
-   Si vous avez précédemment créé des applications [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic et que vous souhaitez utiliser SQLXML 4.0, vous devez recompiler l'application avec une référence à Xblkld4.dll.  
  
-   Pour les applications Visual Basic Scripting Edition, vous devez inscrire la DLL que vous souhaitez utiliser. Dans l'exemple suivant, si vous spécifiez des PROGID indépendants de la version, l'application dépend de la dernière DLL inscrite :  
  
    ```  
    set objBulkLoad = CreateObject("SQLXMLBulkLoad.SQLXMLBulkLoad")   
    ```  
  
    > [!NOTE]  
    >  Le PROGID dépendant de la version est SQLXMLBulkLoad.SQLXMLBulkLoad.4.0.  
  
## <a name="registry-key-changes-for-sqlxml-40"></a>Modifications apportées aux clés de Registre pour SQLXML 4.0  
 Les clés de Registre ont été modifiées par rapport aux versions précédentes. Dans SQLXML 4.0, elles sont les suivantes :  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\SchemaCacheSize  
  
 Vous devez modifier les paramètres si vous souhaitez que ces clés soient appliquées pour SQLXML 4.0.  
  
 De plus, SQLXML 4.0 introduit les clés de Registre suivantes :  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\ReportErrorsWithSQLInfo`  
  
     Par défaut, SQLXML 4.0 retourne des informations d'erreur native fournies par OLE DB et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au lieu d'une erreur SQLXML de niveau supérieur (comme cela était le cas dans les versions antérieures de SQLXML). Si ce comportement ne vous convient pas, attribuez la valeur 0 à cette clé de Registre de type DWORD (la valeur par défaut est 1).  
  
-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\FORXML_GenerateGUIDBraces  
  
     Par défaut, SQLXML retourne des valeurs GUID SQL Server sans accolades de délimitation. Si vous souhaitez que la valeur GUID soit retournée avec les accolades (par exemple, {*some GUID*}), la valeur de cette clé de registre doit être définie sur 1 (la valeur par défaut est 0).  
  
-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\SQL2000CompatMode  
  
     Par défaut, lorsque l'analyseur XML charge les données, les espaces blancs sont normalisés selon les règles du langage XML 1.0. Cela entraîne la perte de quelques espaces blancs dans vos données. Par conséquent, la représentation textuelle de vos données peut ne pas être la même après l'analyse, bien que les données soient les mêmes sur le plan sémantique.  
  
     Cette clé est introduite pour que vous puissiez conserver les espaces blancs dans les données si vous le souhaitez. Si vous ajoutez cette clé de Registre et que vous lui attribuez la valeur 0, les espaces blancs (saut de ligne, retour chariot et tabulation) dans le code XML sont retournés encodés en cas de valeurs d'attribut. En cas de valeurs d'élément, seul le retour chariot est retourné encodé.  
  
     Par exemple :  
  
    ```  
    CREATE TABLE T( Col1 int, Col2 nvarchar(100));  
    GO  
    -- Insert data with tab, line feed and carriage return).  
    INSERT INTO T VALUES (1, 'This is a tab    . This is a line feed and CR   
     more text');  
    GO  
    -- Test this query (without the registry key).  
    SELECT * FROM T   
    FOR XML AUTO;  
    -- This is the result (no encoding of special characters).  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
      <T Col1="1"   
         Col2="This is a tab    . This is a line feed and CR   
     more text"/>  
    </r>  
    -- Now add registry key with value 0 and execute the query again.  
    -- Note the encoding for carriage return, line-feed and tab in the attribute value.  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
      <T Col1="1"   
         Col2="This is a tab    . This is a line feed and CR   
     more text"/>  
    </r>  
  
    -- Update the query and specify ELEMENTS directive  
    SELECT * FROM T  
    FOR XML AUTO, ELEMENTS  
    -- Only the carriage return is returned encoded.  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
       <T>  
          <Col1>1</Col1>  
          <Col2>This is a tab    . This is a line feed and CR   
     more text</Col2>  
       </T>  
    </r>  
    ```  
  
## <a name="migration-issues"></a>Problèmes de migration  
 Les problèmes suivants peuvent affecter la migration de vos applications SQLXML héritées vers SQLXML 4.0.  
  
### <a name="ado-and-sqlxml-40-queries"></a>Requêtes ADO et SQLXML 4.0  
 Dans les versions antérieures de SQLXML, l'exécution de requêtes basées sur une URL à l'aide de répertoires virtuels IIS et du filtre ISAPI SQLXML était prise en charge. Pour les applications qui utilisent SQLXML 4.0, cette prise en charge n'est plus offerte.  
  
 Au lieu de cela, les requêtes, modèles et codes de mise à jour SQLXML peuvent être exécutées à l'aide des extensions SQLXML aux objets ADO (ActiveX Data Objects) qui ont été introduites pour la première fois dans Microsoft Data Access Components (MDAC) 2.6 et versions ultérieures.  
  
 Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="supportability-for-sqlxml-30-isapi-and-data-types-introduced-in-sql-server-2005"></a>Prise en charge de l'interface ISAPI SQLXML 3.0 et des types de données introduits dans SQL Server 2005  
 Étant donné que la prise en charge d’ISAPI a été supprimée de SQLXML 4,0, si votre solution requiert les fonctionnalités de typage de données améliorées introduites dans, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] telles que le [type](../../t-sql/xml/xml-transact-sql.md) de données XML ou les [types de données définis par l’utilisateur (UDT)](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) et l’accès Web, vous devez utiliser une autre solution telle que les [classes managées SQLXML](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md) ou un autre type de gestionnaire HTTP, tel 2005 SQL Server que  
  
 Sinon, si vous n’avez pas besoin de ces extensions de type, vous pouvez continuer à utiliser SQLXML 3,0 pour vous connecter aux [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] installations de et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] . La prise en charge ISAPI de SQLXML 3,0 fonctionnera avec ces versions ultérieures, mais ne prend pas en charge ni ne reconnaît le type de données **XML** ou la prise en charge de type UDT introduite dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
### <a name="xml-bulk-load-security-changes-for-temporary-files"></a>Modifications apportées à la sécurité du chargement en masse XML pour les fichiers temporaires  
 Pour SQLXML 4.0 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les autorisations sur les fichiers de chargement en masse XML sont accordées à l'utilisateur qui exécute l'opération de chargement en masse. Les autorisations en lecture et en écriture sont héritées du système de fichiers. Dans les versions précédentes de SQLXML et de SQL Server, le chargement en masse XML sous SQLXML créait des fichiers temporaires qui n'étaient pas sécurisés et qui pouvaient être lus par n'importe qui.  
  
### <a name="migration-issues-for-client-side-for-xml"></a>Problèmes de migration pour FOR XML côté client  
 En raison des modifications apportées au moteur d’exécution, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut retourner des valeurs différentes dans les métadonnées d’une table de base, par rapport à la valeur retournée si la requête for XML a été exécutée sous [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] . Si cela se produit, la mise en forme côté client des résultats de la requête FOR XML aura une sortie différente selon la version sur laquelle la requête est exécutée.  
  
 Si une requête FOR XML est exécutée côté client à l’aide de SQLXML 3,0 sur une colonne de type de données **XML** , les données contenues dans les résultats sont renvoyées sous forme de chaîne entièrement codé. Dans SQLXML 4.0, si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) est spécifié en tant que fournisseur, les données seront retournées sous forme de données XML.  
  
  
