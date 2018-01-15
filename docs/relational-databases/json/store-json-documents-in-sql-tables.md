---
title: Stocker des documents JSON dans SQL Server ou SQL Database | Microsoft Docs
ms.description: This article describes why and how to store and index JSON documents in SQL Server or SQL Database, and how to optimize queries over the JSON documents.
ms.custom: 
ms.date: 01/04/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 26aed92ee48c2dfd13605a9b830d1b33b4fd7f66
ms.sourcegitcommit: 4aeedbb88c60a4b035a49754eff48128714ad290
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2018
---
# <a name="store-json-documents-in-sql-server-or-sql-database"></a>Stocker des documents JSON dans SQL Server ou SQL Database
SQL Server et Azure SQL Database ont des fonctions JSON natives qui vous permettent d’analyser des documents JSON à l’aide du langage SQL standard. Vous pouvez désormais stocker des documents JSON dans SQL Server ou SQL Database et interroger les données JSON comme dans une base de données NoSQL. Cet article explique comment stocker des documents JSON dans SQL Server ou SQL Database.

## <a name="classic-tables"></a>Tables classiques

La façon la plus simple de stocker des documents JSON dans SQL Server ou SQL Database consiste à créer une table de deux colonnes simple qui contient l’ID et le contenu du document. Exemple :

```sql
create table WebSite.Logs (
    _id bigint primary key identity,
    log nvarchar(max)
);
```

Cette structure est équivalente aux collections que vous pouvez trouver dans les bases de données de document classiques. La clé primaire `_id` est une valeur à incrémentation automatique qui fournit un identificateur unique pour chaque document et permet d’effectuer des recherches rapides. Cette structure est un bon choix pour les scénarios NoSQL classiques dans lesquels vous souhaitez récupérer un document par son ID ou mettre à jour un document stocké par son ID.

Le type de données nvarchar(max) vous permet de stocker des documents JSON ayant une taille maximale de 2 Go. Toutefois, si vous êtes sûr que la taille de vos documents JSON n’est pas supérieure à 8 Ko, nous vous recommandons d’utiliser nvarchar(4000) au lieu de nvarchar(max) pour des raisons de performances.

L’exemple de table créé dans l’exemple précédent suppose que des documents JSON valides sont stockés dans la colonne `log`. Si vous souhaitez que soit enregistré du JSON valide dans la colonne `log`, vous pouvez ajouter une contrainte CHECK sur cette colonne. Exemple :

```sql
ALTER TABLE WebSite.Logs
    ADD CONSTRAINT \[Log record should be formatted as JSON\]
                   CHECK (ISJSON(log)=1)
```

Chaque fois qu’un utilisateur insère ou met à jour un document dans la table, cette contrainte vérifie que le document JSON est correctement mis en forme. Sans la contrainte, la table est optimisée pour les insertions, car tout document JSON est ajouté directement à la colonne sans aucun traitement.

Quand vous stockez vos documents JSON dans la table, vous pouvez utiliser le langage Transact-SQL standard pour les interroger. Exemple :

```sql
SELECT TOP 100 JSON\_VALUE(log, ‘$.severity’), AVG( CAST( JSON\_VALUE(log,’$.duration’) as float))
 FROM WebSite.Logs
 WHERE CAST( JSON_VALUE(log,’$.date’) as datetime) > @datetime
 GROUP BY JSON_VALUE(log, ‘$.severity’)
 HAVING AVG( CAST( JSON_VALUE(log,’$.duration’) as float) ) > 100
 ORDER BY CAST( JSON_VALUE(log,’$.duration’) as float) ) DESC
```

La possibilité d’utiliser *n’importe quelle* clause de requête et fonction T-SQL pour interroger des documents JSON est un réel avantage. SQL Server et SQL Database n’introduisent aucune contrainte dans les requêtes que vous pouvez utiliser pour analyser des documents JSON. Vous pouvez simplement extraire des valeurs d’un document JSON avec la fonction `JSON_VALUE` et les utiliser dans la requête comme toute autre valeur.

C’est la principale différence entre, d’une part, SQL Server et SQL Database et, d’autre part, les bases de données NoSQL classiques : dans Transact-SQL, vous avez probablement la fonction dont vous avez besoin pour traiter les données JSON.

## <a name="indexes"></a>Index

Si vous constatez que vos requêtes parcourent souvent les documents en fonction d’une propriété (par exemple, une propriété `severity` dans un document JSON), vous pouvez ajouter un index NONCLUSTERED classique sur la propriété pour accélérer les requêtes.

Vous pouvez créer une colonne calculée qui expose des valeurs JSON à partir des colonnes JSON sur le chemin spécifié (autrement dit, sur le chemin `$.severity`) et créer un index standard sur cette colonne calculée. Exemple :

```sql
create table WebSite.Logs (
    _id bigint primary key identity,
    log nvarchar(max),

    severity AS JSON_VALUE(log, '$.severity'),
    index ix_severity (severity)
);
```

La colonne calculée utilisée dans cet exemple est une colonne non persistante ou virtuelle qui n’entraîne aucune augmentation de l’espace occupé par la table. Elle est utilisée par l’index `ix_severity` pour améliorer les performances des requêtes, comme dans l’exemple suivant :

```sql
SELECT log
FROM Website.Logs
WHERE JSON_VALUE(log, '$.severity') = 'P4'
```

