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
ms.date: 12/02/2017
ms.author: genemi
ms.workload: t-sql
ms.openlocfilehash: 33c50454f34c1902ea7f7dedc9ecb0a54f99ce24
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2017
---
# <a name="new-and-recently-updated-transact-sql-docs"></a>Nouveau et récemment mis à jour : les documents de Transact-SQL



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Plage de dates de mises à jour :* &nbsp; **2017-09-28** &nbsp; - à - &nbsp; **2017-12-02**
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

1. [Barre oblique inverse (Continuation de ligne) (Transact-SQL)](#TitleNum_1)
2. [Sélectionnez - ORDER BY Clause (Transact-SQL)](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-backslash-line-continuation-transact-sqllanguage-elementssql-server-utilities-statements-backslashmd"></a>1. &nbsp;[Barre oblique inverse (Continuation de ligne) (Transact-SQL)](language-elements/sql-server-utilities-statements-backslash.md)

*Mise à jour : 2017-11-15* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([suivant](#TitleNum_2))

<!-- Source markdown line 83.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9484441710ac9a083a554ffadb59a3b7e92484b3 19b9c37c65ba462a32067c80e81a920eeb339851  (PR=3966  ,  Filename=sql-server-utilities-statements-backslash.md  ,  Dirpath=docs\t-sql\language-elements\  ,  MergeCommitSha40=b0c223ba0f78af5eb76948e68e2d1aab2e7b80c1) -->



**B. Fractionnement d’une chaîne binaire**


L’exemple suivant utilise une barre oblique inverse et un retour chariot pour fractionner une chaîne binaire en deux lignes.

```
SELECT 0xabc\
def AS [ColumnResult];

```

 ..! NCLURE-NotShown--ssResult--... /.. /Includes/ssresult-MD.MD)]

```
 ColumnResult
 ------------
 0xABCDEF
```




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-select---order-by-clause-transact-sqlqueriesselect-order-by-clause-transact-sqlmd"></a>2. &nbsp;[Sélectionnez - ORDER BY Clause (Transact-SQL)](queries/select-order-by-clause-transact-sql.md)

*Mise à jour : 2017-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_1))

<!-- Source markdown line 481.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b8d7bc7bab46e914eb2facf6c654a5944383077e de7e4f3f7826011e273120a2b6b08af4d263a510  (PR=3663  ,  Filename=select-order-by-clause-transact-sql.md  ,  Dirpath=docs\t-sql\queries\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



**<a name="Union"></a>À l’aide de ORDER BY avec UNION, EXCEPT et INTERSECT**

 Lorsqu'une requête utilise les opérateurs UNION, EXCEPT ou INTERSECT, la clause ORDER BY doit être spécifiée à la fin de l'instruction et les résultats des requêtes combinées sont triés. L'exemple suivant retourne tous les produits qui sont rouges ou jaunes et effectue le tri de cette liste combinée selon la colonne `ListPrice`.

```sql
USE AdventureWorks2012;
GO
SELECT Name, Color, ListPrice
FROM Production.Product
WHERE Color = 'Red'
-- ORDER BY cannot be specified here.
UNION ALL
SELECT Name, Color, ListPrice
FROM Production.Product
WHERE Color = 'Yellow'
ORDER BY ListPrice ASC;

```

**Exemples :.. ! NCLURE-NotShown--ssSDWfull--... /.. /Includes/sssdwfull-MD.MD)] et.. ! NCLURE-NotShown--ssPDW--... /.. /Includes/sspdw-MD.MD)]**








## <a name="similar-articles"></a>Articles similaires

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Zones de sujet avec des articles nouveaux ou mis à jour récemment

- [Nouveau + mis à jour (3 + 14) : **avancées d’Analytique pour SQL** documents](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (1 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveau + mis à jour (87 + 0) : **système de plateforme d’Analytique pour SQL** documents](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nouveau + mis à jour (5 + 4) : **se connecter à SQL** documents](../connect/new-updated-connect.md)
- [Nouveau + mis à jour (0 + 1) : **moteur de base de données pour SQL** documents](../database-engine/new-updated-database-engine.md)
- [Nouveau + mis à jour (2 + 2) : **Integration Services pour SQL** documents](../integration-services/new-updated-integration-services.md)
- [Nouveau + mis à jour (10 + 9) : **Linux pour SQL** documents](../linux/new-updated-linux.md)
- [Nouveau + mis à jour (2 + 4) : **des bases de données relationnelles pour SQL** documents](../relational-databases/new-updated-relational-databases.md)
- [Nouveau + mis à jour (4 + 2) : **Reporting Services pour SQL** documents](../reporting-services/new-updated-reporting-services.md)
- [Nouveau + mis à jour (0 + 1) : **exemples pour SQL** documents](../sample/new-updated-sample.md)
- [Nouveau + mis à jour (0 + 21) : **SQL opérations Studio** documents](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nouveau + mis à jour (5 + 1) : **Microsoft SQL Server** documents](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveau + mis à jour (1 + 0) : **SQL Server Migration Assistant (SSMA)** documents](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveau + mis à jour (0 + 2) : **Transact-SQL** documents](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Zones de sujet sans article nouveau ou mis à jour récemment

- [Nouveau + mis à jour (0 0 +) : **données Migration Assistant (DMA) pour SQL** documents](../dma/new-updated-dma.md)
- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)


