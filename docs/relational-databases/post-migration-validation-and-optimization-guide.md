---
title: "La Validation après la migration et Guide d’optimisation | Documents Microsoft"
ms.custom: 
ms.date: 5/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- post-migration validation and optimization
- guide, post-migration validation and optimization
ms.assetid: 11f8017e-5bc3-4bab-8060-c16282cfbac1
caps.latest.revision: 3
author: pelopes
ms.author: harinid
manager: 
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: d81eabfa1bdb5736bbf6f53ed34c2e1ac157e782
ms.contentlocale: fr-fr
ms.lasthandoff: 05/25/2017

---
# <a name="post-migration-validation-and-optimization-guide"></a>La Validation après la migration et Guide d’optimisation
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]post étape de migration est très essentiel de rapprochement de précision des données et l’exhaustivité, ainsi que découvrir des problèmes de performances avec la charge de travail.

# <a name="common-performance-scenarios"></a>Scénarios courants de performances 
Voici quelques-unes des scénarios courants de performances rencontrées après la migration vers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] plateforme et comment les résoudre. Ceux-ci incluent des scénarios qui sont specifdic à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migration (versions antérieures aux versions plus récentes), ainsi que la plateforme étrangère (par exemple, Oracle, DB2, MySQL et Sybase) à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migration.

## <a name="Parameter Sniffing"></a>Sensibilité de la détection des paramètres

**S’applique à :** étrangère plateforme (par exemple, Oracle, DB2, MySQL et Sybase) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migration.

> [!NOTE]
> Pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migrations, si ce problème n’existe dans la source de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], effectuer une migration vers une version plus récente de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en tant que-elle va pas traiter ce scénario. 

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Compile les plans de requête sur les procédures stockées à l’aide de la détection des paramètres d’entrée à la première compilation, générer un plan paramétrable et réutilisable, optimisé pour qu’une entrée de la distribution des données. Même si ne pas les procédures stockées, la plupart des instructions qui génèrent des plans triviaux sont paramétrables. Lorsqu’un plan est tout d’abord mis en cache, toute exécution ultérieure mappe à un plan mis en cache précédemment.
Un problème potentiel se produit lorsque que la première compilation ne peut-être pas avoir utilisées les plus courantes jeux de paramètres pour la charge de travail habituel. Pour des paramètres différents, le même plan d’exécution devient inefficace.

### <a name="steps-to-resolve"></a>Étapes de résolution

1.    Utilisez le `RECOMPILE` indicateur. Un plan est calculé chaque fois adaptée à chaque valeur de paramètre.
2.    Réécrivez la procédure stockée pour utiliser l’option `(OPTIMIZE FOR(<input parameter> = <value>))`. Déterminez la valeur à utiliser qui correspond le mieux à la plupart de la charge de travail pertinents, création et gestion d’un plan qui devient efficace pour la valeur paramétrable.
3.    Réécrivez la procédure stockée à l’aide de la variable locale à l’intérieur de la procédure. L’optimiseur utilise désormais le vecteur de densité pour estimations, ce qui entraîne le même plan, quelle que soit la valeur du paramètre.
4.    Réécrivez la procédure stockée pour utiliser l’option `(OPTIMIZE FOR UNKNOWN)`. Équivaut à l’aide de la technique de variable locale.
5.    Réécrivez la requête afin d’utiliser l’indicateur `DISABLE_PARAMETER_SNIFFING`. Même effet que l’utilisation de la technique de variable locale par totalement la désactivation de la détection des paramètres, sauf si `OPTION(RECOMPILE)`, `WITH RECOMPILE` ou `OPTIMIZE FOR <value>` est utilisé.

> [!TIP] 
> Optimisez la [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] fonctionnalité planifier une analyse pour identifier rapidement s’il s’agit d’un problème. Plus d’informations [ici](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-query-performance-troubleshooting-made-easier/).

## <a name="Missing indexes"></a>Index manquants

