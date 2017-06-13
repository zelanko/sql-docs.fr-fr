---
title: "Mise à jour - docs de bases de données relationnelles | Documents Microsoft"
description: "Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié, pour les bases de données relationnelles."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: relational-databases
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 05/23/2017
ms.author: genemi
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: 3ab051a6fd00670139bb1089dcd3f4af76b9ecef
ms.contentlocale: fr-fr
ms.lasthandoff: 05/25/2017

---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Nouveau et récemment mis à jour : les documents de bases de données relationnelles



Presque tous les jours Microsoft met à jour certains de ses articles existants sur son [Docs.Microsoft.com](http://docs.microsoft.com/) site Web de documentation. Cet article affiche des extraits d’articles récemment mis à jour. Des liens vers nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme est exécuté à nouveau régulièrement. Parfois un extrait peut apparaître avec mise en forme imparfait, ou en tant que markdown de l’article de la source. Les images ne sont jamais affichés ici.

Mises à jour récentes sont signalés pour la plage de dates suivante et l’objet :



- *Plage de dates de mises à jour :* &nbsp; **2017-05-01** &nbsp; - à - &nbsp; **2017-05-23**
- *Zone de sujet :* &nbsp; **bases de données relationnelles**.




&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits de mises à jour collectées à partir des articles qui ont récemment subi une mise à jour importante.

Les extraits affichés ici apparaissent séparés à partir de leur contexte sémantique spécifique. En outre, parfois un extrait est séparé à partir de la syntaxe markdown important qui l’entoure dans l’article. Par conséquent, ces extraits sont pour des conseils généraux. Les extraits permettent uniquement de savoir si votre intérêt justifie pris le temps de cliquer sur et consultez l’article.

Pour celles-ci et d’autres raisons, ne pas copier le code à partir de ces extraits et ne prennent pas en tant que vérité exacte tout extrait de texte. Au lieu de cela, consultez l’article.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-create-a-graph-database-and-run-some-pattern-matching-queries-using-t-sqlgraphssql-graph-samplemd"></a>1. &nbsp;[Créer une base de données du graphique et exécuter des requêtes à l’aide de T-SQL mise en correspondance](graphs/sql-graph-sample.md)

*Updated: 2017-05-04* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Next](#TitleNum_2))

<!-- Source markdown line 68.  ms.author= "shkale".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ff467bf5fcf13592c796836def36e16e34f8cc31 99fcf0399006de16d0ac7cc9057564d307cb981b -->


```
INSERT INTO Person VALUES (1,'John');
INSERT INTO Person VALUES (2,'Mary');
INSERT INTO Person VALUES (3,'Alice');
INSERT INTO Person VALUES (4,'Jacob');
INSERT INTO Person VALUES (5,'Julie');

INSERT INTO Restaurant VALUES (1,'Taco Dell','Bellevue');
INSERT INTO Restaurant VALUES (2,'Ginger and Spice','Seattle');
INSERT INTO Restaurant VALUES (3,'Noodle Land', 'Redmond');

INSERT INTO City VALUES (1,'Bellevue','wa');
INSERT INTO City VALUES (2,'Seattle','wa');
INSERT INTO City VALUES (3,'Redmond','wa');

-- Insert into edge table. While inserting into an edge table, 
-- you need to provide the $node_id from $from_id and $to_id columns.
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 1), 
       (SELECT $node_id FROM Restaurant WHERE id = 1),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 2), 
      (SELECT $node_id FROM Restaurant WHERE id = 2),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 3), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 4), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 5), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);

INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 1),
      (SELECT $node_id FROM City WHERE id = 1));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 2),
      (SELECT $node_id FROM City WHERE id = 2));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 3),
      (SELECT $node_id FROM City WHERE id = 3));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 4),
      (SELECT $node_id FROM City WHERE id = 3));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 5),
      (SELECT $node_id FROM City WHERE id = 1));

INSERT INTO locatedIn VALUES ((SELECT $node_id FROM Restaurant WHERE id = 1),
      (SELECT $node_id FROM City WHERE id =1));
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sysfngetauditfile-transact-sqlsystem-functionssys-fn-get-audit-file-transact-sqlmd"></a>2. &nbsp; [sys.fn_get_audit_file (Transact-SQL)](system-functions/sys-fn-get-audit-file-transact-sql.md)

*Updated: 2017-05-16* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_1) | [Next](#TitleNum_3))

<!-- Source markdown line 145.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 046fa92ad1b7e6bb7a956493ca06cf72d45b5285 fbf55361da90663835d7e107fda697c358e0e061 -->



- **Azure SQL Database**

  Cet exemple lit à partir d'un fichier nommé `ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel`.  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel',default,default);
  GO  
  ```  

  Cet exemple lit tous les rapports d’audit à partir des serveurs qui commencent par `Sh`.  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/Sh',default,default);
  GO  
  ```





&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-manage-retention-of-historical-data-in-system-versioned-temporal-tablestablesmanage-retention-of-historical-data-in-system-versioned-temporal-tablesmd"></a>3. &nbsp;[Gérer la rétention des données d’historique dans les Tables temporelles à système par version](tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)

*Updated: 2017-05-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_2))

<!-- Source markdown line 425.  ms.author= "carlrab".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ee69beb6a46913934d4a322f5d95343cc86f2ec4 94da98fec4ab16636a4581c16eb4456e2d1ff66b -->



**À l’aide d’approche de stratégie de rétention historique temporelle**

> **Remarque :** à l’aide de la stratégie de rétention d’historique temporelle approche est valable pour [ ! INCLUDE [sqldbesa--... /.. /Includes/sqldbesa-MD.MD)] et 2017 du serveur SQL à partir de CTP 1.3.  

Rétention de l’historique temporelle peut être configurée au niveau de la table individuelles, ce qui permet aux utilisateurs de créer de vieillissement flexible des stratégies. Application de la rétention temporelle est simple : il ne requiert qu’un seul paramètre à définir pendant la modification de la création ou le schéma de table.

Après avoir défini la stratégie de rétention, base de données SQL Azure commence à vérifier régulièrement s’il existe des lignes historiques qui sont éligibles pour le nettoyage automatique des données. Identification des lignes correspondantes et leur suppression à partir de la table d’historique se produisent en toute transparence, dans la tâche en arrière-plan est planifiée et exécutée par le système. Condition d’âge pour les lignes de la table historique est vérifiée en fonction de la colonne représentant la fin de la période SYSTEM_TIME. Si la période de rétention, par exemple, est définie à six mois, les lignes éligibles pour le nettoyage de la table répondent à la condition suivante :
```
ValidTo < DATEADD (MONTH, -6, SYSUTCDATETIME())
```
Dans l’exemple précédent, nous avons supposé que ValidTo colonne correspond à la fin de la période SYSTEM_TIME.
**Comment configurer la stratégie de rétention ?**

Avant de configurer la stratégie de rétention pour une table temporelle, vérifiez d’abord si la rétention historique temporelle est activée au niveau de la base de données :
```
SELECT is_temporal_history_retention_enabled, name
FROM sys.databases
```
Indicateur de base de données **is_temporal_history_retention_enabled** a la valeur ON par défaut, mais les utilisateurs peuvent les modifier avec l’instruction ALTER DATABASE. Il est automatiquement défini sur OFF après le point dans l’opération de restauration de temps. Pour activer le nettoyage de rétention d’historique temporelle pour votre base de données, exécutez l’instruction suivante :
```
ALTER DATABASE <myDB>
SET TEMPORAL_HISTORY_RETENTION  ON
```
Stratégie de rétention est configurée lors de la création de table en spécifiant la valeur du paramètre HISTORY_RETENTION_PERIOD :
```
CREATE TABLE dbo.WebsiteUserInfo
```





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’Articles récemment mis à jour

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriées dans la section précédente.

1. [Créer une base de données du graphique et exécuter des requêtes à l’aide de T-SQL mise en correspondance](#TitleNum_1)
2. [Sys.fn_get_audit_file (Transact-SQL)](#TitleNum_2)
3. [Gérer la rétention des données d’historique dans les tables temporelles avec contrôle de version par le système](#TitleNum_3)


<a name="sisters2"/>

&nbsp;

## <a name="sister-articles"></a>Articles de frères

Cette section répertorie les articles très similaires pour les articles récemment mis à jour dans d’autres zones de sujet, dans le même référentiel GitHub.


&nbsp;

[Microsoft /**sql-docs-pr** ](https://github.com/microsoftdocs/sql-docs-pr/) référentiel sur GitHub.com :

- [Récemment mis à jour : **Microsoft SQL Server et les bases de données relationnelles** documents](/sql/relational-databases/relational-databases-new-updated-sql-docs-pr)
- [Récemment mis à jour : **Microsoft SQL Server** documents](/sql/sql-server/sql-server-new-updated-sql-docs-pr)
- [Récemment mis à jour : **Transact-SQL dans SQL Server** documents](/sql/t-sql/t-sql-new-updated-sql-docs-pr)


&nbsp;

<!--
[Microsoft/**azure-docs**](https://github.com/microsoft/azure-docs/) repository on GitHub.com:

- [Sisters list for **azure-docs** repo](https://docs.microsoft.com/azure/sql-server-new-updated-azure-docs/#sisters2)
-->

&nbsp;



