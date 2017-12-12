---
title: "Mise à jour - Documentation de SSDT pour SQL Server | Microsoft Docs"
description: "Affichez des extraits de contenu mis à jour récemment dans la documentation pour SQL Server Data Tools (SSDT) pour Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: 
ms.component: ssdt
ms.suite: sql
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.author: genemi
ms.workload: ssdt-sql-server-data-tools
ms.openlocfilehash: 07bfbac52cdd7d118ffd58842fe2085d52265e6f
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="new-and-recently-updated-sql-server-data-tools-ssdt"></a>Nouveautés et mises à jour récentes : SQL Server Data Tools (SSDT)



Presque tous les jours, Microsoft met à jour certains de ses articles existants sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **28-09-2017** &nbsp; au &nbsp; **02-12-2017**
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

*Mise à jour : 20-11-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 28.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7700cae7cafe1dac95c240b014f14d9c83e32be4 6416949beaee91da2f77dfebb9eb5ed363db4cb7  (PR=4032  ,  Filename=changelog-for-sql-server-data-tools-ssdt.md  ,  Dirpath=docs\ssdt\  ,  MergeCommitSha40=7f8aebc72e7d0c8cff3990865c9f1316996a67d5) -->




**SSDT pour Visual Studio 2017 (préversion 15.4.0)**

Numéro de build : 14.0.16134.0

**Nouveautés**


Cette version fournit un programme d’installation web autonome pour les projets de base de données SQL Server, Analysis Services, Reporting Services et Integration Services dans Visual Studio 2017 15.4 ou ultérieur.

**Programme d’installation**


- L’utilisateur peut donner un surnom quand il installe une nouvelle instance de SSDT pour VS2017.
- Les cases à cocher de sélection de fonctionnalité du programme d’installation sont masquées si aucune instance de Visual Studio n’est sélectionnée.
- Certains messages du programme d’installation ont été affinés en réponse aux commentaires des clients.
- Un problème empêchant le programme d’installation de prendre en charge la mise à niveau a été résolu.


**SSIS**


- Résolution d’un problème empêchant l’Assistant Importation/Exportation de répertorier la source de données quand le Feature Pack Azure est installé.
- Résolution d’un problème où la modification d’une tâche de processus SSIS Analysis Services levait une exception au changement de connexion.
- Résolution d’un problème qui entraînait la rupture de composants CDC après l’application du correctif SQL qui ajoute la colonne __$command_id.
- Résolution d’un problème empêchant la modification et l’exécution d’un package tiers si une ancienne version de SQL Server est ciblée.
- Résolution d’un problème empêchant d’afficher correctement la boîte de dialogue de configuration Source du fichier plat quand l’utilisateur double-cliquait sur DTSWizard.exe et sélectionnait Source du fichier plat.
- Résolution d’un problème empêchant l’exécution d’un package contenant un composant/une tâche Feature Pack Azure quand SQL Server 2017 était ciblé.


**Problèmes connus**

- Le programme d’installation n’est pas localisé.
- La tâche d’exécution de package SSIS ne prend pas en charge le débogage quand *ExecuteOutOfProcess* a la valeur True. Ce problème s’applique uniquement au débogage. L’enregistrement, le déploiement et l’exécution via DTExec.exe ou le catalogue SSIS ne sont pas impactés.


**SSDT 17.3 pour Visual Studio 2015**

Numéro de build : 14.0.61709.290

**Nouveautés**


**Analysis Services (AS)**

- Cosmos DB et HDI Spark sont activés dans les modèles 1400.
- Propriétés des sources de données tabulaires.
- L’option « Requête vide » est maintenant disponible quand vous créez une requête dans l’éditeur de requête pour les modèles de niveau de compatibilité 1400.
- L’éditeur de requête pour les modèles 1400 permet désormais d’enregistrer des requêtes sans nouvelles tables traitées automatiquement.







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
- [Nouveaux + Mis à jour (87 + 0) : **Système de la plateforme d’analyse pour SQL** (documentation)](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nouveaux + Mis à jour (5 + 4) : **Connexion à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (0 + 1) : **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (2 + 2) : **Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (10 + 9) : **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (2 + 4) : **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (4 + 2) : **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (0 + 1) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (0 + 21)  : **SQL Operations Studio** (documentation)](../sql-operations-studio/new-updated-sql-operations-studio.md)
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


