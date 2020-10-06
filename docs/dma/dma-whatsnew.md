---
title: Nouveautés de Assistant Migration de données (SQL Server) | Microsoft Docs
description: Découvrez les nouvelles fonctionnalités de chaque version de Assistant Migration de données pour SQL Server et Azure SQL Database.
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, new features
ms.assetid: ''
author: rajeshsetlem
ms.author: rajpo
ms.openlocfilehash: 11bbf0a39ed9a9bbaa19992f98e4e23d50d6fbe9
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727758"
---
# <a name="whats-new-in-data-migration-assistant"></a>Nouveautés de Data Migration Assistant

Cet article répertorie les ajouts dans chaque version de Assistant Migration de données.

## <a name="data-migration-assistant-v-52"></a>Assistant Migration de données v 5,2
La version 5.2 du Assistant Migration de données prend en charge les éléments suivants :
- Le chargement des évaluations sur Azure Migrate avec la prise en charge des Azure Government et des clouds nationaux (offre souveraine).  Cette fonctionnalité permet d’évaluer la préparation de la migration de SQL Server données vers Azure SQL.
- La prise en charge de la ligne de commande pour le chargement des évaluations sur Azure Migrate avec la prise en charge de Azure Government et des clouds nationaux.  À présent, vous pouvez automatiser complètement le chargement des évaluations dans le projet Azure Migrate pour obtenir un rapport consolidé Azure SQL Readiness. 

## <a name="data-migration-assistant-v-50"></a>Assistant Migration de données v 5,0

La version v 5.0 du Assistant Migration de données prend en charge les éléments suivants :

- SQL Server 2019 pour Windows et SQL Server 2019 pour Linux en tant que cibles à des fins d’évaluation et de mise à niveau.
- Enregistrement et chargement des évaluations, y compris la prise en charge de l’enregistrement et du chargement des évaluations créées dans les versions antérieures du Assistant Migration de données.
- Évaluation des projets SQL Server Integration Services (SSIS) hébergés dans les packages SSISDB et SSIS hébergés dans le magasin de packages. La Assistant Migration de base de données détecte les fonctionnalités non prises en charge, partiellement prises en charge ou déconseillées et les problèmes de compatibilité utilisés dans les packages sources et fournit des recommandations pour vous aider à résoudre ces problèmes.
- Évaluation des requêtes SQL à partir d’une application externe, par exemple des requêtes SQL dans du code source C#. Les utilisateurs peuvent utiliser la boîte à outils de migration de l’accès aux données pour générer un rapport JSON complet pour les requêtes SQL utilisées dans le code source C#, puis charger le rapport dans Assistant Migration de données.

En outre, cette version de Assistant Migration de données fournit des améliorations et des correctifs de bogues supplémentaires, et l’outil a été mis à jour vers .net 4.7.2.

## <a name="data-migration-assistant-v45"></a>Assistant Migration de données v 4.5

La version 4.5 de Assistant Migration de données prend en charge l’évaluation des packages de migration SQL Server Integration Services (SSIS) hébergés dans le système de fichiers vers Azure SQL Database ou SQL Managed Instance.

## <a name="data-migration-assistant-v44"></a>Assistant Migration de données v 4.4

La version de Assistant Migration de données v 4.4 prend en charge le chargement des évaluations sur Azure Migrate.

## <a name="data-migration-assistant-v43"></a>Assistant Migration de données v 4.3

La version 4.3 de Assistant Migration de données prend en charge les éléments suivants :

- Recommandations relatives aux références SKU pour Azure SQL Managed Instance basées sur l’évaluation de la charge de travail.
- RDS SQL Server en tant que source pour les évaluations.
- Évaluations des travaux de l’agent pour Azure SQL Managed Instance en tant que cible.
- La possibilité d’ignorer certaines règles d’évaluation ; la liste des codes d’erreur spécifiée dans la propriété « ignoreErrorCodes » configurée dans DMA ne s’affiche pas dans les résultats de l’évaluation DMA.
- Évaluation des requêtes T-SQL dans les étapes de l’activité des travaux et indication des recommandations appropriées
- Évaluations des événements étendus (version préliminaire publique).

