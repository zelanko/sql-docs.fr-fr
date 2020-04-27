---
title: Constructions Transact-SQL non prises en charge par l’OLTP en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e3f8009c-319d-4d7b-8993-828e55ccde11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dda74f247f9899b9e0a23d43143a5031574d8c13
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63155304"
---
# <a name="transact-sql-constructs-not-supported-by-in-memory-oltp"></a>Constructions Transact-SQL non prises en charge par l’OLTP en mémoire
  Les tables mémoire optimisées et les procédures stockées compilées en mode natif ne prennent pas en charge la surface d'exposition [!INCLUDE[tsql](../../includes/tsql-md.md)] complète qui est prise en charge par les tables sur disque et les procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] interprétées. Lorsque vous tentez d'utiliser une des fonctionnalités non prises en charge, le serveur retourne une erreur.  
  
 Le texte du message d'erreur indique le type d'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] (fonctionnalité, opération, option, par exemple), ainsi que le nom de la fonctionnalité ou du mot clé [!INCLUDE[tsql](../../includes/tsql-md.md)] . La plupart des fonctionnalités qui ne sont pas prises en charge retournent l'erreur 10794, avec le texte du message d'erreur indiquant la fonctionnalité non prise en charge. Les tableaux suivants répertorient les fonctionnalités et les mots clés [!INCLUDE[tsql](../../includes/tsql-md.md)] qui peuvent s'afficher dans le texte du message d'erreur, ainsi que l'action corrective à entreprendre pour résoudre l'erreur.  
  
 Pour plus d'informations sur les fonctionnalités prises en charge avec les tables optimisées en mémoire et les procédures stockées compilées en mode natif, consultez :  
  
-   [Problèmes de migration pour les procédures stockées compilées en mode natif](migration-issues-for-natively-compiled-stored-procedures.md)  
  
-   [Prise en charge de Transact-SQL pour OLTP en mémoire](transact-sql-support-for-in-memory-oltp.md)  
  
-   [Fonctionnalités SQL Server prises en charge](unsupported-sql-server-features-for-in-memory-oltp.md)  
  
-   [Procédures stockées compilées en mode natif](../in-memory-oltp/natively-compiled-stored-procedures.md)  
  
## <a name="databases-that-use-in-memory-oltp"></a>Bases de données qui utilisent OLTP en mémoire  
 Le tableau suivant répertorie les fonctionnalités et les mots clés [!INCLUDE[tsql](../../includes/tsql-md.md)] qui peuvent apparaître dans le texte du message d'une erreur impliquant une base de données OLTP en mémoire.  
  
|Type|Nom|Solution|  
|----------|----------|----------------|  
|Option|AUTO_CLOSE|L'option de base de données AUTO_CLOSE=ON n'est pas prise en charge par les bases de données avec un groupe de fichiers MEMORY_OPTIMIZED_DATA.|  
|Option|ATTACH_REBUILD_LOG|L'option de base de données CREATE ATTACH_REBUILD_LOG n'est pas prise en charge par les bases de données avec un groupe de fichiers MEMORY_OPTIMIZED_DATA.|  
|Fonctionnalité|DATABASE SNAPSHOT|La création d'instantanés de base de données n'est pas prise en charge par les bases de données avec un groupe de fichiers MEMORY_OPTIMIZED_DATA.|  
|Fonctionnalité|Réplication à l'aide de sync_method 'database snapshot' ou 'database snapshot character'|La réplication à l'aide de sync_method 'database snapshot' ou 'database snapshot character' n'est pas prise en charge par les bases de données avec un groupe de fichiers MEMORY_OPTIMIZED_DATA.|  
|Fonctionnalité|DBCC CHECKDB<br /><br /> DBCC CHECKTABLE|DBCC CHECKDB ignore les tables optimisées en mémoire dans la base de données.<br /><br /> DBCC CHECKTABLE échoue pour les tables optimisées en mémoire.|  
  
## <a name="memory-optimized-tables"></a>Tables optimisées en mémoire  
 Le tableau suivant répertorie les fonctionnalités et les mots clés [!INCLUDE[tsql](../../includes/tsql-md.md)] qui peuvent s'afficher dans le texte d'un message d'erreur qui implique une table mémoire optimisée, ainsi que l'action corrective à entreprendre pour résoudre l'erreur.  
  
