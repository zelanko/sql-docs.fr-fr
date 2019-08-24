---
title: Nouveautés de Assistant Migration de données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 08/23/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, new features
ms.assetid: ''
author: HJToland3
ms.author: jtoland
ms.openlocfilehash: 2a4780c9be50275959a0f32091b90c518ccea124
ms.sourcegitcommit: 01c8df19cdf0670c02c645ac7d8cc9720c5db084
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "70000594"
---
# <a name="whats-new-in-data-migration-assistant"></a>Nouveautés de Data Migration Assistant
Cet article répertorie les ajouts dans chaque version de Assistant Migration de données (DMA).

## <a name="dma-v45"></a>DMA v 4.5

La version 4.5 de DMA assure la prise en charge de l’évaluation des packages de migration SQL Server Integration Services (SSIS) hébergés dans le système de fichiers vers Azure SQL Database ou Azure SQL Database Managed instance.

## <a name="dma-v44"></a>DMA v 4.4

La version de DMA v 4.4 prend en charge le chargement des évaluations sur Azure Migrate.

## <a name="dma-v43"></a>DMA v 4.3

La version 4.3 de DMA prend en charge les éléments suivants:

* Recommandations relatives aux références SKU pour les instances gérées de Azure SQL Database basées sur l’évaluation de la charge de travail.
* RDS SQL Server en tant que source pour les évaluations.
* Évaluations de travaux de l’agent pour Azure SQL Database instance gérée en tant que cible.
* La possibilité d’ignorer certaines règles d’évaluation; la liste des codes d’erreur spécifiée dans la propriété «ignoreErrorCodes» configurée dans DMA ne s’affiche pas dans les résultats de l’évaluation DMA.
* Évaluation des requêtes T-SQL dans les étapes de l’activité des travaux et indication des recommandations appropriées
* Évaluations des événements étendus (version préliminaire publique).

En outre, cette version de DMA offre des performances améliorées pour gérer un grand nombre d’objets de schéma dans les bases de données, ainsi que des correctifs de bogues liés à:

* Procédures compilées avec la compilation native, dans certains cas.
* Schémas de base de données complexes.

## <a name="dma-v42"></a>DMA v 4.2

La version 4.2 de DMA fournit la prise en charge de ligne de commande pour l’évaluation de la disponibilité cible pour une ou plusieurs instances de serveur lors de la migration à partir d’un SQL Server local vers une instance gérée Azure SQL Database. Les clients peuvent désormais utiliser la ligne de commande DMA pour collecter les métadonnées relatives à leur schéma de base de données, détecter les bloqueurs et en savoir plus sur les fonctionnalités partiellement prises en charge ou non prises en charge qui affectent la migration vers une instance gérée Azure SQL Database. Les résultats peuvent ensuite être rendus à l’aide du modèle de Power BI fourni.

## <a name="dma-v41"></a>DMA v 4.1

La version v 4.1 de DMA introduit la prise en charge de l’évaluation complète des bases de données SQL Serveres locales qui migrent vers Azure SQL Database Managed Instance.

Le flux de travail d’évaluation vous aide à détecter les problèmes suivants, qui peuvent affecter votre migration vers Azure SQL Database Managed Instance:

* **Fonctionnalités non prises en charge ou partiellement prises**en charge. DMA évalue votre base de données SQL Server source pour les fonctionnalités utilisées qui sont partiellement prises en charge ou non prises en charge sur le Azure SQL Database Managed Instance cible. L’outil fournit ensuite un ensemble complet de recommandations, d’approches alternatives disponibles dans Azure et d’atténuation des étapes afin que les clients puissent prendre en compte ces informations lors de la planification de leurs projets de migration.

* **Problèmes de compatibilité**. DMA identifie également les problèmes de compatibilité liés aux domaines suivants:

  * Modifications avec rupture:  Objets de schéma spécifiques qui peuvent interrompre la fonctionnalité de migration vers la base de données cible.  Nous vous recommandons de corriger ces objets de schéma après la migration de la base de données.
  * Changements de comportement: Les objets de schéma signalés peuvent continuer à fonctionner, mais ils peuvent présenter un comportement différent, par exemple une dégradation des performances.
  * Problèmes d’information:  Ces objets n’ont pas d’impact sur la migration, mais peuvent avoir été dépréciés des versions SQL Server.

