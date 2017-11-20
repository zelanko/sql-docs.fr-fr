---
title: "Mise à jour - Documentation du moteur de base de données | Microsoft Docs"
description: "Affichez des extraits de contenu mis à jour récemment dans la documentation du moteur de base de données."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: barbkess
ms.service: 
ms.component: database-engine
ms.suite: sql
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: 
ms.workload: database-engine
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/27/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: dc4a5516662b200b4224facbb4c9cf4588c1b42e
ms.contentlocale: fr-fr
ms.lasthandoff: 10/02/2017

---
# <a name="new-and-recently-updated-database-engine-docs"></a>Nouveau et récemment mis à jour : documentation du moteur de base de données
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]


Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **11-09-2017** &nbsp; au &nbsp; **27-09-2017**
- *Domaine :* &nbsp; **Moteur de base de données**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Ajouter des fonctionnalités à une instance de SQL Server (programme d’installation)](install-windows/add-features-to-an-instance-of-sql-server-setup.md)
2. [Installer SQL Server à partir de l’invite de commandes](install-windows/install-sql-server-from-the-command-prompt.md)
3. [Installer SQL Server à l’aide d’un fichier de configuration](install-windows/install-sql-server-using-a-configuration-file.md)
4. [Continuité d’activité et récupération de base de données - SQL Server](sql-server-business-continuity-dr.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Installation de mises à jour à partir de l’invite de commandes](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-installing-updates-from-the-command-promptinstall-windowsinstalling-updates-from-the-command-promptmd"></a>1. &nbsp; [Installation de mises à jour à partir de l’invite de commandes](install-windows/installing-updates-from-the-command-prompt.md)

*Mise à jour : 12-09-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 48.  ms.author= "mikeray".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 04abb23d0682c23654a55e7926d2140f0b6ae408 a4bb1e27ae99460a66da72848ace1417b148f85c  (PR=3122  ,  Filename=installing-updates-from-the-command-prompt.md  ,  Dirpath=docs\database-engine\install-windows\  ,  MergeCommitSha40=1df54edd5857ac2816fa4b164d268835d9713638) -->



- Mettez à jour toutes les instances de ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] sur l’ordinateur et tous les composants partagés, comme ..!NCLUDE-NotShown--ssISnoversion--../../includes/ssisnoversion-md.md)] et les outils de gestion :

```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances.
```

- Supprimez une mise à jour d’une seule instance de ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)], et tous les composants partagés, comme ..!NCLUDE-NotShown--ssISnoversion--../../includes/ssisnoversion-md.md)] et les outils de gestion :

```
    <package_name>.exe /qs /Action=RemovePatch /InstanceName=MyInstance.
```

- Supprimez une mise à jour des composants partagés de ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] uniquement, comme ..!NCLUDE-NotShown--ssISnoversion--../../includes/ssisnoversion-md.md)] et les outils de gestion :

```
    <package_name>.exe /qs /Action=RemovePatch
```







## <a name="similar-articles"></a>Articles similaires

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Zones de sujet avec des articles nouveaux ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 1) : **Analytique avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (0 + 1) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (4 + 1) : **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (17 + 0) : **Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (3 + 0) : **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (1 + 1) : **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (2 + 0) : **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (0 + 1) : **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Zones de sujet sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Connexion à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (0 + 0) : **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (0 + 0) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (0 + 0) : **SQL Server Migration Assistant (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)



