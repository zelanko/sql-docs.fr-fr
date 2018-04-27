---
title: Mise à jour - Documentation d’Integration Services pour SQL Server | Microsoft Docs
description: Affichez des extraits de contenu mis à jour récemment dans la documentation d’Integration Services pour Microsoft SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql
ms.component: ssis
ms.date: 02/03/2018
ms.openlocfilehash: ff4632e6e26c702ab85ef70955e0b3eed3a281c7
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="new-and-recently-updated-integration-services-for-sql-server"></a>Nouveau et mis à jour récemment : Integration Services pour SQL Server



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **03-12-2017** &nbsp; au &nbsp; **03-02-2018**
- *Domaine :* &nbsp; **Integration Services pour SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Parcourir tous les principaux, boîte de dialogue](catalog/browse-all-principals-dialog-box.md)
2. [Boîte de dialogue Configurer](catalog/configure-dialog-box.md)
3. [Propriétés du dossier, boîte de dialogue](catalog/folder-properties-dialog-box.md)
4. [Référence de Transact-SQL catalogue Integration Services (SSIS)](catalog/integration-services-ssis-catalog-transact-sql-reference.md)
5. [Serveur et catalogue Integration Services (SSIS)](catalog/integration-services-ssis-server-and-catalog.md)
6. [Propriétés du package, boîte de dialogue](catalog/package-properties-dialog-box.md)
7. [Propriétés du projet, boîte de dialogue](catalog/project-properties-dialog-box.md)
8. [Boîte de dialogue de versions du projet](catalog/project-versions-dialog-box.md)
9. [Boîte de dialogue Définir la valeur du paramètre](catalog/set-parameter-value-dialog-box.md)
10. [Catalogue SSIS](catalog/ssis-catalog.md)
11. [Boîte de dialogue Valider](catalog/validate-dialog-box.md)
12. [Afficher la liste des packages sur le serveur Integration Services](catalog/view-the-list-of-packages-on-the-integration-services-server.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Planifier l’exécution d’un package SSIS sur Azure](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-schedule-the-execution-of-an-ssis-package-on-azurelift-shiftssis-azure-schedule-packagesmd"></a>1. &nbsp; [Planifier l’exécution d’un package SSIS sur Azure](lift-shift/ssis-azure-schedule-packages.md)

*Mise à jour : 18-01-2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 28.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 be778f8096559da9b84670382deb11f56c129971 640dd3cb59a88ccbc4cf6eab363a45e284f6b873  (PR=4662  ,  Filename=ssis-azure-schedule-packages.md  ,  Dirpath=docs\integration-services\lift-shift\  ,  MergeCommitSha40=6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f) -->



Avant de pouvoir utiliser SQL Server Agent localement pour planifier l’exécution des packages stockés sur un serveur Azure SQL Database, vous devez ajouter le serveur SQL Database à votre serveur SQL Server local en tant que serveur lié.

1.  **Configurer le serveur lié**

    ```
    -- Add the SSISDB database on your Azure SQL Database as a linked server to your SQL Server on premises
    EXEC sp_addlinkedserver
        @server='myLinkedServer', -- Name your linked server
        @srvproduct='',
        @provider='sqlncli', -- Use SQL Server native client
        @datasrc='<server_name>.database.windows.net', -- Add your Azure SQL Database server endpoint
        @location='',
        @provstr='',
        @catalog='SSISDB'  -- Add SSISDB as the initial catalog
    ```

2.  **Configurer les informations d’identification du serveur lié**

    ```
    -- Add your Azure SQL DB server admin credentials
    EXEC sp_addlinkedsrvlogin
        @rmtsrvname = 'myLinkedServer',
        @useself = 'false',
        @rmtuser = 'myUsername', -- Add your server admin username
        @rmtpassword = 'myPassword' -- Add your server admin password
    ```

3.  **Configurer les options du serveur lié**

    ```
    EXEC sp_serveroption 'myLinkedServer', 'rpc out', true;
    ```

Pour plus d’informations, consultez [Créer des serveurs liés](lift-shift/../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md) et [Serveurs liés](lift-shift/../../relational-databases/linked-servers/linked-servers-database-engine.md).







## <a name="similar-articles-about-new-or-updated-articles"></a>Articles similaires sur les articles nouveaux ou mis à jour

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Domaines *avec* des articles nouveaux ou mis à jour récemment


- [Nouveaux + Mis à jour (1 + 3) :&nbsp; **Analytique avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (0 + 1) :&nbsp; **Système de la plateforme d’analyse pour SQL** (documentation)](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nouveaux + Mis à jour (0 + 1) :&nbsp; **Connexion à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (0 + 1) :&nbsp; **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (12 + 1) :**Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (6 + 2) :&nbsp; **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (15 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (2 + 9) :&nbsp; **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (1 + 0) :&nbsp; **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (1 + 1) :&nbsp; **SQL Operations Studio** (documentation)](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nouveaux + Mis à jour (1 + 1) :&nbsp; **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (0 + 1) :&nbsp; **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (1 + 2) :&nbsp; **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (0 + 2) :&nbsp; **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Domaines *sans* article nouveau ou mis à jour récemment


- [Nouveaux + Mis à jour (0 + 0) : **Data Migration Assistant (DMA) pour SQL** (documentation)](../dma/new-updated-dma.md)
- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **Exemples pour SQL** (documentation)](../samples/new-updated-samples.md)
- [Nouveaux + Mis à jour (0 + 0) : **SQL Server Migration Assistant (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)


