---
title: "Mise à jour - Documentation de SSMS pour SQL Server | Microsoft Docs"
description: "Affichez des extraits de contenu mis à jour récemment dans la documentation, pour SQL Server Management Studio (SSMS) pour Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: 
ms.component: ssms
ms.suite: sql
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: 
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.author: genemi
ms.workload: ssms-sql-server-management-studio
ms.openlocfilehash: b156ff82b18ab7ffb75ca79b57f324244f759bf5
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="new-and-recently-updated-sql-server-management-studio-ssms-for-sql-server"></a>Nouveautés et mises à jour récentes : SQL Server Management Studio (SSMS) pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


Presque tous les jours, Microsoft met à jour certains de ses articles existants sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **28-09-2017** &nbsp; au &nbsp; **02-12-2017**
- *Domaine :* &nbsp; **SQL Server Management Studio (SSMS)**.




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

1. [SQL Server Management Studio : journal des modifications (SSMS)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-management-studio---changelog-ssmssql-server-management-studio-changelog-ssmsmd"></a>1. &nbsp; [SQL Server Management Studio - Journal des modifications (SSMS)](sql-server-management-studio-changelog-ssms.md)

*Mise à jour : 09-10-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 23.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f483a7e0ba53cff80d3f2d33c9196906d27a7a61 c125f43f0a45e70ce180e62edecc68bdcffd5086  (PR=3441  ,  Filename=sql-server-management-studio-changelog-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=29122bdf543e82c1f429cf401b5fe1d8383515fc) -->



**[SSMS 17.3--download-sql-server-management-studio-ssms.md)**

Disponibilité générale | Numéro de build : 14.0.17199.0

**Améliorations**


- Ajout du nouvel Assistant « Importer un fichier plat » pour simplifier l’importation des fichiers CSV avec une infrastructure intelligente, nécessitant une intervention de l’utilisateur ou des connaissances techniques minimes. Pour plus d’informations, consultez [Assistant Importation d’un fichier plat dans SQL--../relational-databases/import-export/import-flat-file-wizard.md).
- Ajout du nœud « XEvent Profiler » à l’Explorateur d’objets. Pour plus d’informations, consultez [Utiliser SSMS XEvent Profiler--../relational-databases/extended-events/use-the-ssms-xe-profiler.md).
- Mise à jour du filtrage et de la catégorisation des attentes dans le rapport des attentes historiques du Tableau de bord Performances.
- Ajout de la vérification syntaxique de la fonction « Predict ».
- Ajout de la vérification syntaxique des requêtes External Library Management.
- Ajout de la prise en charge SMO pour External Library Management.
- Ajout de la prise en charge de « Démarrer PowerShell » dans la fenêtre « Serveurs inscrits » (nécessite un nouveau module SQL PowerShell).
- Always On : Ajout de la [prise en charge du routage en lecture seule--../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md) pour les groupes de disponibilité.
- Ajout d’une option pour envoyer les informations de trace dans la fenêtre Sortie pour les connexions « Active Directory - Authentification universelle avec prise en charge de MFA » (option désactivée par défaut ; doit être activée dans les paramètres utilisateur sous « Outils > Options > Services Azure > Azure Cloud > Niveau de trace dans la fenêtre Sortie ADAL »).
- Magasin des requêtes :
  - L’interface utilisateur Magasin des requêtes est maintenant accessible même quand QDS est désactivé, si QDS a enregistré des données.
  - L’interface utilisateur Magasin des requêtes expose maintenant les attentes par catégorie dans tous les rapports existants. Cela permet aux clients de gérer les scénarios avec des requêtes principales en attente, par exemple.
- Ajout des en-têtes de paramètres de script rendu facultatif (désactivé par défaut ; peut être activé dans les paramètres utilisateur sous « Outils > Options > Explorateur d’objets SQL Server > Scripts > Inclure l’en-tête des paramètres de script ») - [Article Connect 3139199](https://connect.microsoft.com/SQLServer/feedback/details/3139199).







## <a name="similar-articles"></a>Articles similaires

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Zones de sujet avec des articles nouveaux ou mis à jour récemment

- [Nouveaux + Mis à jour (3 + 14) : **Analytique avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (1 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + mis à jour (87 + 0) : **Système de la plateforme d’analyse pour SQL** (documentation)](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nouveaux + Mis à jour (5 + 4) : **Connexion à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (0 + 1) : **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (2 + 2) : **Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (10 + 9) : **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (2 + 4) : **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (4 + 2) : **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (0 + 1) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + mis à jour (0 + 21)  : **SQL Operations Studio** (documentation)](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nouveaux + Mis à jour (5 + 1) : **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (1 + 0) : **Assistant Migration SQL Server (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (0 + 2) : **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Zones de sujet sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **Data Migration Assistant (DMA) pour SQL** (documentation)](../dma/new-updated-dma.md)
- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)


