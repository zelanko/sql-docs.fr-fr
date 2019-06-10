---
title: Quelles sont les nouveautés dans Data Migration Assistant (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2019
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
manager: jroth
ms.openlocfilehash: f88562c25982ce8c5d6c8d4b87dd629e4ba57c03
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794307"
---
# <a name="whats-new-in-data-migration-assistant"></a>Nouveautés de Data Migration Assistant
Cet article répertorie les ajouts dans chaque version de Data Migration Assistant (DMA).

## <a name="dma-v43"></a>DMA 4.3

La version 4.3 de DMA prend en charge :

* Recommandations de référence (SKU) pour Azure SQL Database managed instances basées sur l’évaluation de la charge de travail.
* Services Bureau à distance SQL Server en tant que source pour les évaluations.
* Évaluations de travail d’agent pour Azure SQL Database managed instance en tant que cible.
* La possibilité d’ignorer certaines règles d’évaluation ; la liste des codes d’erreur spécifiée dans la propriété « ignoreErrorCodes » configurée dans DMA n’apparaît pas dans les résultats d’évaluation DMA.
* Évaluation des requêtes T-SQL dans les étapes de travail l’activité et fournissant des recommandations appropriées
* Évaluation des événements étendus (version préliminaire publique).

En outre, cette version de DMA offre de meilleures performances pour gérer un grand nombre d’objets de schéma dans les bases de données, ainsi que des correctifs de bogues liés à :

* Procédures compilées avec la compilation native, dans certains cas.
* Schémas de base de données complexes.

## <a name="dma-v42"></a>DMA v4.2

La version de v4.2 de DMA fournit la prise en charge de la ligne de commande pour l’évaluation de la disponibilité cible pour une ou plusieurs instances de serveur lors de la migration à partir de local SQL Server vers Azure SQL Database managed instance. Les clients peuvent désormais utiliser la ligne de commande DMA pour collecter les métadonnées relatives à leur schéma de base de données, de détecter les blocages et découvrez les fonctionnalités partiellement prises en charge ou non pris en charge qui affectent la migration vers une instance gérée Azure SQL Database. Les résultats peuvent ensuite être restitués à l’aide du modèle de Power BI fourni.

## <a name="dma-v41"></a>DMA v4.1

La version 4.1 du DMA introduit la prise en charge pour une évaluation complète des bases de données SQL Server sur site migration vers Azure SQL Database Managed Instance.

Le flux de travail d’évaluation vous permet de détecter les problèmes suivants, ce qui peuvent affecter votre migration vers Azure SQL Database Managed Instance :

* **Non pris en charge ou partiellement prises en charge des fonctionnalités**. DMA évalue votre base de données SQL Server source pour les fonctionnalités qui sont partiellement pris en charge ou non pris en charge sur la cible Azure SQL Database Managed Instance en cours d’utilisation. L’outil fournit ensuite un ensemble complet de recommandations, d’approches alternatives disponibles dans Azure et d’atténuation des étapes afin que les clients peuvent prendre en compte ces informations lors de la planification de leurs projets de migration.

* **Problèmes de compatibilité**. DMA identifie également les problèmes de compatibilité liés aux domaines suivants :

  * Modifications avec rupture :  Les objets de schéma spécifique qui peuvent rompre la fonctionnalité de migration vers la base de données cible.  Nous recommandons de corriger ces objets de schéma après la migration de base de données.
  * Changements de comportement : Les objets de schéma signalées peuvent continuer à fonctionner, mais ils peuvent présenter un comportement différent, par exemple une dégradation des performances.
  * Problèmes d’information :  Ces objets sont sans incidence sur la migration, mais peuvent ont été déconseillés à partir de la fonctionnalité que SQL Server libère.

Une fois l’évaluation terminée, utilisez notre [Azure Database Migration Service](https://azure.microsoft.com/services/database-migration/) (DMS) pour effectuer la migration de vos bases de données SQL Server vers Azure SQL Database Managed Instance.  DMS prend en charge les deux [hors connexion](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance) (une fois) et [online](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online) migrations de base de données (-temps d’arrêt minimal) vers Azure SQL Database Managed Instance.

## <a name="dma-v40"></a>DMA v4.0

La version v4.0 de DMA présente la fonctionnalité de recommandations SKU de base de données SQL Azure, ce qui permet aux utilisateurs d’identifier le minimum recommandé SKU de base de données SQL Azure en fonction des compteurs de performances collectés à partir des ou les ordinateurs hébergeant vos bases de données. Cette fonctionnalité fournit des recommandations relatives à la tarification du niveau, de niveau de calcul et de taille maximale de données, ainsi que coût estimé par mois. Il offre également la possibilité de configurer toutes vos bases de données vers Azure en bloc.

> [!NOTE]
> Cette fonctionnalité est actuellement accessible uniquement via l’Interface de ligne de commande (CLI).

Pour plus d’informations, consultez l’article [identifier la référence SKU à base de données SQL Azure appropriée pour votre base de données locale](dma-sku-recommend-sql-db.md).

## <a name="dma-v36"></a>DMA v3.6

La version de la version 3.6 du DMA présente « Correction automatique » pour les objets de schéma qui sont affectés par les bloqueurs de migration courants.

Cette version offre de réglage automatique pour le bloqueur de migration suivants et le comportement change de problèmes :

* Les objets de schéma qui utilisent la syntaxe de jointure non qualifié.
* Les objets de schéma qui utilisent l’instruction RAISEERROR héritée.
* Instructions SQL qui utilisent la commande par entier littéral.

DMA effectue une conversion de schéma automatique pour les objets affectés par les problèmes répertoriés et invite l’utilisateur à confirmer l’opération avant de procéder à la conversion de schéma. Les utilisateurs peuvent examiner les modifications de code proposé puis accepter ou rejeter toutes les conversions de n’importe quel objet de base de données spécifique.

DMA utilise la technologie de synthèse de programme Microsoft (PROSE) pour suggérer des que correctifs du code. En savoir plus sur [PROSE](https://microsoft.github.io/prose/).

## <a name="dma-v35"></a>DMA v3.5

La version v3.5 de DMA inclut les ajouts suivants :

* Améliorations significatives des performances pour la migration vers Azure SQL Database (tests de performances indiquent que le processus est quatre fois plus rapide avec les versions antérieures de DMA).
* L’encombrement mémoire est davantage optimisé pour améliorer la stabilité du flux de travail de migration.
* La possibilité d’ignorer des évaluations pendant les migrations de schéma et les données (si vous avez déjà effectué l’évaluation et traité les objets de schéma avec rupture avant la migration).
* Un correctif pour résoudre un problème avec l’outil se bloque lorsqu’un chemin d’accès du partage réseau non valide est fournie pour les fichiers de sauvegarde lors de la mise à niveau d’une ancienne version de SQL Server locale vers une version ultérieure ou à SQL Server sur des machines virtuelles Azure.

## <a name="dma-v34"></a>Version 3.4 DMA

La version de la version 3.4 de DMA inclut les ajouts suivants :

* Prise en charge pour SQL Server 2017 en tant que source pour les migrations de base de données SQL Azure.
* Améliorations apportées à l’exactitude de règle de la stabilité, performances et l’évaluation.

## <a name="dma-v33"></a>Version 3.3 DMA

La version de la version 3.3 de DMA permet la migration d’une instance de SQL Server sur site vers la nouvelle version de SQL Server 2017 sur Windows et Linux. Si le workflow global de migration pour Windows et Linux est le même, la migration vers SQL Server 2017 pour Linux nécessite quelques considérations supplémentaires.

### <a name="specifying-the-back-up-path"></a>En spécifiant le chemin de sauvegarde

Linux et Windows utilisent des formats de chemin d’accès différent. Par conséquent, la migration vers SQL Server 2017 sur Linux nécessite que l’utilisateur fournissent des versions de Windows et de Linux du chemin vers l’emplacement du fichier physique. Vous pouvez fournir les deux versions du chemin d’accès de différentes manières selon l’emplacement du fichier physique.
Si le fichier de sauvegarde physique est sur un ordinateur exécutant :

* Linux, utilisez un « samba » partage pour partager le fichier avec d’autres ordinateurs sur le réseau.
* Windows, utilisez la commande « mnt » pour monter le partage sur l’ordinateur exécutant Linux.

> [!NOTE]
> Détails de l’utilisation d’un partage 'samba' ou la commande « mnt » sont dépasse le cadre de cet article.

### <a name="migrating-windows-logins"></a>Connexions Windows migration

Bien que la migration des connexions d’Active Directory (AD) est officiellement pris en charge par SQL Server 2017 sur Linux, il nécessite une configuration supplémentaire pour fonctionner correctement. Consultez l’article [l’authentification Active Directory avec SQL Server sur Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-authentication) pour plus d’informations sur la configuration des connexions Active Directory sur SQL Server 2017 sur Linux. Après avoir effectué la configuration requise, le programme d’installation est terminée et vous pouvez migrer les connexions Active Directory comme d’habitude. Authentification SQL standard fonctionne comme prévu, sans aucune installation supplémentaire.

## <a name="dma-v32"></a>DMA v3.2

La version de v3.2 de DMA inclut les ajouts suivants :

* Migration de schéma et les données sont activés à partir de bases de données SQL Server locale vers Azure SQL Database avec un nouveau flux de travail de migration.
* Pendant la migration de schéma pour la base de données SQL Azure, DMA scripts vos objets de base de données source, fournit des conseils sur la façon de résoudre les problèmes de compatibilité potentiels, puis déploie votre schéma vers Azure.

## <a name="dma-v31"></a>DMA v3.1

La version 3.1 de DMA inclut les ajouts suivants :

* Recommandations d’évaluation améliorée pour les bases de données SQL Azure en termes de classements de base de données, l’utilisation des procédures stockées du système non pris en charge et les objets CLR.
* Évaluation des conseils sur les niveaux de compatibilité 130, 120, 110 et 100 lorsque vous migrez vers les bases de données SQL Azure.

## <a name="dma-v30"></a>DMA v3.0

La version de la version 3.0 de DMA étend l’évaluation de la base de données SQL Azure pour fournir des recommandations complètes pour aider à résoudre les problèmes liés à :

* Problèmes de blocage de migration.
* Partiellement ou non pris en charge des fonctionnalités et fonctions.

## <a name="dma-v21"></a>DMA v2.1

La version de la version 2.1 de DMA inclut les ajouts suivants :

* Prise en charge de ligne de commande pour l’exécution des évaluations en mode sans assistance, ce qui facilite l’exécution des évaluations à l’échelle. Pour plus d’informations, consultez l’article [exécuter Data Migration Assistant à partir de la ligne de commande](dma-commandline.md).
* Améliorations des performances lorsque les utilisateurs de lancement et fermer le DMA.
* La possibilité de configurer le délai de connexion SQL. Pour plus d’informations, consultez l’article [paramètres de Configuration de Data Migration Assistant](dma-configurationsettings.md).

## <a name="dma-v20"></a>DMA v2.0

La version v2.0 de DMA inclut améliorées recommandations de fonctionnalités de la base de données Stretch pour fournir des tables hiérarchisées appropriées qui optimisent les économies de stockage.

## <a name="dma-v10"></a>DMA v1.0

La version v1.0 de DMA est la version initiale, et il fournit pour :

* Détection des problèmes qui peuvent affecter une mise à niveau vers une version locale de SQL Server. Les conclusions sont décrits comme des problèmes de compatibilité, et ils sont classés dans les domaines suivants :
  * Modifications avec rupture
  * Changements de comportement
  * Fonctionnalités dépréciées
* Découverte des nouvelles fonctionnalités de la plateforme SQL Server cible la base de données pouvant bénéficier du après une mise à niveau. Les conclusions sont décrites en tant que recommandation de fonctionnalité, et ils sont classés dans les domaines suivants :
  * Performances
  * Sécurité
  * Stockage
* Expérience utilisateur modernes pour effectuer des évaluations.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de l’Assistant Migration de données](../dma/dma-overview.md)