En outre, cette version de DMA offre des performances améliorées pour gérer un grand nombre d’objets de schéma dans les bases de données, ainsi que des correctifs de bogues liés à :

- Procédures compilées avec la compilation native, dans certains cas.
- Schémas de base de données complexes.

## <a name="data-migration-assistant-v42"></a>Assistant Migration de données v 4.2

La version 4.2 de Assistant Migration de données fournit une prise en charge de la ligne de commande pour l’évaluation de l’avancement cible d’une ou de plusieurs instances de serveur lors de la migration à partir d’une SQL Server locale vers une Managed Instance SQL. Les clients peuvent désormais utiliser la ligne de commande Assistant Migration de données pour collecter les métadonnées relatives à leur schéma de base de données, détecter les bloqueurs et en savoir plus sur les fonctionnalités partiellement prises en charge ou non prises en charge qui affectent la migration vers une Managed Instance SQL. Les résultats peuvent ensuite être rendus à l’aide du modèle de Power BI fourni.

## <a name="data-migration-assistant-v41"></a>Assistant Migration de données v 4.1

La version v 4.1 de Assistant Migration de données introduit la prise en charge de l’évaluation complète des bases de données SQL Server locales qui migrent vers SQL Managed Instance.

Le flux de travail d’évaluation vous aide à détecter les problèmes suivants, qui peuvent affecter votre migration vers SQL Managed Instance :

- **Fonctionnalités non prises en charge ou partiellement prises**en charge. Assistant Migration de données évalue votre base de données source SQL Server pour les fonctionnalités en cours d’utilisation qui sont partiellement prises en charge ou non prises en charge sur le Managed Instance SQL cible. L’outil fournit ensuite un ensemble complet de recommandations, d’approches alternatives disponibles dans Azure et d’atténuation des étapes afin que les clients puissent prendre en compte ces informations lors de la planification de leurs projets de migration.

- **Problèmes de compatibilité**. Assistant Migration de données identifie également les problèmes de compatibilité liés aux domaines suivants :

  - Dernières modifications : objets de schéma spécifiques qui peuvent perturber la migration de la fonctionnalité vers la base de données cible.  Nous vous recommandons de corriger ces objets de schéma après la migration de la base de données.
  - Changements de comportement : les objets de schéma signalés peuvent continuer à fonctionner, mais ils peuvent présenter un comportement différent, par exemple une dégradation des performances.
  - Problèmes d’information : ces objets n’ont pas d’impact sur la migration, mais peuvent avoir été dépréciés des versions SQL Server.

