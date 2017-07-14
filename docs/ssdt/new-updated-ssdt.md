---
title: "Mise à jour - Documentation de SSDT pour SQL Server | Microsoft Docs"
description: "Affichez des extraits de contenu mis à jour récemment dans la documentation pour SQL Server Data Tools (SSDT) pour Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 06/30/2017
ms.author: genemi
ms.workload: ssdt-sql-server-data-tools
ms.translationtype: Human Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 5e43cb76dac922b3c43318b2a9f539ab19ec7bfe
ms.contentlocale: fr-fr
ms.lasthandoff: 07/03/2017

---
# Nouveautés et mises à jour récentes : SQL Server Data Tools (SSDT)
<a id="new-and-recently-updated-sql-server-data-tools-ssdt" class="xliff"></a>



Presque tous les jours Microsoft met à jour certains de ses articles existants sur son [Docs.Microsoft.com](http://docs.microsoft.com/) site Web de documentation. Cet article affiche des extraits d’articles récemment mis à jour. Des liens vers nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme est exécuté à nouveau régulièrement. Parfois un extrait peut apparaître avec mise en forme imparfait, ou en tant que markdown de l’article de la source. Les images ne sont jamais affichés ici.

Mises à jour récentes sont signalés pour la plage de dates suivante et l’objet :



- *Plage de dates des mises à jour :* &nbsp; **17-05-2017** &nbsp; - au - &nbsp; **30-06-2017**
- *Zone de sujet :* &nbsp; **SQL Server Data Tools (SSDT)**.




&nbsp;

## Nouveaux articles créés récemment
<a id="new-articles-created-recently" class="xliff"></a>

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


*Il n’y a aucun nouvel article.*



&nbsp;

## Articles mis à jour avec des extraits
<a id="updated-articles-with-excerpts" class="xliff"></a>

Cette section affiche les extraits de mises à jour collectées à partir des articles qui ont récemment subi une mise à jour importante.

Les extraits affichés ici apparaissent séparés à partir de leur contexte sémantique spécifique. En outre, parfois un extrait est séparé à partir de la syntaxe markdown important qui l’entoure dans l’article. Par conséquent, ces extraits sont pour des conseils généraux. Les extraits permettent uniquement de savoir si votre intérêt justifie pris le temps de cliquer sur et consultez l’article.

Pour celles-ci et d’autres raisons, ne pas copier le code à partir de ces extraits et ne prennent pas en tant que vérité exacte tout extrait de texte. Au lieu de cela, consultez l’article.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### 1. &nbsp; [Journal des modifications de SQL Server Data Tools (SSDT)](changelog-for-sql-server-data-tools-ssdt.md)
<a id="1-nbsp-changelog-for-sql-server-data-tools-ssdtchangelog-for-sql-server-data-tools-ssdtmd" class="xliff"></a>

*Date de mise à jour : 2017-05-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 21.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 cf17883ce0daf75fdf88881171bf4042558b1cf4 536fe0fe41b023a4186f494a509fa14fcbafccf4  (PR=1777  ,  Filename=changelog-for-sql-server-data-tools-ssdt.md  ,  Dirpath=docs\ssdt\  ,  MergeCommitSha40=5bd0e1d3955d898824d285d28979089e2de6f322) -->



Pour des publications détaillées sur les nouveautés et les modifications, visitez [le blog de l’équipe SSDT](https://blogs.msdn.microsoft.com/ssdt/)

**SSDT 17.1**

Numéro de build : 14.0.61705.170

**Nouveautés**

**Projets AS :**
- Les utilisateurs peuvent définir le codage des indications sur les colonnes dans l’interface utilisateur sur les modèles de 1400
- Modèle de non liés IntelliSense est désormais disponible en mode hors connexion
- L’Explorateur de modèles tabulaires contient maintenant un nœud pour représenter des expressions M nommées disponibles sur le modèle (1400 modèles tabulaires au niveau de compatibilité)
- Azure sélecteur d’utilisateurs Active Directory similaire à un IAM du portail Microsoft Azure désormais disponible lors du paramétrage des membres du rôle dans les modèles tabulaires

**Projets de base de données :**
- Mise à jour vers DacFx 17.1

**Correctifs de bogues**

- Correction d’un problème où le nom du groupe concepteurs Business Intelligence a été affiché correctement dans les Options de Visual Studio dans VS2017
- Correction d’un problème où une panne peut se produire à la génération d’une carte de Code pour une solution avec un projet de rapport ou en tant que projet
- Un nombre fixe de problèmes avec l’intégration de PowerQuery pour les modèles tabulaires Analysis Services 1400 au niveau de compatibilité
- Correction d’un problème dans le nouvel éditeur DAX fenêtre outil où l’opérateur d’assignation ne pourrait pas être sur une ligne distincte lors de la définition d’une mesure
- Correction d’un problème qui a empêché l’affichage de mesures sous forme de tableau à partir de la mise à jour lorsque vous renommez des mesures de perspective
- Mise à jour de moteur d’espace de travail intégré Analysis Services et de modèle objet tabulaire qui résout une régression à l’origine des projets tabulaires 1200 contenant des traductions sur déployer au serveur SQL Server 2016 Analysis Services
- Correction d’un problème de performances apportées creation\deletion de nouvelles sources de données tabulaires 1400 très lentes
- Correction d’un problème où le diagramme de vue de gestion dynamique dans les modèles multidimensionnels peut arrêter le rendu si vous modifiez la vue rapidement entre différents DSV

**DacFx 17.1**

- Correction d’un problème lors du chiffrement d’une colonne avec les tables à mémoire optimisée avec d’autres colonnes d’identité
- Prise en charge SQLDOM pour l’option CATALOG_COLLATION pour créer la base de données





&nbsp;

<a name="compactupdatedlist"/>

## Liste compacte d’Articles récemment mis à jour
<a id="compact-list-of-articles-updated-recently" class="xliff"></a>

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriées dans la section précédente.

1. [Journal des modifications de SQL Server Data Tools (SSDT)](#TitleNum_1)




<a name="sisters2"/>

&nbsp;

## Articles de frères
<a id="sister-articles" class="xliff"></a>

Cette section liste les articles très similaires récemment mis à jour dans d’autres zones de sujet, dans le même dépôt GitHub.com : [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/).

<!--  20170630-1150  -->

#### Zones de sujet avec des articles nouveaux ou mis à jour récemment
<a id="subject-areas-which-do-have-new-or-recently-updated-articles" class="xliff"></a>

- [Nouveaux + Mis à jour (12 + 2) : **Analytiques avancées pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (1 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (0 + 2) : **Connexion à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (3 + 0) : **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (1 + 2) : **Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (2 + 8) : **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (1 + 0) : **Master Data Services pour SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (5 + 5) : **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (2 + 0) : **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (0 + 4) : **Microsoft SQL Server** (documentation) ](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (1 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)


#### Zones de sujet sans article nouveau ou mis à jour récemment
<a id="subject-areas-which-have-no-new-or-recently-updated-articles" class="xliff"></a>

- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (0 + 0) : **SQL Server Migration Assistant (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 0) : **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)


&nbsp;