**S’applique à :** étrangère plate-forme (par exemple, Oracle, DB2, MySQL et Sybase) et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migration.

Index incorrectes ou manquantes provoque des e/s supplémentaires qui aboutissent à une mémoire supplémentaire et UC gaspillé. Cette fonction peut être, car le profil de charge de travail a changé par exemple à l’aide de différents prédicats, invalidant existant la conception d’index. Preuve d’une stratégie d’indexation médiocre ou des modifications dans le profil de charge de travail sont les suivantes :
-   Rechercher les doublon, redondant, rarement utilisé et index entièrement inutilisés.
-   Soin particulier avec les index non utilisés avec les mises à jour.

### <a name="steps-to-resolve"></a>Étapes de résolution

1.    Tirer parti du plan d’exécution graphique pour toutes les références de l’Index manquant.
2.    L’indexation des suggestions générées par [l’Assistant Paramétrage du moteur de base de données](../tools/dta/tutorial-database-engine-tuning-advisor.md).
3.    Tirer parti de la [DMV d’index manquants](../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md) ou via le [tableau de bord SQL Server Performance](https://www.microsoft.com/en-us/download/details.aspx?id=29063).
4.    Tirer parti des scripts préexistants qui DMV existants fournisse dans n’importe quel index manquants, en double, redondantes, rarement utilisés et entièrement inutilisés, mais également si toutes les références de l’index sont suggéré/codée en dur dans les procédures existantes et des fonctions dans votre base de données. 

> [!TIP] 
> Exemples de ces scripts préexistants [la création d’Index](https://github.com/Microsoft/tigertoolbox/tree/master/Index-Creation) et [informations sur les Index](https://github.com/Microsoft/tigertoolbox/tree/master/Index-Information). 

## <a name="Inability to use predicates"></a>Impossibilité d’utiliser des prédicats pour filtrer les données

**S’applique à :** étrangère plate-forme (par exemple, Oracle, DB2, MySQL et Sybase) et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migration.

> [!NOTE]
> Pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migrations, si ce problème n’existe dans la source de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], effectuer une migration vers une version plus récente de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en tant que-elle va pas traiter ce scénario.

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Optimiseur de requête peut uniquement compte pour plus d’informations sont connus au moment de la compilation. Si une charge de travail s’appuie sur les prédicats qui peuvent uniquement être connues au moment de l’exécution, le risque d’un choix de plan médiocres augmente. Pour un plan de meilleure qualité, les prédicats doivent être **SARGable**, ou **S**echerche **Arg**ument**en mesure de**.

Voici quelques exemples de prédicats sargables non :
-   Conversions implicites de données, tels que VARCHAR en NVARCHAR ou INT à VARCHAR. Recherchez des avertissements de CONVERT_IMPLICIT runtime dans les Plans d’exécution réel. Conversion d’un type à un autre peut également provoquer la perte de précision.
-   Les expressions indéterminées complexes telles que `WHERE UnitPrice + 1 < 3.975`, mais pas `WHERE UnitPrice < 320 * 200 * 32`.
-   Expressions à l’aide de fonctions, telles que `WHERE ABS(ProductID) = 771` ou`WHERE UPPER(LastName) = 'Smith'`
-   Chaînes avec un caractère générique au début, tel que `WHERE LastName LIKE '%Smith'`, mais pas `WHERE LastName LIKE 'Smith%'`.

### <a name="steps-to-resolve"></a>Étapes de résolution

1. Toujours déclarer les variables/paramètres comme la cible prévue [type de données](../t-sql/data-types/data-types-transact-sql.md). 
  -   Cette opération peut impliquer la comparaison d’une construction de code défini par l’utilisateur qui est stockée dans la base de données (par exemple, les procédures stockées, des fonctions définies par l’utilisateur ou des vues) avec les tables système qui contiennent des informations sur les types de données utilisés dans les tables sous-jacentes (telles que [sys.columns](../relational-databases/system-catalog-views/sys-columns-transact-sql.md)).
2. S’il est impossible de parcourir tout le code au point précédent, puis dans le même but, modifiez le type de données sur la table pour correspondre à toute déclaration de variable ou paramètre.
3. La raison à l’utilité des structures suivantes :
  -   Fonctions en cours utilisées comme prédicats ;
  -   Recherches par caractères génériques ;
  -   Les expressions complexes basées sur des données en colonnes : évaluer la nécessité de créer à la place des colonnes calculées persistantes, ce qui peuvent être indexées ;

> [!NOTE] 
> Programmaticaly tous les éléments ci-dessus peuvent être effectuée.

## <a name="Table Valued Functions"></a>Utilisation de fonctions table (plusieurs instructions Inline Visual Studio)

**S’applique à :** étrangère plate-forme (par exemple, Oracle, DB2, MySQL et Sybase) et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migration.

> [!NOTE]
> Pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migrations, si ce problème n’existe dans la source de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], effectuer une migration vers une version plus récente de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en tant que-elle va pas traiter ce scénario.

