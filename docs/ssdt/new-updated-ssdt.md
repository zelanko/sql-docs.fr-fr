---
title: Mise à jour - Documentation de SSDT pour SQL Server | Microsoft Docs
description: Affichez des extraits de contenu mis à jour récemment dans la documentation pour SQL Server Data Tools (SSDT) pour Microsoft SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql
ms.component: ssdt
ms.date: 02/03/2018
ms.openlocfilehash: 2b754531dd25a21444a24a30af14f528ec26a170
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="new-and-recently-updated-sql-server-data-tools-ssdt"></a>Nouveautés et mises à jour récentes : SQL Server Data Tools (SSDT)



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **03-12-2017** &nbsp; au &nbsp; **03-02-2018**
- *Domaine :* &nbsp; **SQL Server Data Tools (SSDT)**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


***Il n’y a aucun nouvel article pour cette fois.***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Journal des modifications de SQL Server Data Tools (SSDT)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-changelog-for-sql-server-data-tools-ssdtchangelog-for-sql-server-data-tools-ssdtmd"></a>1. &nbsp; [Journal des modifications de SQL Server Data Tools (SSDT)](changelog-for-sql-server-data-tools-ssdt.md)

*Mise à jour : 18-01-2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 28.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6416949beaee91da2f77dfebb9eb5ed363db4cb7 de18314845cffa197b3fd2ed868f2c330760bedb  (PR=4652  ,  Filename=changelog-for-sql-server-data-tools-ssdt.md  ,  Dirpath=docs\ssdt\  ,  MergeCommitSha40=6b4aae3706247ce9b311682774b13ac067f60a79) -->



**SSDT pour Visual Studio 2017 (15.5.1)**

Numéro de build : 14.0.16148.0

**Nouveautés**


Visual Studio 2017 (15.5.1) est la même version que la version 15.5.0 à l’exception des résolutions de bogues suivantes appliquées au programme d’installation :

1.  Résolution d’un problème qui entraîne le blocage du programme d’installation lors de la post-installation de SQL Server Integration Services.
2.  Résolution d’un problème qui entraîne l’échec de l’installation avec le message d’erreur suivant : « L’opération de métafichier demandée n’est pas prise en charge (0x800707D3) ».

En plus de ces deux résolutions de bogues, les détails suivants pour 15.5.0 s’appliquent toujours à 15.5.1

**SSDT pour Visual Studio 2017 (15.5.0)**

Numéro de build : 14.0.16146.0

**Nouveautés**


SSDT pour Visual Studio 2017 (15.5.0) qui était en préversion est désormais en disponibilité générale.

**Programme d’installation**
1. L’interface utilisateur du programme d’installation est localisée.
1. L’icône est remplacée par une version de qualité supérieure.

**Integration Services (IS)**
1. Ajout d’une étape de validation de package dans l’Assistant Déploiement lors du déploiement sur le runtime d’intégration Azure-SSIS dans ADF, ce qui permet de détecter les éventuels problèmes de compatibilité dans les packages SSIS à exécuter dans le runtime d’intégration Azure-SSIS. Pour plus d’informations, consultez [Valider des packages SSIS déployés sur Azure](..\integration-services\lift-shift\ssis-azure-validate-packages.md).
1. L’extension SSIS est localisée.

**Correctifs de bogues**


**Integration Services (IS)**
1. Résolution d’un problème qui entraîne l’endommagement de la disposition du gestionnaire de connexions OLE DB et ADO.NET.
2. Résolution d’un problème qui entraîne l’affichage d’une erreur d’assembly introuvable lors de la tentative de modification d’une tâche de traitement de dimension.

**Problèmes connus**


**IS (Integration Services)** La tâche d’exécution de package SSIS ne prend pas en charge le débogage quand ExecuteOutOfProcess a la valeur True. Ce problème s’applique uniquement au débogage. L’enregistrement, le déploiement et l’exécution via DTExec.exe ou le catalogue SSIS ne sont pas impactés.



**SSDT 17.4 pour Visual Studio 2015**

Numéro de build : 14.0.61712.050

**Nouveautés**


**Projets AS (Analysis Services)**
- Ajout de trois nouvelles options aux projets tabulaires (sous Options > Analysis Services (tabulaire) > Importation des données) :







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


