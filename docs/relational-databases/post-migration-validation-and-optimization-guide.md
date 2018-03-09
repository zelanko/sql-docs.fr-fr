---
title: "Guide de validation et d’optimisation post-migration | Microsoft Docs"
ms.custom: 
ms.date: 5/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: relational-databases-misc
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- post-migration validation and optimization
- guide, post-migration validation and optimization
ms.assetid: 11f8017e-5bc3-4bab-8060-c16282cfbac1
caps.latest.revision: 
author: pelopes
ms.author: harinid
manager: 
ms.workload: Inactive
ms.openlocfilehash: 3264cab532c77a8e27daff0a3c5c1bd5ed801818
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2018
---
# <a name="post-migration-validation-and-optimization-guide"></a>Guide de validation et d’optimisation post-migration
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

L’étape post-migration de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est cruciale pour rapprocher et compléter les données, ainsi que pour détecter les problèmes de performances liés à la charge de travail.

# <a name="common-performance-scenarios"></a>Scénarios de performance courants 
Voici quelques-uns des scénarios de performance courants rencontrés après la migration vers la plateforme [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et leur résolution. Certains scénarios sont spécifiques à la migration de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (d’une version antérieure vers une version plus récente), d’autres à la migration d’une plateforme étrangère (comme Oracle, DB2, MySQL ou Sybase) vers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

## <a name="CEUpgrade"></a> Régression des requêtes en raison d’un changement de version CE

**S’applique à :** migration de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

Quand vous faites migrer une ancienne version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vers [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] ou ultérieur, et que vous passez au [niveau de compatibilité de base de données](../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) le plus récent, il est possible que les performances d’une charge de travail fassent l’objet d’une régression.

Cela vient du fait qu’à compter de [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], tous les changements de l’optimiseur de requête sont liés au [niveau de compatibilité de base de données](../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) le plus récent, de sorte que les plans ne sont pas changés au moment même de la mise à niveau, mais quand un utilisateur remplace l’option de base de données `COMPATIBILITY_LEVEL` par la plus récente. Cette fonctionnalité, en association avec le magasin de requêtes, vous offre un niveau de contrôle élevé sur les performances des requêtes dans le processus de mise à niveau. 

Pour plus d’informations sur les changements apportés à l’optimiseur de requête dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], consultez [Optimisation de vos plans de requête avec l’estimateur de cardinalité SQL Server 2014](http://msdn.microsoft.com/library/dn673537.aspx).

### <a name="steps-to-resolve"></a>Étapes de résolution

Remplacez le [niveau de compatibilité de base de données](../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) par celui de la version de la source, puis suivez la procédure de mise à niveau recommandée que présente l’image suivante :

![query-store-usage-5](../relational-databases/performance/media/query-store-usage-5.png "query-store-usage-5")  

Pour plus d’informations à ce sujet, consultez [Maintenir la stabilité des performances lors de la mise à niveau vers une version plus récente de SQL Server](../relational-databases/performance/query-store-usage-scenarios.md#CEUpgrade).

## <a name="ParameterSniffing"></a> Sensibilité de la détection de paramètres

**S’applique à :** Plateforme étrangère (par exemple Oracle, DB2, MySQL et Sybase) et à la migration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

> [!NOTE]
> Pour les migrations de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], si ce problème existe dans la source [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], la migration vers une version plus récente de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en l’état ne concerne pas ce scénario. 

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] compile les plans de requête sur les procédures stockées en utilisant la détection de paramètres d’entrée au moment de la première compilation, et en générant un plan paramétrable et réutilisable, optimisé pour la distribution des données d’entrée. Même s’il ne s’agit pas de procédures stockées, la plupart des instructions qui génèrent des plans triviaux sont paramétrables. Après la première mise en cache d’un plan, les exécutions futures sont mappées au plan déjà mis en cache.
Un problème peut se produire quand la première compilation n’a pas utilisé les jeux de paramètres les plus courants pour la charge de travail usuelle. Pour des paramètres distincts, le même plan d’exécution devient inefficace. Pour plus d’informations à ce sujet, consultez [Détection de paramètres](../relational-databases/query-processing-architecture-guide.md#ParamSniffing).

### <a name="steps-to-resolve"></a>Étapes de résolution

1.  Utilisez le conseil `RECOMPILE`. Un plan est calculé chaque fois de manière adaptée à chaque valeur de paramètre.
2.  Réécrivez la procédure stockée pour utiliser l’option `(OPTIMIZE FOR(<input parameter> = <value>))`. Déterminez la valeur à utiliser qui correspond le mieux à la plupart des charges de travail appropriées. Cela vous permet de créer et de gérer un plan qui devient efficace pour la valeur paramétrable.
3.  Réécrivez la procédure stockée en utilisant une variable locale dans la procédure. L’optimiseur utilise désormais le vecteur de densité pour les estimations, ce qui permet d’obtenir le même plan, quelle que soit la valeur du paramètre.
4.  Réécrivez la procédure stockée pour utiliser l’option `(OPTIMIZE FOR UNKNOWN)`. Même effet qu’avec la technique de la variable locale.
5.  Réécrivez la requête pour utiliser le conseil `DISABLE_PARAMETER_SNIFFING`. Même effet qu’avec la technique de la variable locale en désactivant totalement la détection de paramètres, sauf si `OPTION(RECOMPILE)`, `WITH RECOMPILE` ou `OPTIMIZE FOR <value>` est utilisé.

> [!TIP] 
> Tirez parti de la fonctionnalité d’analyse de plan de [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] pour déterminer rapidement s’il s’agit d’un problème. Plus d’informations disponibles [ici](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-query-performance-troubleshooting-made-easier/).

## <a name="MissingIndexes"></a> Index manquants

**S’applique à :** Plateforme étrangère (par exemple Oracle, DB2, MySQL et Sybase) et à la migration de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

Les index incorrects ou manquants provoquent des suppléments d’E/S qui entraînent un gaspillage de mémoire et d’UC. Cela peut être dû au fait que le profil de charge de travail a changé, par exemple en raison de l’utilisation d’autres prédicats ou à la suite de l’invalidation de la conception d’index existante. Voici comment identifier une mauvaise stratégie d’indexation ou l’existence de changements dans le profil de charge de travail :
-   Recherchez les index dupliqués, redondants, rarement utilisés et complètement inutilisés.
-   Prêtez une attention particulière aux index inutilisés avec des mises à jour.

### <a name="steps-to-resolve"></a>Étapes de résolution

1.  Tirez parti du plan d’exécution graphique pour toutes les références d’index manquantes.
2.  Indexez les suggestions générées par l’[Assistant Paramétrage du moteur de base de données](../tools/dta/tutorial-database-engine-tuning-advisor.md).
3.  Tirez parti de la [Vue DMV des index manquants](../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md) ou du [Tableau de bord Performances SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=29063).
4.  Tirez parti des scripts préexistants qui peuvent utiliser les vues DMV existantes pour fournir un insight des index manquants, dupliqués, redondants, rarement utilisés et complètement inutilisés, ainsi que des références d’index avec indicateur/codées en dur dans les procédures et fonctions de votre base de données. 

> [!TIP] 
> La [Création d’index](https://github.com/Microsoft/tigertoolbox/tree/master/Index-Creation) et les [Informations d’index](https://github.com/Microsoft/tigertoolbox/tree/master/Index-Information) sont des exemples de scripts préexistants. 

## <a name="InabilityPredicates"></a> Incapacité à utiliser les prédicats pour filtrer les données

**S’applique à :** Plateforme étrangère (par exemple Oracle, DB2, MySQL et Sybase) et à la migration de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

> [!NOTE]
> Pour les migrations de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], si ce problème existe dans la source [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], la migration vers une version plus récente de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en l’état ne concerne pas ce scénario.

L’optimiseur de requête [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut uniquement prendre en compte les informations connues au moment de la compilation. Si une charge de travail s’appuie sur des prédicats qui ne peuvent être connus qu’au moment de l’exécution, le potentiel d’un mauvais choix de plan augmente. Pour permettre l’amélioration de la qualité d’un plan, les prédicats doivent être **SARGable**, ou **S**earch **Arg**ument**able**.

Voici quelques exemples de prédicats non SARGable :
-   Conversions de données implicites, par exemple de VARCHAR à NVARCHAR, ou de INT à VARCHAR. Recherchez les avertissements d’exécution liés à CONVERT_IMPLICIT dans les plans d’exécution réels. La conversion d’un type vers un autre type peut également entraîner une perte de précision.
-   Expressions indéterminées complexes telles que `WHERE UnitPrice + 1 < 3.975` mais pas `WHERE UnitPrice < 320 * 200 * 32`.
-   Expressions utilisant des fonctions, telles que `WHERE ABS(ProductID) = 771` ou `WHERE UPPER(LastName) = 'Smith'`
-   Chaînes commençant par un caractère générique, par exemple `WHERE LastName LIKE '%Smith'` mais pas `WHERE LastName LIKE 'Smith%'`.

### <a name="steps-to-resolve"></a>Étapes de résolution

1. Déclarez toujours les variables/paramètres en tant que [type de données](../t-sql/data-types/data-types-transact-sql.md) cible prévu. 
  -   Cela peut impliquer la comparaison d’une construction de code définie par l’utilisateur et stockée dans la base de données (par exemple des procédures stockées, des fonctions définies par l’utilisateur ou des vues) aux tables système qui contiennent des informations sur les types de données utilisés dans les tables sous-jacentes (par exemple [sys.columns](../relational-databases/system-catalog-views/sys-columns-transact-sql.md)).
2. Si vous ne parvenez pas à traverser l’ensemble du code jusqu’au point précédent, pour la même finalité, changez le type de données de la table afin qu’il corresponde à une déclaration de variable/paramètre.
3. Vérifiez l’utili