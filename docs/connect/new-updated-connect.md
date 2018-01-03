---
title: "Mise à jour - se connecter à la documentation de SQL Server | Documents Microsoft"
description: "Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié, pour se connecter à Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.topic: article
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.author: genemi
ms.workload: connect-to-sql
ms.openlocfilehash: d8fb5f5cfbd94cc9d2bd86c4dfe1cbc15bc68d34
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="new-and-recently-updated-connect-to-sql-server"></a>Nouveaux et mis à jour récemment : se connecter à SQL Server



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **28-09-2017** &nbsp; au &nbsp; **02-12-2017**
- *Zone de sujet :* &nbsp; **se connecter à SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [1 de l’écran de l’Assistant Source de données](odbc/windows/dsn-wizard-1.md)
2. [2 de l’écran de l’Assistant Source de données](odbc/windows/dsn-wizard-2.md)
3. [3 de l’écran de l’Assistant Source de données](odbc/windows/dsn-wizard-3.md)
4. [Écran Assistant Source de données 4](odbc/windows/dsn-wizard-4.md)
5. [Boîte de dialogue de connexion SQL Server (ODBC)](odbc/windows/sql-server-login-dialog.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [PDOStatement::bindParam](#TitleNum_1)
2. [PDOStatement::bindValue](#TitleNum_2)
3. [sqlsrv_prepare](#TitleNum_3)
4. [sqlsrv_query](#TitleNum_4)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-pdostatementbindparamphppdostatement-bindparammd"></a>1. &nbsp;[PDOStatement::bindParam](php/pdostatement-bindparam.md)

*Mise à jour : 2017-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([suivant](#TitleNum_2))

<!-- Source markdown line 119.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2792d149331f5326f6914721c86687d545685488 e363544e2c6f73277b7f2ca05b9269a4139d1fac  (PR=3663  ,  Filename=pdostatement-bindparam.md  ,  Dirpath=docs\connect\php\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



> [!NOTE]
> Il est recommandé d’utiliser des chaînes en tant qu’entrées lors de la liaison de valeurs à un [colonne decimal ou numeric](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql) pour vérifier la précision et l’exactitude que PHP est limitée à la précision pour [nombres à virgule flottante](http://php.net/manual/en/language.types.float.php).

**Exemple**

Cet exemple de code montre comment lier une valeur décimale en tant que paramètre d’entrée.

```php
<?php
$database = "Test";
$server = "(local)";
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");

// Assume TestTable exists with a decimal field
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindParam(1, $input, PDO::PARAM_STR);
$stmt->execute();
```




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-pdostatementbindvaluephppdostatement-bindvaluemd"></a>2. &nbsp;[PDOStatement::bindValue](php/pdostatement-bindvalue.md)

*Mise à jour : 2017-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_1) | [suivant](#TitleNum_3))

<!-- Source markdown line 77.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c1d5ff4d5bfdbfbf1635cf14d71b4d583164075a 6cd5fc88860ae9ffca25ee15e8eeaeba29991fda  (PR=3663  ,  Filename=pdostatement-bindvalue.md  ,  Dirpath=docs\connect\php\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



> [!NOTE]
> Il est recommandé d’utiliser des chaînes en tant qu’entrées lors de la liaison de valeurs à un [colonne decimal ou numeric](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql) pour vérifier la précision et l’exactitude que PHP est limitée à la précision pour [nombres à virgule flottante](http://php.net/manual/en/language.types.float.php).

**Exemple**

Cet exemple de code montre comment lier une valeur décimale en tant que paramètre d’entrée.

```php
<?php
$database = "Test";
$server = "(local)";
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");

// Assume TestTable exists with a decimal field
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindValue(1, $input, PDO::PARAM_STR);
$stmt->execute();
```



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-sqlsrvpreparephpsqlsrv-preparemd"></a>3. &nbsp; [sqlsrv_prepare](php/sqlsrv-prepare.md)

*Mise à jour : 2017-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_2) | [suivant](#TitleNum_4))

<!-- Source markdown line 219.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7811e459efec90ef79340375d5fb34364130466b 3d28b3d320dc7fe5df12300da5cb9579abf6839a  (PR=3663  ,  Filename=sqlsrv-prepare.md  ,  Dirpath=docs\connect\php\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



> [!NOTE]
> Il est recommandé d’utiliser des chaînes en tant qu’entrées lors de la liaison de valeurs à un [colonne decimal ou numeric](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql) pour vérifier la précision et l’exactitude que PHP est limitée à la précision pour [nombres à virgule flottante](http://php.net/manual/en/language.types.float.php).

**Exemple**

Cet exemple de code montre comment lier une valeur décimale en tant que paramètre d’entrée.

```php
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"YourTestDB");
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
    echo "Could not connect.\n";
    die(print_r(sqlsrv_errors(), true));
}

// Assume TestTable exists with a decimal field
$input = "9223372036854.80000";
$params = array($input);
$stmt = sqlsrv_prepare($conn, "INSERT INTO TestTable (DecimalCol) VALUES (?)", $params);
sqlsrv_execute($stmt);

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);

?>
```



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-sqlsrvqueryphpsqlsrv-querymd"></a>4. &nbsp; [sqlsrv_query](php/sqlsrv-query.md)

*Mise à jour : 2017-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_3))

<!-- Source markdown line 163.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 07a84878c07af0b6ad7e247337be5b4567ce03c3 127af26a8a054a45dda51d90f43f08652949ba18  (PR=3663  ,  Filename=sqlsrv-query.md  ,  Dirpath=docs\connect\php\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



> [!NOTE]
> Il est recommandé d’utiliser des chaînes en tant qu’entrées lors de la liaison de valeurs à un [colonne decimal ou numeric](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql) pour vérifier la précision et l’exactitude que PHP est limitée à la précision pour [nombres à virgule flottante](http://php.net/manual/en/language.types.float.php).

**Exemple**

Cet exemple de code montre comment lier une valeur décimale en tant que paramètre d’entrée.

```php
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"YourTestDB");
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
     echo "Could not connect.\n";
     die(print_r(sqlsrv_errors(), true));
}

// Assume TestTable exists with a decimal field
$input = "9223372036854.80000";
$params = array($input);
$stmt = sqlsrv_query($conn, "INSERT INTO TestTable (DecimalCol) VALUES (?)", $params);

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);

?>
```








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
- [Nouveaux + Mis à jour (21 + 0) : **SQL Operations Studio** (documentation)](../sql-operations-studio/new-updated-sql-operations-studio.md)
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


