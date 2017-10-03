---
title: "Mise à jour - T-SQL docs | Documents Microsoft"
description: "Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié, de Transact-SQL."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/27/2017
ms.author: genemi
ms.workload: t-sql
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 4d48c7df783ebe50f7b5d7fe3e72bef91559006e
ms.contentlocale: fr-fr
ms.lasthandoff: 10/02/2017

---
# <a name="new-and-recently-updated-transact-sql-docs"></a>Nouveau et récemment mis à jour : les documents de Transact-SQL



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Plage de dates de mises à jour :* &nbsp; **2017-09-11** &nbsp; - à - &nbsp; **2017-09-27**
- *Zone de sujet :* &nbsp; **T-SQL**.




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

1. [sql_variant (Transact-SQL)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sqlvariant-transact-sqldata-typessql-variant-transact-sqlmd"></a>1. &nbsp; [sql_variant (Transact-SQL)](data-types/sql-variant-transact-sql.md)

*Mise à jour : 2017-09-13* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

<!-- Source markdown line 111.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 659578de7de33d8672ceb9542093862107d13526 c80026de2b0deedab3722a874e9124c2cfefa049  (PR=0  ,  Filename=sql-variant-transact-sql.md  ,  Dirpath=docs\t-sql\data-types\  ,  MergeCommitSha40=5cd78481b3fac55ec34b59e7b1ad25e0e14d2a00) -->



**Exemples**


**A. À l’aide d’un sql_variant dans une table**

 L’exemple suivant, crée une table avec un type de données sql_variant. L’exemple récupère `SQL_VARIANT_PROPERTY` plus d’informations sur la `colA` valeur `46279.1` où `colB`  = `1689`, étant donné que `tableA` a `colA` qui est de type `sql_variant` et `colB`.

```
CREATE   TABLE tableA(colA sql_variant, colB int)
INSERT INTO tableA values ( cast (46279.1 as decimal(8,2)), 1689)
SELECT   SQL_VARIANT_PROPERTY(colA,'BaseType') AS 'Base Type',
         SQL_VARIANT_PROPERTY(colA,'Precision') AS 'Precision',
         SQL_VARIANT_PROPERTY(colA,'Scale') AS 'Scale'
FROM      tableA
WHERE      colB = 1689
```

 ..! NCLURE-NotShown--ssResult--... /.. /Includes/ssresult-MD.MD)] Notez que chacune de ces trois valeurs est un **sql_variant**.

```
Base Type    Precision    Scale
---------    ---------    -----
decimal      8           2

(1 row(s) affected)
```

**B. À l’aide d’un sql_variant en tant que variable**

 L’exemple suivant, crée une variable avec le type de données sql_variant et récupère ensuite `SQL_VARIANT_PROPERTY` plus d’informations sur une variable nommée @v1.

```
DECLARE @v1 sql_variant;
SET @v1 = 'ABC';
SELECT @v1;
SELECT SQL_VARIANT_PROPERTY(@v1, 'BaseType');
SELECT SQL_VARIANT_PROPERTY(@v1, 'MaxLength');
```








## <a name="similar-articles"></a>Articles similaires

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Zones de sujet avec des articles nouveaux ou mis à jour récemment

- [Nouveau + mis à jour (0 + 1) : **avancées d’Analytique pour SQL** documents](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveau + mis à jour (0 + 1) : **Analysis Services pour SQL** documents](../analysis-services/new-updated-analysis-services.md)
- [Nouveau + mis à jour (4 + 1) : **moteur de base de données pour SQL** documents](../database-engine/new-updated-database-engine.md)
- [Nouveau + mis à jour (17 + 0) : **Integration Services pour SQL** documents](../integration-services/new-updated-integration-services.md)
- [Nouveau + mis à jour (3 + 0) : **Linux pour SQL** documents](../linux/new-updated-linux.md)
- [Nouveau + mis à jour (1 + 1) : **des bases de données relationnelles pour SQL** documents](../relational-databases/new-updated-relational-databases.md)
- [Nouveau + mis à jour (2 + 0) : **Reporting Services pour SQL** documents](../reporting-services/new-updated-reporting-services.md)
- [Nouveau + mis à jour (0 + 1) : **SQL Server Management Studio (SSMS)** documents](../ssms/new-updated-ssms.md)
- [Nouveau + mis à jour (0 + 1) : **Transact-SQL** documents](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Zones de sujet sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveau + mis à jour (0 0 +) : **se connecter à SQL** documents](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveau + mis à jour (0 0 +) : **Microsoft SQL Server** documents](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (0 + 0) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (0 + 0) : **SQL Server Migration Assistant (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveau + mis à jour (0 0 +) : **Tools pour SQL** documents](../tools/new-updated-tools.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)