Une caractéristique importante de cet index est qu’il prend en charge les classements. Si votre colonne NVARCHAR d’origine a une propriété COLLATION (par exemple, un classement respectant la casse ou en fonction de la langue japonaise), l’index est organisé selon les règles de langue ou de respect de la casse associées à la colonne NVARCHAR. Cela peut être une fonctionnalité importante si vous développez des applications à l’échelle internationale qui doivent utiliser des règles de langue personnalisées quand elles traitent des documents JSON.

## <a name="large-tables--columnstore-format"></a>Tables de grande taille et mise en forme de columnstore

Si vous prévoyez un grand nombre de documents JSON dans votre collection, nous vous recommandons d’ajouter un index CLUSTERED COLUMNSTORE dans la collection, comme indiqué dans l’exemple suivant :

```sql
create sequence WebSite.LogID as bigint;
go
create table WebSite.Logs (
    _id bigint default(next value for WebSite.LogID),
    log nvarchar(max),

    INDEX cci CLUSTERED COLUMNSTORE
);
```

Un index CLUSTERED COLUMNSTORE fournit un taux de compression de données élevé (jusqu’à 25 fois plus important) qui peut considérablement réduire vos besoins en espace de stockage, baisser les coûts de stockage et améliorer les performances d’E/S de votre charge de travail. De plus, les index CLUSTERED COLUMNSTORE étant optimisés pour l’analytique et les analyses de table sur vos documents JSON, ils constituent probablement la meilleure option pour l’analytique des journaux.

L’exemple précédent utilise un objet de séquence pour attribuer des valeurs à la colonne `_id`. Les séquences et les identités sont des options valides pour la colonne d’ID.

## <a name="frequently-changing-documents--memory-optimized-tables"></a>Changement fréquent de documents et de tables à mémoire optimisée

Si vous prévoyez un grand nombre d’opérations de suppression, d’insertion et de mise à jour dans vos collections, vous pouvez stocker vos documents JSON dans des tables à mémoire optimisée. Les collections JSON à mémoire optimisée conservant toujours les données en mémoire, il n’existe aucune surcharge d’E/S pour le stockage. De plus, les collections JSON à mémoire optimisée sont complètement dépourvues de verrou ; autrement dit, les actions sur les documents ne bloquent aucune autre opération.

La seule chose à faire pour convertir une collection classique en collection à mémoire optimisée consiste à spécifier l’option **with (memory_optimized=on)** après la définition de table, comme indiqué dans l’exemple suivant. Vous disposez alors d’une version à mémoire optimisée de la collection JSON.

```sql
create table WebSite.Logs (
  _id bigint identity primary key nonclustered,
  log nvarchar(4000)
) with (memory_optimized=on)
```

Une table à mémoire optimisée est la meilleure option pour les documents qui changent fréquemment. Quand vous envisagez des tables à mémoire optimisée, prenez également en considération le niveau de performance. Si possible, utilisez NVARCHAR(4000) au lieu de NVARCHAR(max) pour les documents JSON dans vos collections à mémoire optimisée, car cela peut améliorer considérablement le niveau de performance.

Comme avec les tables classiques, vous pouvez ajouter des index sur les champs que vous exposez dans des tables à mémoire optimisée à l’aide de colonnes calculées. Exemple :

```sql
create table WebSite.Logs (

  _id bigint identity primary key nonclustered,
  log nvarchar(4000),

  severity AS cast(JSON_VALUE(log, '$.severity') as tinyint) persisted,
  index ix_severity (severity)

) with (memory_optimized=on)
```

Pour optimiser les performances, effectuez un cast de la valeur JSON vers le plus petit type possible pouvant contenir la valeur de la propriété. Dans l’exemple précédent, **tinyint** est utilisé.

Vous pouvez également placer les requêtes SQL qui mettent à jour les documents JSON dans des procédures stockées pour tirer parti de la compilation native. Exemple :

```sql
CREATE PROCEDURE WebSite.UpdateData(@Id int, @Property nvarchar(100), @Value nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION

AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    UPDATE WebSite.Logs
    SET log = JSON_MODIFY(log, @Property, @Value)
    WHERE _id = @Id;

END
```

Cette procédure compilée en mode natif prend la requête et crée un code .DLL qui exécute la requête. Il s’agit de l’approche la plus rapide pour interroger et mettre à jour des données.

## <a name="conclusion"></a>Conclusion

Les fonctions JSON natives dans SQL Server et SQL Database vous permettent de traiter des documents JSON comme dans les bases de données NoSQL. Chaque base de données - relationnelle ou NoSQL - présente des avantages et des inconvénients pour le traitement des données JSON. Le principal avantage du stockage des documents JSON dans SQL Server ou SQL Database est la prise en charge complète du langage SQL. Vous pouvez utiliser toute la palette du langage Transact-SQL pour traiter les données et configurer de nombreuses options de stockage (des index columnstore pour la compression à un taux élevé et l’analytique rapide aux tables à mémoire optimisée pour le traitement sans verrou). Parallèlement, vous tirez parti de fonctionnalités de sécurité et d’internationalisation matures que vous pouvez simplement réutiliser dans votre scénario NoSQL. Ce sont là d’excellentes raisons pour envisager de stocker les documents JSON dans SQL Server ou SQL Database.

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>En savoir plus sur la prise en charge intégrée de JSON dans SQL Server  
Pour accéder à un grand nombre de solutions spécifiques, de cas d’usage et de recommandations, consultez les [billets de blog sur la prise en charge intégrée de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) dans SQL Server et Azure SQL Database, écrits par Jovan Popovic (Microsoft Program Manager).