|Type|Nom|Solution|  
|----------|----------|----------------|  
|Fonctionnalité|ACTIVÉ|Les tables optimisées en mémoire ne peuvent pas être placées sur un groupe de fichiers ou un schéma de partition. Supprimez la clause ON de l'instruction `CREATE TABLE`.|  
|Type de données|*Nom du type de données*|Le type de données spécifié n'est pas pris en charge. Remplacez le type par un des types de données pris en charge. Pour plus d’informations, consultez [types de données pris en charge](supported-data-types-for-in-memory-oltp.md).|  
|Fonctionnalité|Colonnes calculées|Les colonnes calculées ne sont pas prises en charge pour les tables mémoire optimisées. Supprimez les colonnes calculées de l'instruction `CREATE TABLE`.|  
|Fonctionnalité|Réplication|La réplication n'est pas pris en charge avec les tables mémoire optimisées.|  
|Fonctionnalité|FILESTREAM|Le stockage FILESTREAM n'est pas pris en charge pour les colonnes de tables mémoire optimisées. Supprimez le mot clé `FILESTREAM` de la définition de colonne.|  
|Fonctionnalité|SPARSE|Les colonnes de tables mémoire optimisées ne peuvent pas être définies comme SPARSE. Supprimez le mot clé `SPARSE` de la définition de colonne.|  
|Fonctionnalité|ROWGUIDCOL|L'option ROWGUIDCOL n'est pas prise en charge pour les colonnes de tables mémoire optimisées. Supprimez le mot clé `ROWGUIDCOL` de la définition de colonne.|  
|Fonctionnalité|FOREIGN KEY|Les contraintes FOREIGN KEY ne sont pas prises en charge pour les tables mémoire optimisées. Supprime la contrainte de la définition de table.<br /><br /> Pour plus d’informations sur la façon de limiter l’absence de prise en charge des contraintes, consultez [migration de contraintes de vérification et de clé étrangère](../../database-engine/migrating-check-and-foreign-key-constraints.md).|  
|Fonctionnalité|CHECK|Les contraintes CHECK ne sont pas prises en charge pour les tables mémoire optimisées. Supprime la contrainte de la définition de table.<br /><br /> Pour plus d’informations sur la façon de limiter l’absence de prise en charge des contraintes, consultez [migration de contraintes de vérification et de clé étrangère](../../database-engine/migrating-check-and-foreign-key-constraints.md).|  
|Fonctionnalité|UNIQUE|Les contraintes UNIQUE ne sont pas prises en charge pour les tables mémoire optimisées. Supprime la contrainte de la définition de table.<br /><br /> Pour plus d’informations sur la façon de limiter l’absence de prise en charge des contraintes, consultez [migration de contraintes de vérification et de clé étrangère](../../database-engine/migrating-check-and-foreign-key-constraints.md).|  
|Fonctionnalité|COLUMNSTORE|Les index COLUMNSTORE ne sont pris en charge avec les tables mémoire optimisées. Spécifiez un index NONCLUSTERED ou NONCLUSTERED HASH à la place.|  
|Fonctionnalité|index cluster|Spécifiez un index non cluster. Dans le cas d'un index de clé principale, veillez à spécifier `PRIMARY KEY NONCLUSTERED [HASH]`.|  
|Fonctionnalité|page de codes autre que 1252|Les colonnes de tables mémoire optimisées avec les types de données `char` et `varchar` doivent utiliser la page de codes 1252. Utilisez n(var)char plutôt que (var)char, ou utilisez un classement avec la page de codes 1252 (par exemple, Latin1_General_BIN2). Pour plus d'informations, consultez [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).|  
|Fonctionnalité|Transactions dans DDL|Les tables mémoire optimisées et les procédures stockées compilées en mode natif ne peuvent pas être créées ou supprimées dans le contexte d'une transaction utilisateur. Ne commencez pas de transaction et veillez à ce que le paramètre de session IMPLICIT_TRANSACTIONS ait la valeur OFF avant d'exécuter l'instruction CREATE ou DROP.|  
|Fonctionnalité|déclencheurs DDL|Les tables mémoire optimisées et les procédures stockées compilées en mode natif ne peuvent pas être créées ou supprimées s'il existe un déclencheur de serveur ou de base de données pour cette opération DDL. Supprimez les déclencheurs de serveur et base de données dans l'instruction CREATE/DROP TABLE et CREATE/DROP PROCEDURE.|  
|Fonctionnalité|EVENT NOTIFICATION|Les tables mémoire optimisées et les procédures stockées compilées en mode natif ne peuvent pas être créées ou supprimées s'il existe une notification d'événement de serveur ou de base de données pour cette opération DDL. Supprimez les notifications d'événement de serveur et de base de données sur CREATE TABLE ou DROP TABLE et CREATE PROCEDURE ou DROP PROCEDURE.|  
|Fonctionnalité|FileTable|Les tables mémoire optimisées ne peuvent pas être créées en tant que tables de fichiers. Supprimez l'argument `AS FileTable` de l'instruction `CREATE TABLE`.|  
|Opération|Mettre à jour les colonnes clés primaires|Les colonnes clés primaires des tables mémoire optimisées et les types de table ne peuvent pas être mis à jour. Si la clé primaire doit être mise à jour, supprimez l'ancienne ligne et insérez la nouvelle ligne avec la clé primaire mise à jour.|  
|Opération|CREATE INDEX|Les index sur les tables mémoire optimisées doivent être spécifiés inline avec l'instruction `CREATE TABLE`. Pour ajouter un index à une table mémoire optimisée, supprimez et recréez la table, notamment la spécification du nouvel index.|  
|Opération|ALTER TABLE|La modification des tables mémoire optimisées n'est pas prise en charge. Supprimez et recréez la table en utilisant la définition de table mise à jour.|  
|Opération|CREATE FULLTEXT INDEX|Les index de recherche en texte intégral ne sont pas pris en charge pour les tables mémoire optimisées.|  
|Opération|modification de schéma|Les tables mémoire optimisées et les procédures stockées compilées en mode natif ne prennent pas en charge les modifications de schéma, par exemple `sp_rename`.<br /><br /> Les tentatives de modification du schéma, telles que l'affectation d'un nouveau nom à une table, génèrent l'erreur 12320, les opérations qui nécessitent une modification de la version du schéma, par exemple l'affectation d'un nouveau nom, ne sont pas prises en charge par les tables mémoire optimisées.<br /><br /> Pour modifier le schéma, supprimez et recréez la table ou la procédure en utilisant une définition mise à jour.|  
|Opération|CREATE TRIGGER|Les déclencheurs sur les tables mémoire optimisées ne sont pas pris en charge.|  
|Opération|TRUNCATE TABLE|L'opération TRUNCATE n'est pas prise en charge pour les tables mémoire optimisées. Pour supprimer toutes les lignes d’une table, supprimez toutes `DELETE FROM`les lignes à l’aide de *table* ou supprimez la table, puis recréez-la.|  
|Opération|ALTER AUTHORIZATION|La modification du propriétaire d'une table mémoire optimisée ou d'une procédure stockée compilée en mode natif existante n'est pas prise en charge. Supprimez ou recréez la table ou la procédure pour modifier la propriété.|  
|Opération|ALTER SCHEMA|La modification du schéma d'une table mémoire optimisée ou d'une procédure stockée compilée en mode natif existante n'est pas prise en charge. Supprimez ou recréez la table ou la procédure pour modifier le schéma.|  
|Opération|DBCC CHECKTABLE|DBCC CHECKTABLE n'est pas pris en charge avec les tables mémoire optimisées.|  
|Fonctionnalité|ANSI_PADDING OFF|L'option de session `ANSI_PADDING` doit être activée (ON) lorsque vous créez des tables mémoire optimisées ou des procédures stockées compilées en mode natif. Exécutez `SET ANSI_PADDING ON` avant d'exécuter l'instruction CREATE.|  
|Option|DATA_COMPRESSION|La compression des données n'est pas prise en charge pour les tables optimisées en mémoire. Supprimez l'option de la définition de table.|  
|Fonctionnalité|DTC|Les tables optimisées en mémoire et les procédures stockées compilées en mode natif ne sont pas accessibles à partir de transactions distribuées. Utilisez plutôt des transactions SQL.|  
|Fonctionnalité|MARS (Multiple Active Result Sets)|Multiple Active Result Sets (MARS) n'est pas pris en charge avec les tables mémoire optimisées. Cette erreur peut également indiquer l'utilisation d'un serveur lié. Un serveur lié peut utiliser MARS. Les serveurs liés ne sont pas pris en charge avec les tables mémoire optimisées. À la place, connectez-vous directement au serveur et à la base de données qui héberge les tables mémoire optimisées.|  
|Opération|Tables optimisées en mémoire comme cibles de MERGE|Les tables mémoire optimisées ne peuvent pas être la cible d'une opération `MERGE`. Utilisez des instructions `INSERT`, `UPDATE` ou `DELETE` à la place.|  
  
