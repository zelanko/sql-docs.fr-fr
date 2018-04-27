---
title: Mise à jour - Documentation de SSMS pour SQL Server | Microsoft Docs
description: Affichez des extraits de contenu mis à jour récemment dans la documentation, pour SQL Server Management Studio (SSMS) pour Microsoft SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql
ms.component: ssms
ms.date: 02/03/2018
ms.openlocfilehash: 8f2ad52b9741a3220a8c5db0a60924a41cc62d27
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="new-and-recently-updated-sql-server-management-studio-ssms-for-sql-server"></a>Nouveautés et mises à jour récentes : SQL Server Management Studio (SSMS) pour SQL Server



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **03-12-2017** &nbsp; au &nbsp; **03-02-2018**
- *Domaine :* &nbsp; **SQL Server Management Studio (SSMS)**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Installer des versions de SQL Server Management Studio (SSMS) dans d’autres langues que l’anglais](install-other-languages.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Télécharger SQL Server Management Studio (SSMS)](#TitleNum_1)
2. [SQL Server Management Studio : journal des modifications (SSMS)](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-download-sql-server-management-studio-ssmsdownload-sql-server-management-studio-ssmsmd"></a>1. &nbsp; [Télécharger SQL Server Management Studio (SSMS)](download-sql-server-management-studio-ssms.md)

*Mise à jour : 18-01-2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Suivant](#TitleNum_2))

<!-- Source markdown line 83.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0e123e7bdf04f02fcd26ac31fa30ed5f31b19c7d 924246b55d3cad6a5d068da8a41f4be23dcfeb2b  (PR=4652  ,  Filename=download-sql-server-management-studio-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=6b4aae3706247ce9b311682774b13ac067f60a79) -->



SSMS 17.4 est la dernière version de SQL Server Management Studio. La génération 17.x de SSMS prend en charge presque tous les composants de SQL Server 2008 à SQL Server 2017. La version 17.x prend également en charge la PaaS SQL Analysis Services.

Contenu de la version 17.4 :

Évaluation des vulnérabilités :
- Ajout d’un nouveau service d’évaluation des vulnérabilités SQL pour analyser la présence éventuelle de vulnérabilités et d’écarts par rapport aux meilleures pratiques dans les bases de données, par exemple, des erreurs de configuration, des autorisations excessives et des données sensibles exposées.
- Les résultats de l’évaluation sont accompagnés d’étapes actionnables permettant de résoudre chaque problème et, le cas échéant, de scripts de correction personnalisés. Le rapport d’évaluation est adaptable à chaque environnement et aux exigences spécifiques. Pour en savoir plus, consultez la page [Évaluation des vulnérabilités SQL](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment).

SMO :
- Correction du problème à cause duquel *HasMemoryOptimizedObjects* levait une exception sur Azure.
- Ajout de la prise en charge de la nouvelle fonctionnalité CATALOG_COLLATION.

Tableau de bord Always On :
- Amélioration de l’analyse de la latence dans les groupes de disponibilité.
- Ajout de deux nouveaux rapports : *AlwaysOn\_Latency\_Primary* et *AlwaysOn\_Latency\_Secondary*.

Plan d’exécution de requêtes :
- Mise à jour des liens, de sorte qu’ils pointent vers la documentation appropriée.
- Permet une analyse de plan unique directement à partir du plan réellement généré.
- Nouvel ensemble d’icônes.
- Ajout de la prise en charge permettant de reconnaître « Appliquer des opérateurs logiques », comme GbApply ou InnerApply.

XE Profiler :
- Renommé XEvent Profiler.
- À présent, les commandes de menu Arrêter/Démarrer arrêtent/démarrent la session par défaut.
- Activation des raccourcis clavier (par exemple, CTRL+F pour faire une recherche).
- Ajout des actions database\_name et client\_hostname aux événements concernés dans les sessions XEvent Profiler. Pour que la modification prenne effet, vous devrez peut-être supprimer les instances de sessions QuickSessionStandard et QuickSessionTSQL sur les serveurs - [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981).



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sql-server-management-studio---changelog-ssmssql-server-management-studio-changelog-ssmsmd"></a>2. &nbsp; [SQL Server Management Studio - Journal des modifications (SSMS)](sql-server-management-studio-changelog-ssms.md)

*Mise à jour : 29-01-2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_1))

<!-- Source markdown line 27.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b5096fa8f1ae3f2e4bc040f43cb8810d96f2c69c eb641ac39386a26a76dc303f5bd55eb3f9f4c78d  (PR=0  ,  Filename=sql-server-management-studio-changelog-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=ba4b1c2e5200f2f78786b710da18fd38fedde6c9) -->



**[SSMS 17.4](download-sql-server-management-studio-ssms.md)**

Disponibilité générale | Numéro de build : 14.0.17213.0

**Nouveautés**


**SSMS général**

Évaluation des vulnérabilités :
- Ajout d’un nouveau service d’évaluation des vulnérabilités SQL pour analyser la présence éventuelle de vulnérabilités et d’écarts par rapport aux meilleures pratiques dans les bases de données, par exemple, des erreurs de configuration, des autorisations excessives et des données sensibles exposées.
- Les résultats de l’évaluation sont accompagnés d’étapes actionnables permettant de résoudre chaque problème et, le cas échéant, de scripts de correction personnalisés. Le rapport d’évaluation est adaptable à chaque environnement et aux exigences spécifiques. Pour en savoir plus, consultez la page [Évaluation des vulnérabilités SQL](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment).

SMO :
- Correction du problème à cause duquel *HasMemoryOptimizedObjects* levait une exception sur Azure.
- Ajout de la prise en charge de la nouvelle fonctionnalité CATALOG_COLLATION.

Tableau de bord Always On :
- Amélioration de l’analyse de la latence dans les groupes de disponibilité.
- Ajout de deux nouveaux rapports : *AlwaysOn\_Latency\_Primary* et *AlwaysOn\_Latency\_Secondary*.

Plan d’exécution de requêtes :
- Mise à jour des liens, de sorte qu’ils pointent vers la documentation appropriée.
- Permet une analyse de plan unique directement à partir du plan réellement généré.
- Nouvel ensemble d’icônes.
- Ajout de la prise en charge permettant de reconnaître « Appliquer des opérateurs logiques », comme GbApply ou InnerApply.

XE Profiler :
- Renommé XEvent Profiler.
- À présent, les commandes de menu Arrêter/Démarrer arrêtent/démarrent la session par défaut.
- Activation des raccourcis clavier (par exemple, CTRL+F pour faire une recherche).
- Ajout des actions database\_name et client\_hostname aux événements concernés dans les sessions XEvent Profiler. Pour que la modification prenne effet, vous devrez peut-être supprimer les instances de sessions QuickSessionStandard et QuickSessionTSQL sur les serveurs - [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981).

Ligne de commande :
- Ajout d’une nouvelle option de ligne de commande («-G ») qui permet de faire en sorte que SSMS se connecte automatiquement à un serveur/une base de données avec l’authentification Active Directory (« Intégré » ou « Mot de passe »). Pour plus d’informations, consultez la page [Utilitaire SSMS](ssms-utility.md).







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


