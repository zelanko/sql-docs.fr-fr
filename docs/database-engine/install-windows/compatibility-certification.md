---
title: Certification de compatibilité | Microsoft Docs
ms.custom: ''
ms.date: 08/26/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], after upgrade
- Database Engine [SQL Server], upgrading
- Databases [SQL Server], upgrading
- Database Engine [SQL Server], upgrading
- compatibility [SQL Server], certification
- compatibility level [SQL Server], upgrades
ms.assetid: 3c036813-36cf-4415-a0c9-248d0a433856
author: pmasl
ms.author: pelopes
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: a133f41fb429a2cfe910020e1fefb768436888c4
ms.sourcegitcommit: af6f66cc3603b785a7d2d73d7338961a5c76c793
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73142785"
---
# <a name="compatibility-certification"></a>Certification de compatibilité

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

La certification de compatibilité permet aux entreprises de mettre à niveau et de moderniser une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale, dans le cloud et à la périphérie, éliminant ainsi les risques de compatibilité des applications. 

Le même [!INCLUDE[ssde_md](../../includes/ssde_md.md)] alimente à la fois [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] (avec instance managée). Ce [!INCLUDE[ssde_md](../../includes/ssde_md.md)] partagé signifie qu’une base de données utilisateur peut être déplacée sans interruption entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] en local, tandis que le code d’application qui s’exécute dans la base de données en tant que [!INCLUDE[tsql](../../includes/tsql-md.md)] continue de fonctionner comme dans son système source.

Pour chaque nouvelle version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le niveau de compatibilité par défaut est défini sur la version du [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Toutefois, le niveau de compatibilité des versions précédentes est conservé pour assurer la compatibilité continue des applications existantes. Cette matrice de compatibilité peut être consultée [ici](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md#supported-dbcompats).
Par conséquent, une application certifiée pour utiliser une version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] donnée était en fait certifiée pour fonctionner sur le niveau de compatibilité par défaut de cette version.

Par exemple, le niveau de compatibilité de base de données 130 était la valeur par défaut dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Étant donné que les niveaux de compatibilité imposent des comportements d’optimisation des requêtes et des fonctions [!INCLUDE[tsql](../../includes/tsql-md.md)] spécifiques, une base de données certifiée pour fonctionner sur [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] était implicitement certifiée au niveau de compatibilité de base de données 130. Cette base de données peut fonctionner telle quelle sur une version plus récente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (comme [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) et [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)], tant que le niveau de compatibilité de la base de données conserve la valeur 130. 

Il s’agit d’un principe fondamental pour le modèle d’opération d’intégration continue [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]. Le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] est en permanence amélioré et mis à niveau dans Azure, mais comme les bases de données existantes conservent leur niveau de compatibilité actuel, elles continuent de fonctionner comme prévu même après les mises à niveau apportées au [!INCLUDE[ssde_md](../../includes/ssde_md.md)] sous-jacent. 

## <a name="managing-upgrade-risk-with-compatibility-certification"></a>Gestion des risques de mise à niveau avec la certification de compatibilité
L’utilisation de la certification de compatibilité est une approche intéressante de la modernisation des bases de données. Avec une certification basée sur le niveau de compatibilité, les développeurs définissent les exigences techniques pour qu’une application soit prise en charge sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)], mais dissocient le cycle de vie de l’application du cycle de vie de la plateforme de base de données. Cela permet aux entreprises de garder le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] à jour comme demandé par les stratégies de cycle de vie, de tirer parti des nouvelles améliorations en matière de scalabilité et de performances qui ne sont pas dépendantes du code et de connecter les applications pour **conserver leur état opérationnel** pendant les mises à niveau.

La possibilité de nuire aux fonctionnalités et aux performances est le principal facteur de risque pour toutes les mises à niveau. La certification de compatibilité représente la tranquillité d’esprit en termes de gestion de ces risques de mise à niveau :