Une fois l’évaluation terminée, utilisez notre [Azure Database Migration Service](https://azure.microsoft.com/services/database-migration/) (DMS) pour effectuer la migration de vos bases de données SQL Server vers SQL Managed instance.  DMS prend en charge les migrations de base de données [hors connexion](/azure/dms/tutorial-sql-server-to-managed-instance) (ponctuelles) et [en ligne](/azure/dms/tutorial-sql-server-managed-instance-online) (temps d’arrêt minimal) vers SQL Managed instance.

## <a name="data-migration-assistant-v40"></a>Assistant Migration de données v 4.0

La version v 4.0 de Assistant Migration de données présente la fonctionnalité de recommandation Azure SQL Database SKU, qui permet aux utilisateurs d’identifier la référence SKU Azure SQL Database minimale recommandée en fonction des compteurs de performances collectés sur le ou les ordinateurs hébergeant vos bases de données. Cette fonctionnalité fournit des recommandations relatives au niveau tarifaire, au niveau de calcul et à la taille maximale des données, ainsi qu’au coût estimé par mois. Il offre également la possibilité d’approvisionner toutes vos bases de données dans Azure en bloc.

> [!NOTE]
> Cette fonctionnalité n’est actuellement disponible qu’à l’aide de l’interface de ligne de commande (CLI).

Pour plus d’informations, consultez l’article [identifier la référence SKU Azure SQL Database appropriée pour votre base de données locale](dma-sku-recommend-sql-db.md).

## <a name="data-migration-assistant-v36"></a>Assistant Migration de données v 3.6

La version 3.6 de Assistant Migration de données introduit la « correction automatique » pour les objets de schéma affectés par les bloqueurs de migration les plus courants.

Cette version fournit un réglage automatique pour les problèmes de blocage de migration et de changement de comportement suivants :

- Objets de schéma qui utilisent la syntaxe de jointure non qualifiée.
- Objets de schéma qui utilisent l’instruction RAISEERROR héritée.
- Instructions SQL qui utilisent un littéral d’entier order by.

Assistant Migration de données effectue une conversion automatique du schéma pour les objets affectés par les problèmes listés et invite l’utilisateur à confirmer l’exécution avant de procéder à la conversion du schéma. Les utilisateurs peuvent passer en revue les modifications de code suggérées, puis accepter ou refuser toutes les conversions pour un objet de base de données donné.

Assistant Migration de données utilise la technologie de synthèse de programmes Microsoft (PROSEWARE) pour suggérer les correctifs de code. En savoir plus sur le [proseware](https://microsoft.github.io/prose/).

## <a name="data-migration-assistant-v35"></a>Assistant Migration de données v 3.5

La version 3.5 de Assistant Migration de données comprend les ajouts suivants :

- Des améliorations significatives en matière de performances pour la migration vers Azure SQL Database (tests d’évaluation indiquent que le processus est quatre fois plus rapide qu’avec les versions antérieures de Assistant Migration de données).
- L’encombrement mémoire est optimisé pour améliorer la stabilité du flux de travail de migration.
- La possibilité d’ignorer les évaluations pendant les migrations de schéma et de données (si vous avez déjà effectué l’évaluation et résolu les objets de schéma de rupture avant la migration).
- Correctif permettant de résoudre un problème avec l’outil qui se bloque lorsqu’un chemin de partage réseau non valide est fourni pour les fichiers de sauvegarde, lorsque vous effectuez une mise à niveau d’une version héritée de SQL Server sur site vers une version ultérieure ou SQL Server sur des machines virtuelles Azure.

## <a name="data-migration-assistant-v34"></a>Assistant Migration de données v 3.4

La version 3.4 de Assistant Migration de données comprend les ajouts suivants :

- La prise en charge de SQL Server 2017 comme source pour les migrations vers Azure SQL Database.
- Améliorations de la stabilité, des performances et de l’exactitude des règles d’évaluation.

## <a name="data-migration-assistant-v33"></a>Assistant Migration de données v 3.3

La version 3.3 de Assistant Migration de données permet la migration d’une instance SQL Server locale vers la nouvelle version de SQL Server 2017, sur Windows et Linux. Tandis que le flux de travail global de migration pour Windows et Linux est le même, le passage à SQL Server 2017 pour Linux nécessite quelques considérations supplémentaires.

### <a name="specifying-the-back-up-path"></a>Spécification du chemin de sauvegarde

Linux et Windows utilisent des formats de chemin d’accès différents. Par conséquent, la migration vers SQL Server 2017 sur Linux nécessite que l’utilisateur fournisse à la fois les versions Windows et Linux du chemin d’accès à l’emplacement du fichier physique. Vous pouvez fournir les deux versions du chemin d’accès de différentes façons en fonction de l’emplacement du fichier physique.
Si le fichier de sauvegarde physique se trouve sur un ordinateur exécutant :

- Linux, utilisez un partage « samba » pour partager le fichier avec d’autres ordinateurs sur le réseau.
- Windows, utilisez la commande « mnt » pour monter le partage sur l’ordinateur exécutant Linux.

> [!NOTE]
> Les détails de l’utilisation d’un partage « samba » ou de la commande « mnt » n’entrent pas dans le cadre de cet article.

### <a name="migrating-windows-logins"></a>Migration des connexions Windows

Tandis que la migration des connexions Active Directory (AD) est officiellement prise en charge par SQL Server 2017 sur Linux, elle nécessite une configuration supplémentaire pour fonctionner correctement. Reportez-vous à l’article [Active Directory l’authentification avec SQL Server sur Linux](../linux/sql-server-linux-active-directory-authentication.md) pour obtenir des informations détaillées sur la configuration des connexions Active Directory sur SQL Server 2017 sur Linux. Après avoir effectué la configuration requise, l’installation est terminée et vous pouvez migrer Active Directory connexions comme d’habitude. L’authentification SQL standard fonctionne comme prévu sans aucune configuration supplémentaire.

## <a name="data-migration-assistant-v32"></a>Assistant Migration de données v 3.2

La version de Assistant Migration de données v 3.2 comprend les ajouts suivants :

- La migration des schémas et des données est activée à partir des bases de données SQL Server locales pour Azure SQL Database avec un nouveau flux de travail de migration.
- Lors de la migration de schéma vers Azure SQL Database, DMA scripte vos objets de base de données source, fournit des conseils sur la façon de résoudre les éventuels problèmes de compatibilité, puis déploie votre schéma sur Azure.

## <a name="data-migration-assistant-v31"></a>Assistant Migration de données v 3.1

La version v 3.1 de Assistant Migration de données comprend les ajouts suivants :

- Recommandations d’évaluation améliorées pour les Azure SQL Database en termes de classements de bases de données, d’utilisation de procédures stockées système non prises en charge et d’objets CLR.
- Guide d’évaluation des niveaux de compatibilité 130, 120, 110 et 100 lors de la migration vers Azure SQL Database.

## <a name="data-migration-assistant-v30"></a>Assistant Migration de données v 3.0

La version 3.0 de Assistant Migration de données étend l’évaluation de Azure SQL Database afin de fournir des recommandations complètes pour vous aider à résoudre les problèmes liés à :

- Problèmes de blocage de la migration.
- Fonctionnalités et fonctions partiellement ou non prises en charge.

## <a name="data-migration-assistant-v21"></a>Assistant Migration de données v 2.1

La version 2.1 de Assistant Migration de données comprend les ajouts suivants :

- Prise en charge de la ligne de commande pour l’exécution des évaluations en mode sans assistance, ce qui permet d’exécuter des évaluations à l’échelle. Pour plus d’informations, reportez-vous à l’article [exécuter Assistant Migration de données à partir de la ligne de commande](dma-commandline.md).
- Amélioration des performances lorsque les utilisateurs lancent et ferment DMA.
- La possibilité de configurer le délai d’expiration de la connexion SQL. Pour plus d’informations, reportez-vous à l’article [paramètres de configuration pour Assistant Migration de données](dma-configurationsettings.md).

## <a name="data-migration-assistant-v20"></a>Assistant Migration de données v 2.0

La version v 2.0 de Assistant Migration de données comprend des recommandations de fonctionnalités Stretch Database améliorées pour fournir des tables prioritaires appropriées qui optimisent les économies de stockage.

## <a name="data-migration-assistant-v10"></a>Assistant Migration de données v 1.0

La version v 1.0 de Assistant Migration de données est la version initiale, et elle fournit pour :

- Détection des problèmes qui peuvent affecter une mise à niveau vers une version locale de SQL Server. Toutes les découvertes sont décrites comme des problèmes de compatibilité et sont classées dans les domaines suivants :
  - Changements cassants
  - Changements de comportement
  - Fonctionnalités dépréciées
- Découverte de nouvelles fonctionnalités de la plateforme de SQL Server cible dont la base de données peut bénéficier après une mise à niveau. Toutes les découvertes sont décrites comme des recommandations relatives aux fonctionnalités et sont classées dans les domaines suivants :
  - Performances
  - Sécurité
  - Stockage
- Expérience utilisateur moderne pour effectuer des évaluations.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de l’Assistant Migration de données](../dma/dma-overview.md)