Une fois l’évaluation terminée, utilisez notre [Azure Database Migration Service](https://azure.microsoft.com/services/database-migration/) (DMS) pour effectuer la migration de vos bases de données SQL Server vers Azure SQL Database Managed instance.  DMS prend en charge les migrations de base de données [hors connexion](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance) (ponctuelles) et [en ligne](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online) (temps d’arrêt minimal) vers Azure SQL Database Managed instance.

## <a name="dma-v40"></a>DMA v 4.0

La version v 4.0 de DMA présente la fonctionnalité de recommandations relatives aux références SKU Azure SQL Database, qui permet aux utilisateurs d’identifier la référence SKU Azure SQL Database minimale recommandée en fonction des compteurs de performances collectés sur le ou les ordinateurs hébergeant vos bases de données. Cette fonctionnalité fournit des recommandations relatives au niveau tarifaire, au niveau de calcul et à la taille maximale des données, ainsi qu’au coût estimé par mois. Il offre également la possibilité d’approvisionner toutes vos bases de données dans Azure en bloc.

> [!NOTE]
> Cette fonctionnalité n’est actuellement disponible qu’à l’aide de l’interface de ligne de commande (CLI).

Pour plus d’informations, consultez l’article [identifier la référence SKU Azure SQL Database appropriée pour votre base de données locale](dma-sku-recommend-sql-db.md).

## <a name="dma-v36"></a>DMA v 3.6

La version v 3.6 de DMA introduit la «correction automatique» pour les objets de schéma affectés par les bloqueurs de migration les plus courants.

Cette version fournit un réglage automatique pour les problèmes de blocage de migration et de changement de comportement suivants:

* Objets de schéma qui utilisent la syntaxe de jointure non qualifiée.
* Objets de schéma qui utilisent l’instruction RAISEERROR héritée.
* Instructions SQL qui utilisent un littéral d’entier order by.

DMA effectue une conversion de schéma automatique pour les objets affectés par les problèmes listés et invite l’utilisateur à confirmer avant de procéder à la conversion du schéma. Les utilisateurs peuvent passer en revue les modifications de code suggérées, puis accepter ou refuser toutes les conversions pour un objet de base de données donné.

DMA utilise la technologie de synthèse de programmes Microsoft (PROSEWARE) pour suggérer les correctifs de code. En savoir plus sur le [proseware](https://microsoft.github.io/prose/).

## <a name="dma-v35"></a>DMA v 3.5

La version v 3.5 de DMA comprend les ajouts suivants:

* Des améliorations significatives en matière de performances pour la migration vers Azure SQL Database (tests d’évaluation indiquent que le processus est quatre fois plus rapide qu’avec les versions antérieures de DMA).
* L’encombrement mémoire est optimisé pour améliorer la stabilité du flux de travail de migration.
* La possibilité d’ignorer les évaluations pendant les migrations de schéma et de données (si vous avez déjà effectué l’évaluation et résolu les objets de schéma de rupture avant la migration).
* Correctif permettant de résoudre un problème avec l’outil qui se bloque lorsqu’un chemin de partage réseau non valide est fourni pour les fichiers de sauvegarde, lorsque vous effectuez une mise à niveau d’une version héritée de SQL Server sur site vers une version ultérieure ou SQL Server sur des machines virtuelles Azure.

## <a name="dma-v34"></a>DMA v 3.4

La version 3.4 de DMA comprend les ajouts suivants:

* La prise en charge de SQL Server 2017 comme source pour les migrations vers Azure SQL Database.
* Améliorations de la stabilité, des performances et de l’exactitude des règles d’évaluation.

## <a name="dma-v33"></a>DMA v 3.3

La version 3.3 de DMA permet la migration d’une instance de SQL Server locale vers la nouvelle version de SQL Server 2017, sur Windows et Linux. Tandis que le flux de travail global de migration pour Windows et Linux est le même, le passage à SQL Server 2017 pour Linux nécessite quelques considérations supplémentaires.

### <a name="specifying-the-back-up-path"></a>Spécification du chemin de sauvegarde

Linux et Windows utilisent des formats de chemin d’accès différents. Par conséquent, la migration vers SQL Server 2017 sur Linux nécessite que l’utilisateur fournisse à la fois les versions Windows et Linux du chemin d’accès à l’emplacement du fichier physique. Vous pouvez fournir les deux versions du chemin d’accès de différentes façons en fonction de l’emplacement du fichier physique.
Si le fichier de sauvegarde physique se trouve sur un ordinateur exécutant:

* Linux, utilisez un partage «samba» pour partager le fichier avec d’autres ordinateurs sur le réseau.
* Windows, utilisez la commande «mnt» pour monter le partage sur l’ordinateur exécutant Linux.

> [!NOTE]
> Les détails de l’utilisation d’un partage «samba» ou de la commande «mnt» n’entrent pas dans le cadre de cet article.

### <a name="migrating-windows-logins"></a>Migration des connexions Windows

Tandis que la migration des connexions Active Directory (AD) est officiellement prise en charge par SQL Server 2017 sur Linux, elle nécessite une configuration supplémentaire pour fonctionner correctement. Reportez-vous à l’article [Active Directory l’authentification avec SQL Server sur Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-authentication) pour obtenir des informations détaillées sur la configuration des connexions Active Directory sur SQL Server 2017 sur Linux. Après avoir effectué la configuration requise, l’installation est terminée et vous pouvez migrer Active Directory connexions comme d’habitude. L’authentification SQL standard fonctionne comme prévu sans aucune configuration supplémentaire.

## <a name="dma-v32"></a>DMA v 3.2

La version v 3.2 de DMA comprend les ajouts suivants:

* La migration des schémas et des données est activée à partir des bases de données SQL Server locales pour Azure SQL Database avec un nouveau flux de travail de migration.
* Lors de la migration de schéma vers Azure SQL Database, DMA scripte vos objets de base de données source, fournit des conseils sur la façon de résoudre les éventuels problèmes de compatibilité, puis déploie votre schéma sur Azure.

## <a name="dma-v31"></a>DMA v 3.1

La version v 3.1 de DMA comprend les ajouts suivants:

* Recommandations d’évaluation améliorées pour les bases de données SQL Azure en termes de classements de bases de données, d’utilisation de procédures stockées système non prises en charge et d’objets CLR.
* Guide d’évaluation des niveaux de compatibilité 130, 120, 110 et 100 lors de la migration vers des bases de données SQL Azure.

## <a name="dma-v30"></a>DMA v 3.0

La version 3.0 de DMA étend l’évaluation d’Azure SQL Database afin de fournir des recommandations complètes pour vous aider à résoudre les problèmes liés à:

* Problèmes de blocage de la migration.
* Fonctionnalités et fonctions partiellement ou non prises en charge.

## <a name="dma-v21"></a>DMA v 2.1

La version v 2.1 de DMA comprend les ajouts suivants:

* Prise en charge de la ligne de commande pour l’exécution des évaluations en mode sans assistance, ce qui permet d’exécuter des évaluations à l’échelle. Pour plus d’informations, reportez-vous à l’article [exécuter Assistant Migration de données à partir de la ligne de commande](dma-commandline.md).
* Amélioration des performances lorsque les utilisateurs lancent et ferment DMA.
* La possibilité de configurer le délai d’expiration de la connexion SQL. Pour plus d’informations, reportez-vous à l’article [paramètres de configuration pour Assistant Migration de données](dma-configurationsettings.md).

## <a name="dma-v20"></a>DMA v 2.0

La version v 2.0 de DMA comprend des recommandations de fonctionnalités Stretch Database améliorées pour fournir des tables prioritaires appropriées qui optimisent les économies de stockage.

## <a name="dma-v10"></a>DMA v 1.0

La version v 1.0 de DMA est la version initiale, et elle fournit pour:

* Détection des problèmes qui peuvent affecter une mise à niveau vers une version locale de SQL Server. Toutes les découvertes sont décrites comme des problèmes de compatibilité et sont classées dans les domaines suivants:
  * Modifications avec rupture
  * Changements de comportement
  * Fonctionnalités dépréciées
* Découverte de nouvelles fonctionnalités de la plateforme de SQL Server cible dont la base de données peut bénéficier après une mise à niveau. Toutes les découvertes sont décrites comme des recommandations relatives aux fonctionnalités et sont classées dans les domaines suivants:
  * Performances
  * Sécurité
  * Stockage
* Expérience utilisateur moderne pour effectuer des évaluations.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Assistant Migration de données](../dma/dma-overview.md)