-  En ce qui concerne le comportement de [!INCLUDE[tsql](../../includes/tsql-md.md)], toute modification signifie que l’exactitude d’une application doit être recertifiée. Toutefois, le paramètre de [niveau de compatibilité de la base de données](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md) fournit une compatibilité descendante avec les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uniquement pour la base de données spécifiée, et non pour l’ensemble du serveur. Le fait de conserver le niveau de compatibilité de la base de données en l’état garantit que les requêtes d’application existantes continuent d’afficher le même comportement avant et après une mise à niveau du [!INCLUDE[ssde_md](../../includes/ssde_md.md)]. Pour plus d’informations sur le comportement de [!INCLUDE[tsql](../../includes/tsql-md.md)] et les niveaux de compatibilité, consultez [Utilisation des niveaux de compatibilité pour la compatibilité descendante](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md#backwardCompat).

-  En ce qui concerne les performances, étant donné que des améliorations sont apportées à l’optimiseur de requête avec chaque version, il est possible que vous rencontriez des différences de plan de requête entre différentes versions du [!INCLUDE[ssde_md](../../includes/ssde_md.md)]. Les différences de plan de requête dans l’étendue d’une mise à niveau se traduisent généralement en risques quand certaines modifications peuvent nuire à une requête ou une charge de travail donnée. À leur tour, ces risques constituent un motif de recertification, qui peut retarder les mises à niveau et poser des problèmes de cycle de vie et de support. 
   L’atténuation des risques de mise à niveau est la raison pour laquelle les améliorations de l’optimiseur de requête sont contrôlées au niveau de compatibilité par défaut d’une nouvelle version. La certification de compatibilité comprend la **protection de la forme du plan de requête** : la notion de maintien d’un niveau de compatibilité de base de données en l’état immédiatement après une mise à niveau du [!INCLUDE[ssde_md](../../includes/ssde_md.md)] signifie que le modèle d’optimisation des requêtes utilisé pour créer des plans de requête dans la nouvelle version est le même qu’avant la mise à niveau et que la forme du plan de requête ne doit pas changer. 
   
   > [!NOTE]
   > La **forme de plan de requête** fait référence à la représentation visuelle des différents opérateurs qui composent un plan de requête. Cela inclut les opérateurs tels que les recherches, les analyses, les jointures et les tris, ainsi que les connexions entre eux qui indiquent le flux des données et l’ordre des opérations. La forme du plan de requête est déterminée par l’optimiseur de requête. Pour plus d’informations, consultez le [Guide d’architecture de traitement des requêtes](../../relational-databases/query-processing-architecture-guide.md#optimizing-select-statements).
   
   Pour plus d’informations, consultez [Utilisation des niveaux de compatibilité pour la compatibilité descendante](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md#backwardCompat).
   
Tant que l’application n’a pas besoin de tirer parti des améliorations disponibles uniquement dans un niveau de compatibilité de base de données plus élevé, il est judicieux de mettre à niveau le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et de conserver le niveau de compatibilité de base de données précédent, sans besoin de recertifier une application. Pour plus d’informations, consultez [Niveaux de compatibilité et mises à niveau du moteur de base de données](#compatibility-levels-and-database-engine-upgrades) plus loin dans cet article.

Pour un nouveau travail de développement ou quand une application existante exige l’utilisation de nouvelles fonctionnalités comme le [traitement de requêtes intelligent](../../relational-databases/performance/intelligent-query-processing.md) ou un nouveau [!INCLUDE[tsql](../../includes/tsql-md.md)], envisagez de mettre à niveau le niveau de compatibilité de base de données vers la dernière version disponible dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis certifiez votre application pour qu’elle fonctionne avec ce niveau de compatibilité. Pour plus d’informations sur la mise à niveau du niveau de compatibilité de base de données, consultez [Bonnes pratiques pour la mise à niveau du niveau de compatibilité de base de données](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md#best-practices-for-upgrading-database-compatibility-level).

## <a name="compatibility-certification-benefits"></a>Avantages de la certification de compatibilité
La certification de base de données présente plusieurs avantages immédiats, comme une approche basée sur la compatibilité plutôt qu’une approche de version nommée :

-  **Dissociation de la certification de l’application de la plateforme**. En raison de son [!INCLUDE[ssde_md](../../includes/ssde_md.md)] partagé, pour les applications qui ont juste besoin d’exécuter des requêtes [!INCLUDE[tsql](../../includes/tsql-md.md)], il n’est pas nécessaire de gérer des processus de certification distincts pour Azure et en local.
-  **Réduction des risques de mise à niveau** car, pendant la modernisation de la plateforme de base de données, les cycles de mise à niveau de l’application et de la couche de plateforme de base de données peuvent être séparés pour réduire les interruptions et améliorer la gestion des changements.
-  **Mise à niveau sans modification du code**. Il est possible de procéder à une mise à niveau de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] vers une nouvelle version sans modification du code en conservant le même niveau de compatibilité que le système source, et sans avoir à recertifier immédiatement jusqu’à ce que l’application doive tirer parti des améliorations disponibles uniquement dans un niveau de compatibilité de base de données plus élevé.
- **Amélioration de la gestion et de la scalabilité** sans nécessiter de modifications d’application, en utilisant des améliorations qui ne sont pas contrôlées par le niveau de compatibilité de la base de données. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], citons par exemple : 
  - Améliorations enrichies concernant la supervision et la résolution des problèmes, avec de nouvelles [vues de gestion dynamique système](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md), de nouveaux [événements étendus](../../relational-databases/extended-events/extended-events.md) et un nouveau [paramétrage automatique](../../relational-databases/automatic-tuning/automatic-tuning.md). 
  - Scalabilité améliorée avec [Soft-NUMA automatique](../../database-engine/configure-windows/soft-numa-sql-server.md#automatic-soft-numa).

Les nouvelles bases de données sont toujours définies sur le niveau de compatibilité par défaut de la version du [!INCLUDE[ssde_md](../../includes/ssde_md.md)]. Toutefois, quand une base de données passe d’une version antérieure quelconque de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers une nouvelle version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)], la base de données conserve son niveau de compatibilité existant. 

> [!IMPORTANT]
> Avant de déplacer une base de données vers une nouvelle version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)], vérifiez si le niveau de compatibilité de la base de données est toujours pris en charge. La matrice de prise en charge du niveau de compatibilité de la base de données peut être consultée [ici](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md#arguments). 
>
> Lors de la mise à niveau d’une base de données ayant un niveau de compatibilité inférieur à celui autorisé (par exemple, 90 qui était la valeur par défaut dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]), son niveau de compatibilité est défini sur la valeur la plus basse autorisée (100).
>
> Pour déterminer le niveau de compatibilité actuel, interrogez la colonne **compatibility_level** de [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).

