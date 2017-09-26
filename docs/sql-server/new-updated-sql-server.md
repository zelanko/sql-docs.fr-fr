---
title: "Mise à jour de la documentation de SQL Server | Microsoft Docs"
description: "Affichage d’extraits du contenu mis à jour pour les modifications récentes de la documentation pour SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: sql-server
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 7f1c64e11e1bec44a558cec10c3d1f90f4951dfd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/21/2017

---
# <a name="new-and-recently-updated-sql-server-docs"></a>Nouveautés et mises à jour récentes : documentation de SQL Server



Presque tous les jours, Microsoft met à jour certains de ses articles existants sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **18-07-2017** &nbsp; au &nbsp; **11-09-2017**
- *Domaine :* &nbsp; **SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [SQL Server 2008 R2 SP2 Release Notes](sql-server-2008-r2-sp2-release-notes.md)
2. [Notes de publication de SQL Server 2012](sql-server-2012-release-notes.md)
3. [SQL Server 2012 SP1 Release Notes](sql-server-2012-sp1-release-notes.md)
4. [SQL Server 2012 SP2 Release Notes](sql-server-2012-sp2-release-notes.md)
5. [Notes de publication de SQL Server 2012 SP3](sql-server-2012-sp3-release-notes.md)
6. [SQL Server 2014 Release Notes](sql-server-2014-release-notes.md)
7. [Visionneuse d’aide et contenu hors connexion pour SQL Server](sql-server-help-installation.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Nouveautés de SQL Server 2016](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-whats-new-in-sql-server-2016what-s-new-in-sql-server-2016md"></a>1. &nbsp;[Nouveautés de SQL Server 2016](what-s-new-in-sql-server-2016.md)

*Mise à jour : 2017-09-08* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 34.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e5bc0c05f120289f09a535400a4d521e4113ae55 0607d0a9af1c9a8dd9d3d7b0606895ff23bbffdc  (PR=0  ,  Filename=what-s-new-in-sql-server-2016.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=b97cc9723d563b19c85661f5ad7049a96fc904ff) -->



- Téléchargez **gratuitement** [**SQL Server 2016 Developer Edition**](https://www.microsoft.com/en-us/cloud-platform/sql-server-editions-developers).
- Téléchargez la dernière version de [SQL Server Management Studio (SSMS)](/sql-docs/docs/ssms/download-sql-server-management-studio-ssms).
- Vous avez un compte Azure ? Faites tourner une [machine virtuelle sur laquelle SQL Server 2016 est déjà installé](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/).

**Moteur de base de données SQL Server 2016**

- Il est à présent possible de configurer plusieurs fichiers de base de données **tempDB** pendant l’installation et la configuration de SQL Server.
- Le nouveau **Magasin des requêtes** stocke le texte des requêtes, les plans d’exécution et les indicateurs de performances dans la base de données, ce qui facilite le monitoring et la résolution des problèmes de performances. Un tableau de bord affiche les requêtes qui ont consommé le plus de temps, de mémoire ou de ressources du processeur.
- Les **tables temporelles** sont des tables d’historique qui enregistrent toutes les modifications de données, avec la date et l’heure auxquelles elles se sont produites.
- La nouvelle **prise en charge de JSON** intégrée à SQL Server gère les importations, les exportations, l’analyse et le stockage JSON.
- Le nouveau moteur d’interrogation **PolyBase** intègre SQL Server avec des données externes dans Hadoop ou le Stockage Blob Azure. Vous pouvez importer et exporter des données, de même qu’exécuter des requêtes.
- La nouvelle fonctionnalité **Stretch Database** permet d’archiver des données, de manière dynamique et en toute sécurité, d’une base de données SQL Server locale vers une base de données SQL Azure dans le cloud. SQL Server interroge automatiquement les données locales et distantes dans les bases de données liées.
- **OLTP en mémoire :**
    - prend maintenant en charge les contraintes FOREIGN KEY, UNIQUE et CHECK, les procédures stockées compilées natives OR, NOT, SELECT DISTINCT et OUTER JOIN et les sous-requêtes dans SELECT ;
    - prend en charge des tables d’une taille pouvant atteindre 2 To (à partir de 256 Go) ;
    - a fait l’objet d’améliorations des index columnstore pour le tri et la prise en charge des groupes de disponibilité AlwaysOn.
- Nouvelles fonctionnalités de sécurité :
    - **Always Encrypted :** lorsqu’elle est activée, seule l’application qui possède la clé de chiffrement peut accéder aux données sensibles chiffrées de la base de données SQL Server 2016. La clé n’est jamais transmise à SQL Server.







## <a name="similar-articles"></a>Articles similaires

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Zones de sujet avec des articles nouveaux ou mis à jour récemment

- [Nouveaux + Mis à jour (3 + 12) : **Analytique avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (5 + 0) : **Se connecter à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (5 + 1) : **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (19 + 82) : **Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (1 + 8) : **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (12 + 1) : **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (0 + 1) : **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (7 + 1) : **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (1 + 1) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (0 + 2) : **SQL Server Migration Assistant (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (1 + 4) : **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (4 + 1) : **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)
- [Nouveaux + Mis à jour (0 + 1) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Zones de sujet sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)