## <a name="indexes-on-memory-optimized-tables"></a>Index sur des tables optimisées en mémoire  
 Le tableau suivant répertorie les fonctionnalités et les mots clés [!INCLUDE[tsql](../../includes/tsql-md.md)] qui peuvent s'afficher dans le texte d'un message d'erreur qui implique un index sur une table optimisée en mémoire, ainsi que l'action corrective à entreprendre pour résoudre l'erreur.  
  
|Type|Nom|Solution|  
|----------|----------|----------------|  
|Fonctionnalité|Index filtré|Les index filtrés ne sont pris en charge avec les tables optimisées en mémoire. Omettez la clause `WHERE` de la spécification d'index.|  
|Fonctionnalité|UNIQUE|Les index uniques ne sont pas pris en charge pour les tables mémoire optimisées. Supprimez l'argument `UNIQUE` de la spécification d'index.|  
|Fonctionnalité|Colonnes nullable|Toutes les colonnes d'une clé d'index sur une table mémoire optimisée doivent être spécifiés en tant que `NOT NULL`. Incluez la contrainte `NOT NULL` avec toutes les colonnes des clés d'index.|  
|Fonctionnalité|classement non-bin2|Toutes les colonnes de caractères d'une clé d'index sur une table mémoire optimisée doivent être déclarés en tant que classement BIN2. Utilisez la clause `COLLATE` pour définir le classement dans la définition de colonne. Pour plus d'informations, consultez [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).|  
|Fonctionnalité|Colonnes incluses|La spécification de colonnes incluses n'est pas nécessaire pour les tables mémoire optimisées. Toutes les colonnes de la table mémoire optimisée sont incluses implicitement dans chaque index mémoire optimisé.|  
|Opération|ALTER INDEX|La modification des index sur les tables mémoire optimisées n'est pas prise en charge. À la place, supprimez et recréez la table en utilisant la spécification d'index mise à jour.|  
|Opération|DROP INDEX|La suppression des index sur les tables mémoire optimisées n'est pas prise en charge. À la place, supprimez et recréez la table en utilisant les index souhaités.|  
|Option d'index|*Option d'index*|L'option d'index indiquée n'est pas prise en charge avec des index sur les tables mémoire optimisées. Supprimez l'option de la spécification d'index.|  
  