Fonctions table retournent un type de données de table qui peut constituer une alternative aux vues. Alors que les vues sont limitées à un seul `SELECT` instruction, des fonctions définies par l’utilisateur peuvent contenir des instructions supplémentaires qui permettent une logique supplémentaire qu’il n’est possible dans les vues.

> [!IMPORTANT] 
> Étant donné que la table de sortie d’un MSTVF (fonction table multi-instructions Table) n’est pas créée au moment de la compilation, le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] optimiseur de requête s’appuie sur les paramètres heuristiques et statistiques pas réelles, afin de déterminer les estimations de ligne. Même si les index sont ajoutés à l’ou plusieurs tables de base, cela ne va pas à l’aide. Pour MSTVFs, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilise une estimation fixe de 1 pour le nombre de lignes attendu doivent être retournées par une MSTVF (en commençant par [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] fixe d’estimation est 100 lignes).

### <a name="steps-to-resolve"></a>Étapes de résolution
1.    Si la fonction table à instructions multiples est la seule instruction, convertir les TVF Inline.

    ```tsql
    CREATE FUNCTION dbo.tfnGetRecentAddress(@ID int)
    RETURNS @tblAddress TABLE
    ([Address] VARCHAR(60) NOT NULL)
    AS
    BEGIN
      INSERT INTO @tblAddress ([Address])
      SELECT TOP 1 [AddressLine1]
      FROM [Person].[Address]
      WHERE  AddressID = @ID
      ORDER BY [ModifiedDate] DESC
    RETURN
    END
    ```
    Pour 

    ```tsql
    CREATE FUNCTION dbo.tfnGetRecentAddress_inline(@ID int)
    RETURNS TABLE
    AS
    RETURN (
      SELECT TOP 1 [AddressLine1] AS [Address]
      FROM [Person].[Address]
      WHERE  AddressID = @ID
      ORDER BY [ModifiedDate] DESC
    )
    ```

2.    Si elle est plus complexe, envisagez d’utiliser des résultats intermédiaires stockés dans des tables optimisées en mémoire ou des tables temporaires.

##  <a name="Additional_Reading"></a> Lecture supplémentaire  
 [Bonnes pratiques relatives au magasin de requêtes](../relational-databases/performance/best-practice-with-the-query-store.md)  
[Tables optimisées en mémoire](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
[Fonctions définies par l'utilisateur](../relational-databases/user-defined-functions/user-defined-functions.md)  
[Variables de table et de ligne des Estimations - partie 1](https://blogs.msdn.microsoft.com/blogdoezequiel/2012/11/30/table-variables-and-row-estimations-part-1/)  
[Variables de table et de ligne des Estimations - partie 2](https://blogs.msdn.microsoft.com/blogdoezequiel/2012/12/09/table-variables-and-row-estimations-part-2/)  
[La mise en cache du Plan d’exécution et réutilisation](../relational-databases/query-processing-architecture-guide.md#execution-plan-caching-and-reuse)