## <a name="compatibility-levels-and-database-engine-upgrades"></a>Niveaux de compatibilité et mises à niveau du moteur de base de données
Pour mettre à niveau le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] vers la dernière version tout en conservant le niveau de compatibilité de base de données qui existait avant la mise à niveau et son état de capacité de prise en charge, il est recommandé de procéder à une validation de la surface d’exposition fonctionnelle statique du code d’application dans la base de données (objets de programmabilité tels que procédures, fonctions, déclencheurs stockés et autres) et dans l’application (en utilisant une trace de charge de travail qui capture le code dynamique envoyé par l’application) en utilisant l’outil [Assistant Migration de données Microsoft](https://www.microsoft.com/download/details.aspx?id=53595) (DMA). L’absence d’erreurs dans la sortie de l’outil DMA liées à l’absence ou à l’incompatibilité de fonctionnalités protège l’application contre des régressions fonctionnelles dans la nouvelle version cible. Pour plus d’informations, consultez [Vue d’ensemble de l’Assistant Migration de données](../../dma/dma-overview.md).

> [!NOTE]
> DMA prend en charge le niveau de compatibilité de base de données 100 et supérieur. L’utilisation de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] en tant que version source est exclue.   

> [!IMPORTANT]
> [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande de procéder à un test minime de façon à vérifier que la mise à niveau réussit tout en conservant le niveau de compatibilité de base de données précédent. Il vous appartient de déterminer ce à quoi correspond un test minime pour vos propres application et scénario.   

> [!NOTE]
> [!INCLUDE[msCoName](../../includes/msconame-md.md)] assure une protection de la forme du plan de requête quand :
>
> - La nouvelle version (cible) de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute sur du matériel comparable à celui sur lequel la précédente version (source) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécutait.
> - Le même [niveau de compatibilité de base de données pris en charge](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md#supported-dbcompats) est utilisé sur la version cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et sur la version source de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
>
> Toute régression de la forme du plan de requête (par rapport à la version source de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) qui se produit dans les conditions précédentes sera traitée. Contactez le Support technique Microsoft si c’est le cas.
  
## <a name="see-also"></a>Voir aussi 
[ALTER DATABASE COMPATIBILITY LEVEL](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)       
[Afficher ou modifier le niveau de compatibilité d’une base de données](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)       
[Bonnes pratiques pour la mise à niveau du niveau de compatibilité de base de données](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md#best-practices-for-upgrading-database-compatibility-level)      