## <a name="nonclustered-hash-indexes"></a>Index de hachage non cluster  
 Le tableau suivant répertorie les fonctionnalités et les mots clés [!INCLUDE[tsql](../../includes/tsql-md.md)] qui peuvent s'afficher dans le texte d'un message d'erreur qui implique un index de hachage non cluster, ainsi que l'action corrective à entreprendre pour résoudre l'erreur.  
  
|Type|Nom|Solution|  
|----------|----------|----------------|  
|Option|ASC/DESC|Les index de hachage non cluster ne sont pas ordonnés. Supprimez les mots clés `ASC` et `DESC` de la spécification de clé d'index.|  
  
## <a name="natively-compiled-stored-procedures"></a>procédures stockées compilées en mode natif  
 Le tableau suivant répertorie les fonctionnalités et les mots clés [!INCLUDE[tsql](../../includes/tsql-md.md)] qui peuvent s'afficher dans le texte d'un message d'erreur qui implique des procédures stockées compilées en mode natif, ainsi que l'action corrective à entreprendre pour résoudre l'erreur.  
  
|Type|Fonctionnalité|Solution|  
|----------|-------------|----------------|  
|Fonctionnalité|Variables de table inline|Les types de table ne peuvent pas être déclarés inline avec des déclarations de variable. Les types de table doivent être déclarés explicitement à l'aide d'une instruction `CREATE TYPE`.|  
|Fonctionnalité|Curseurs|Les curseurs ne sont pas pris en charge sur ou dans les procédures stockées compilées en mode natif.<br /><br /> -Lors de l’exécution de la procédure à partir du client, utilisez RPC plutôt que l’API de curseur. Avec ODBC, évitez l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)]`EXECUTE`, et spécifiez directement le nom de la procédure à la place.<br /><br /> -Lors de l’exécution de la procédure [!INCLUDE[tsql](../../includes/tsql-md.md)] à partir d’un lot ou d’une autre procédure stockée, évitez d’utiliser un curseur avec la procédure stockée compilée en mode natif.<br /><br /> -Lors de la création d’une procédure stockée compilée en mode natif, plutôt que d’utiliser un curseur, `WHILE` utilisez une logique basée sur un ensemble ou une boucle.|  
|Fonctionnalité|Valeurs par défaut non constantes des paramètres|Lors de l'utilisation des valeurs par défaut avec des paramètres sur les procédures stockées compilées en mode natif, les valeurs doivent être constantes. Supprimez les caractères génériques des déclarations de paramètre.|  
|Fonctionnalité|EXTERNAL|Les procédures stockées CLR ne peuvent pas être compilées en mode natif. Supprimez la clause AS EXTERNAL ou l'option NATIVE_COMPILATION de l'instruction CREATE PROCEDURE.|  
|Fonctionnalité|Procédures stockées numérotées|Les procédures stockées compilées en mode natif ne peuvent pas être numérotées. Supprimez `;`le *nombre* de `CREATE PROCEDURE` l’instruction.|  
|Fonctionnalité|INSERTION de plusieurs lignes... Instructions VALUEs|Impossible d'insérer plusieurs lignes en utilisant la même instruction `INSERT` dans une procédure stockée compilée en mode natif. Créez des instructions `INSERT` pour chaque ligne.|  
|Fonctionnalité|Expressions de table communes|Les expressions de table communes ne sont pas prises en charge dans les procédures stockées compilées en mode natif. Réécrire la requête.|  
|Fonctionnalité|sous-requête|Les sous-requêtes (requêtes imbriquées dans une autre requête) ne sont pas prises en charge. Réécrire la requête.|  
|Fonctionnalité|COMPUTE|La clause `COMPUTE` n'est pas prise en charge. Supprimez-la de la requête.|  
|Fonctionnalité|SELECT INTO|La clause `INTO` n'est pas prise en charge avec l'instruction `SELECT`. Réécrivez la requête sous `INSERT INTO`forme de *table*`SELECT`.|  
|Fonctionnalité|OUTPUT|La clause `OUTPUT` n'est pas prise en charge. Supprimez-la de la requête.|  
|Fonctionnalité|liste de colonnes d'insertion incomplète|Dans les instructions `INSERT`, des valeurs doivent être spécifiées pour toutes les colonnes de la table.|  
|Fonction|*Fonction*|La fonction intégrée n'est pas prise en charge dans les procédures stockées compilées en mode natif. Supprimez la fonction de la procédure stockée. Pour plus d’informations sur les fonctions intégrées prises en charge, consultez [procédures stockées compilées en mode natif](../in-memory-oltp/natively-compiled-stored-procedures.md).|  
|Fonctionnalité|CASE|L'instruction `CASE` n'est pas prise en charge dans les requêtes à l'intérieur de procédures stockées compilées en mode natif. Créez des requêtes pour chaque cas. Pour plus d’informations, consultez [implémentation d’une instruction case](implementing-a-case-expression-in-a-natively-compiled-stored-procedure.md).|  
|Fonctionnalité|fonctions définies par l'utilisateur|Les fonctions définies par l'utilisateur ne peuvent pas être utilisées dans les procédures stockées compilées en mode natif. Supprimez la référence à la fonction de la définition de procédure.|  
|Fonctionnalité|agrégats définis par l'utilisateur|Les fonctions d'agrégation définies par l'utilisateur ne peuvent pas être utilisées dans les procédures stockées compilées en mode natif. Supprimez la référence à la fonction dans la procédure.|  
|Fonctionnalité|métadonnées de modes de navigation|Les procédures stockées compilées en mode natif ne prennent pas en charge les métadonnées de modes de navigation. Assurez-vous que l'option de session `NO_BROWSETABLE` est désactivée (OFF).|  
|Fonctionnalité|DELETE avec la clause FROM|La clause `FROM` n'est pas prise en charge pour les instructions `DELETE` avec une table source dans les procédures stockées compilées en mode natif.<br /><br /> `DELETE` avec la clause `FROM` est prise en charge lorsqu'elle est utilisée pour indiquer de la table dans laquelle la suppression doit avoir lieu.|  
|Fonctionnalité|UPDATE avec la clause FROM|La clause `FROM` n'est pas prise en charge pour les instructions `UPDATE` dans les procédures stockées compilées en mode natif.|  
|Fonctionnalité|procédures temporaires|Les procédures stockées temporaires ne peuvent pas être compilées en mode natif. Créez une procédure stockée compilée en mode natif permanente ou une procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] interprétée.|  
|Niveau d'isolation|READ UNCOMMITTED|Le niveau d'isolation READ UNCOMMITTED n'est pas pris en charge pour les procédures stockées compilées en mode natif. Utilisez un niveau d'isolation pris en charge, tel que SNAPSHOT.|  
|Niveau d'isolation|READ COMMITTED|Le niveau d'isolation READ UNCOMMITTED n'est pas pris en charge pour les procédures stockées compilées en mode natif. Utilisez un niveau d'isolation pris en charge, tel que SNAPSHOT.|  
|Fonctionnalité|tables temporaires|Les tables de tempdb ne peuvent pas être utilisées dans les procédures stockées compilées en mode natif. À la place, utilisez une variable de table ou une table mémoire optimisée avec DURABILITY=SCHEMA_ONLY.|  
|Fonctionnalité|MARS|MARS (multiple Active Results Sets) n'est pas pris en charge avec les procédures stockées compilées en mode natif. Cette erreur peut également indiquer l'utilisation d'un serveur lié. Un serveur lié peut utiliser MARS. Les serveurs liés ne sont pas pris en charge avec les procédures stockées compilées en mode natif. À la place, connectez-vous directement au serveur et à la base de données qui héberge les procédures stockées compilées en mode natif.|  
|Fonctionnalité|DTC|Les tables optimisées en mémoire et les procédures stockées compilées en mode natif ne sont pas accessibles à partir de transactions distribuées. Utilisez plutôt des transactions SQL.|  
|Fonctionnalité|classement non-bin2|La comparaison, le tri et d'autres opérations sur les chaînes de caractères dans les procédures stockées compilées en mode natif exigent l'utilisation d'un classement BIN2. Utilisez la clause COLLATE ou des colonnes et des variables avec un classement approprié. Pour plus d'informations, consultez [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).|  
|Fonctionnalité|Troncation des chaînes de caractères avec un classement SC.|Les chaînes de caractères avec un classement `_SC` utilisent le codage UTF-16. La conversion d'une valeur n(var)char en valeur n(var)char plus courte implique la troncation. Cette opération n'est pas prise en charge pour les valeurs UTF-16 dans les procédures stockées compilées en mode natif. Évitez la troncation de chaînes UTF-16.|  
|Fonctionnalité|EXECUTE WITH RECOMPILE|L'option `WITH RECOMPILE` n'est pas pris en charge avec les procédures stockées compilées en mode natif.|  
|Fonctionnalité|LEN et SUBSTRING avec un argument dans un classement SC|Les chaînes de caractères avec un classement _SC utilisent le codage UTF-16. Les fonctions intégrées LEN et SUBSTRING, utilisées dans des procédures stockées compilées en mode natif, ne prennent pas en charge l'encodage UTF-16. Utilisez un autre classement ou évitez d'utiliser ces fonctions.|  
|Fonctionnalité|Exécution à partir de la connexion administrateur dédiée.|Les procédures stockées compilées en mode natif ne peuvent pas être exécutées à partir de la connexion administrateur dédiée. Utilisez plutôt une connexion normale.|  
|Opération|ALTER PROCEDURE|Les procédures stockées compilées en mode natif ne peuvent pas être modifiées. Pour modifier la définition de la procédure, supprimez et recréez la procédure stockée.|  
|Opération|point d'enregistrement|Les procédures stockées compilées en mode natif ne peuvent pas être appelées à partir de transactions qui possèdent un point de sauvegarde actif. Supprimez le point de sauvegarde de la transaction.|  
|Opération|ALTER AUTHORIZATION|La modification du propriétaire d'une table mémoire optimisée ou d'une procédure stockée compilée en mode natif existante n'est pas prise en charge. Supprimez ou recréez la table ou la procédure pour modifier la propriété.|  
|Opérateur|OPENROWSET|Cet opérateur n'est pas pris en charge. Supprimez `OPENROWSET` de la procédure stockée compilée en mode natif.|  
|Opérateur|OPENQUERY|Cet opérateur n'est pas pris en charge. Supprimez `OPENQUERY` de la procédure stockée compilée en mode natif.|  
|Opérateur|OPENDATASOURCE|Cet opérateur n'est pas pris en charge. Supprimez `OPENDATASOURCE` de la procédure stockée compilée en mode natif.|  
|Opérateur|OPENXML|Cet opérateur n'est pas pris en charge. Supprimez `OPENXML` de la procédure stockée compilée en mode natif.|  
|Opérateur|CONTAINSTABLE|Cet opérateur n'est pas pris en charge. Supprimez `CONTAINSTABLE` de la procédure stockée compilée en mode natif.|  
|Opérateur|FREETEXTTABLE|Cet opérateur n'est pas pris en charge. Supprimez `FREETEXTTABLE` de la procédure stockée compilée en mode natif.|  
|Fonctionnalité|fonctions table|Les fonctions table ne peuvent pas être référencées à partir de procédures stockées compilées en mode natif. Une solution de contournement possible pour cette restriction consiste à ajouter la logique des fonctions tables au corps de la procédure.|  
|Opérateur|CHANGETABLE|Cet opérateur n'est pas pris en charge. Supprimez `CHANGETABLE` de la procédure stockée compilée en mode natif.|  
|Opérateur|GOTO|Cet opérateur n'est pas pris en charge. Utilisez d'autres constructions de procédure, telles que WHILE.|  
|Opérateur|EXECUTE, INSERT EXEC|L'imbrication de procédures stockées compilées en mode natif n'est pas prise en charge. Les opérations nécessaires peuvent être spécifiées inline, dans le cadre de la définition de procédure stockée.|  
|Opérateur|OFFSET|Cet opérateur n'est pas pris en charge. Supprimez `OFFSET` de la procédure stockée compilée en mode natif.|  
|Opérateur|UNION|Cet opérateur n'est pas pris en charge. Supprimez `UNION` de la procédure stockée compilée en mode natif. La combinaison de plusieurs jeux de résultats en un jeu de résultats unique peut être effectuée en utilisant une variable de table.|  
|Opérateur|INTERSECT|Cet opérateur n'est pas pris en charge. Supprimez `INTERSECT` de la procédure stockée compilée en mode natif. Dans certain cas, INNER JOIN permet d'obtenir le même résultat.|  
|Opérateur|EXCEPT|Cet opérateur n'est pas pris en charge. Supprimez `EXCEPT` de la procédure stockée compilée en mode natif.|  
|Opérateur|OUTER JOIN|Cet opérateur n'est pas pris en charge. Supprimez `OUTER JOIN` de la procédure stockée compilée en mode natif. Pour plus d’informations, consultez [implémentation d’une jointure externe](implementing-an-outer-join.md).|  
|Opérateur|APPLY|Cet opérateur n'est pas pris en charge. Supprimez `APPLY` de la procédure stockée compilée en mode natif.|  
|Opérateur|PIVOT|Cet opérateur n'est pas pris en charge. Supprimez `PIVOT` de la procédure stockée compilée en mode natif.|  
|Opérateur|UNPIVOT|Cet opérateur n'est pas pris en charge. Supprimez `UNPIVOT` de la procédure stockée compilée en mode natif.|  
|Opérateur|OR, IN|La disjonction (OR, IN) n'est pas prise en charge dans la clause WHERE pour les requêtes dans les procédures stockées compilées en mode natif. Créez des requêtes pour chaque cas.|  
|Opérateur|CONTAINS|Cet opérateur n'est pas pris en charge. Supprimez `CONTAINS` de la procédure stockée compilée en mode natif.|  
|Opérateur|FREETEXT|Cet opérateur n'est pas pris en charge. Supprimez `FREETEXT` de la procédure stockée compilée en mode natif.|  
|Opérateur|NOT|Cet opérateur n'est pas pris en charge. Supprimez `NOT` de la procédure stockée compilée en mode natif. Dans certains cas, `NOT` peut être remplacé par une inégalité. Par exemple, `NOT a=b` peut être remplacé par `a!=b`.|  
|Opérateur|TSEQUAL|Cet opérateur n'est pas pris en charge. Supprimez `TSEQUAL` de la procédure stockée compilée en mode natif.|  
|Opérateur|LIKE|Cet opérateur n'est pas pris en charge. Supprimez `LIKE` de la procédure stockée compilée en mode natif.|  
|Opérateur|NEXT VALUE FOR|Les séquences ne peuvent pas être référencées dans les procédures stockées compilées en mode natif. Obtenez la valeur en utilisant [!INCLUDE[tsql](../../includes/tsql-md.md)]interprété, puis passez-la dans la procédure stockée compilée en mode natif. Pour plus d’informations, consultez [Implémentation d’IDENTITY dans une table mémoire optimisée](implementing-identity-in-a-memory-optimized-table.md).|  
|Option Set|*option*|Les options SET peuvent être modifiées dans les procédures stockées compilées en mode natif. Certaines options peuvent être définies avec l'instruction BEGIN ATOMIC. Pour plus d'informations, consultez la section sur les blocs atomiques dans [Natively Compiled Stored Procedures](../in-memory-oltp/natively-compiled-stored-procedures.md).|  
|Opérande|TABLESAMPLE|Cet opérateur n'est pas pris en charge. Supprimez `TABLESAMPLE` de la procédure stockée compilée en mode natif.|  
|Option|RECOMPILE|Les procédures stockées compilées en mode natif sont compilées au moment de la création. Pour recompiler une procédure stockée compilée en mode natif, supprimez-la, puis recréez-la. Supprimez `RECOMPILE` de la définition de la procédure.|  
|Option|ENCRYPTION|Cette option n'est pas prise en charge. Supprimez `ENCRYPTION` de la définition de la procédure.|  
|Option|FOR REPLICATION|Les procédures stockées compilées en mode natif ne peuvent pas être créées pour la réplication. Supprimez `FOR REPLICATION` de la définition de procédure.|  
|Option|FOR XML|Cette option n'est pas prise en charge. Supprimez `FOR XML` de la procédure stockée compilée en mode natif.|  
|Option|FOR BROWSE|Cette option n'est pas prise en charge. Supprimez `FOR BROWSE` de la procédure stockée compilée en mode natif.|  
|Indicateur de jointure|HASH, MERGE|Les procédures stockées compilées en mode natif ne prennent en charge que les jointures de boucles imbriquées. Les jointures de hachage et de fusion ne sont pas prises en charge. Supprimez l'indicateur de jointure.|  
|Indicateur de requête|*Indicateur de requête*|Cet indicateur de requête n'est pas pris en charge dans les procédures stockées compilées en mode natif. Pour obtenir les indicateurs de requête pris en charge, consultez [Indicateurs de requête &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query).|  
|Option|DISTINCT|Cette option n'est pas prise en charge. Supprimez `DISTINCT` de la requête dans la procédure stockée compilée en mode natif.|  
|Option|PERCENT|Cette option n'est pas prise en charge avec les clauses `TOP`. Supprimez `PERCENT` de la requête dans la procédure stockée compilée en mode natif.|  
|Option|WITH TIES|Cette option n'est pas prise en charge avec les clauses `TOP`. Supprimez `WITH TIES` de la requête dans la procédure stockée compilée en mode natif.|  
|Fonction d'agrégation|*Fonction d’agrégation*|Cette clause n'est pas prise en charge. Pour plus d'informations sur les fonctions d'agrégation dans les procédures stockées compilées en mode natif, consultez [Natively Compiled Stored Procedures](../in-memory-oltp/natively-compiled-stored-procedures.md).|  
|Fonction de classement|*Fonction de classement*|Les fonctions de classement ne sont pas prises en charge dans les procédures stockées compilées en mode natif. Supprimez-les de la définition de procédure.|  
|Fonction|*Fonction*|Cette fonction n'est pas prise en charge. Supprimez-la de la procédure stockée compilée en mode natif.|  
|.|*.*|Cette instruction n'est pas prise en charge. Supprimez-la de la procédure stockée compilée en mode natif.|  
|Fonctionnalité|MIN et MAX utilisé avec des chaînes binaires et de caractères|Les fonctions d'agrégation `MIN` et `MAX` ne peuvent pas être utilisées pour les valeurs de chaîne de caractère et binaire dans les procédures stockées compilées en mode natif.|  
|Fonctionnalité|GROUP BY sans fonction d'agrégation|Dans les procédures stockées compilées en mode natif, lorsqu'une requête contient une clause `GROUP BY`, elle doit également utiliser une fonction d'agrégation dans la clause SELECT ou HAVING. Ajoutez une fonction d'agrégation à la requête.|  
|Fonctionnalité|GROUP BY ALL|ALL ne peut pas être utilisé avec les clauses GROUP BY dans des procédures stockées compilées en mode natif. Supprimez ALL de la clause GROUP BY.|  
|Fonctionnalité|GROUP BY ()|Le regroupement par une liste vide n'est pas pris en charge. Supprimez la clause GROUP BY, ou incluez des colonnes dans la liste de regroupement.|  
|Fonctionnalité|ROLLUP|`ROLLUP` ne peut pas être utilisé avec les clauses `GROUP BY` dans des procédures stockées compilées en mode natif. Supprimez `ROLLUP` de la définition de la procédure.|  
|Fonctionnalité|CUBE|`CUBE` ne peut pas être utilisé avec les clauses `GROUP BY` dans des procédures stockées compilées en mode natif. Supprimez `CUBE` de la définition de la procédure.|  
|Fonctionnalité|GROUPING SETS|`GROUPING SETS` ne peut pas être utilisé avec les clauses `GROUP BY` dans des procédures stockées compilées en mode natif. Supprimez `GROUPING SETS` de la définition de la procédure.|  
|Fonctionnalité|BEGIN TRANSACTION, COMMIT TRANSACTION et ROLLBACK TRANSACTION|Utilisez des blocs ATOMIC pour contrôler les transactions et la gestion des erreurs. Pour plus d’informations, consultez [Atomic Blocks](atomic-blocks-in-native-procedures.md).|  
|Fonctionnalité|Déclarations de variables de table inline.|Les variables de table doivent référencer les types de tables mémoire optimisées définis. Vous devez créer un type de table mémoire optimisée et utiliser ce type pour la déclaration de variable, plutôt que spécifier le type inline.|  
|Fonctionnalité|sp_recompile|La recompilation de procédures stockées compilées en mode natif n'est pas prise en charge. Supprimez et recréez la procédure.|  
|Fonctionnalité|EXECUTE AS CALLER|La clause `EXECUTE AS` est obligatoire. Mais `EXECUTE AS CALLER` n'est pas prise en charge. Utilisez `EXECUTE AS OWNER`, `EXECUTE AS` *User*ou `EXECUTE AS SELF`.|  
|Fonctionnalité|Tables sur disque|Les tables sur disque ne sont pas accessibles à partir de procédures stockées compilées en mode natif. Supprimez les références aux tables sur disque dans les procédures stockées compilées en mode natif. Sinon, migrez les tables sur disques vers des tables mémoire optimisées.|  
|Fonctionnalité|Les vues|Les vues ne sont pas accessibles à partir de procédures stockées compilées en mode natif. Au lieu d'utiliser des vues, référencez les tables de base sous-jacentes.|  
|Fonctionnalité|Fonctions table|Les fonctions table ne sont pas accessibles à partir de procédures stockées compilées en mode natif. Supprimez les références aux fonctions table dans les procédures stockées compilées en mode natif.|  
  
## <a name="transactions-that-access-memory-optimized-tables"></a>Transactions qui accèdent aux tables mémoire optimisées  
 Le tableau suivant répertorie les fonctionnalités et les mots clés [!INCLUDE[tsql](../../includes/tsql-md.md)] qui peuvent s'afficher dans le texte d'un message d'erreur qui implique des transactions qui accèdent aux tables mémoire optimisées, ainsi que l'action corrective à entreprendre pour résoudre l'erreur.  
  
|Type|Nom|Solution|  
|----------|----------|----------------|  
|Fonctionnalité|point d'enregistrement|La création de points de sauvegarde dans des transactions qui accèdent aux tables mémoire optimisées n'est pas prise en charge.|  
|Fonctionnalité|transaction liée|Les sessions liées ne peuvent pas participer dans des transactions qui accèdent aux tables mémoire optimisées. Ne liez pas la session avant d'exécuter la procédure.|  
|Fonctionnalité|DTC|Les transactions qui accèdent aux tables mémoire optimisées ne peuvent pas être des transactions distribuées.|  
  
## <a name="see-also"></a>Voir aussi  
 [Migration vers OLTP en mémoire](migrating-to-in-memory-oltp.md)  
  
  
