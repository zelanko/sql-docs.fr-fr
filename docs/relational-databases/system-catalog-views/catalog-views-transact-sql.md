---
title: Affichages catalogue (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sql13.SysViewExpandPortal.f1
dev_langs:
- TSQL
helpviewer_keywords:
- catalog metadata [SQL Server]
- system views [SQL Server], catalog
- metadata [SQL Server], views
- catalogs [SQL Server], metadata
- catalog views [SQL Server]
- Database Engine [SQL Server], metadata
- catalog views [SQL Server], about catalog views
ms.assetid: 13bccc2f-ed3c-4b58-abd0-ca8bf34a66b8
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9532ee19ec8489caa51d090feaff464e030a0da0
ms.sourcegitcommit: c70a0e2c053c2583311fcfede6ab5f25df364de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68670558"
---
# <a name="system-catalog-views-transact-sql"></a>Affichages catalogue système (Transact-SQL)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Les affichages catalogue retournent des informations utilisées par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Il est conseillé d'utiliser les affichages catalogue puisqu'ils représentent l'interface la plus générale vers les métadonnées de catalogue et le moyen le plus efficace pour obtenir, transformer et présenter des formulaires personnalisés de ces informations. Toutes les métadonnées de catalogue accessibles à l'utilisateur sont exposées dans des affichages catalogue.

> [!NOTE]
> Les affichages catalogue ne contiennent pas d'informations sur la réplication, la sauvegarde, le plan de maintenance de base de données ou les données de catalogue de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

 Certains affichages de catalogue héritent de lignes d'autres affichages catalogue. Par exemple, l’affichage catalogue [sys. tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) hérite de l’affichage catalogue [sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) . L'affichage catalogue sys.objects est appelé affichage de base, et l'affichage sys.tables est appelé affichage dérivé. L'affichage catalogue sys.tables retourne les colonnes qui sont spécifiques aux tables, ainsi que toutes les colonnes retournées par l'affichage catalogue sys.objects. L'affichage catalogue sys.objects retourne des lignes pour les objets autres que les tables, notamment les procédures stockées et les vues. Lorsqu'une table est créée, les métadonnées de la table sont retournées dans les deux affichages. Bien que les deux affichages catalogue retournent différents niveaux d'informations concernant la table, il n'existe qu'une seule entrée dans les métadonnées de cette table, avec un nom et un object_id. Cela peut être résumé comme suit :

- L'affichage de base contient un sous-ensemble de colonnes et un sur-ensemble de lignes.
- L'affichage dérivé contient un sur-ensemble de colonnes et un sous-ensemble de lignes.

> [!IMPORTANT]
> Dans les versions ultérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[msCoName](../../includes/msconame-md.md)] peut augmenter la définition de l'affichage catalogue système en ajoutant des colonnes à la fin de la liste des colonnes. Nous vous recommandons d’utiliser la syntaxe \* Select from *sys. catalog_view_name* dans le code de production, car le nombre de colonnes retournées peut changer et rompre votre application.

Les affichages catalogue de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont classés en plusieurs catégories :

|||
|-|-|
|[Affichages &#40;catalogue de groupes de disponibilité Always on Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)|[Messages &#40;pour les&#41; affichages &#40;catalogue des erreurs&#41;Transact-SQL](../system-catalog-views/messages-for-errors-catalog-views-sys-messages.md))|
|[Affichages catalogue Azure SQL Database](../../relational-databases/system-catalog-views/azure-sql-database-catalog-views.md)|[Affichages &#40;catalogue d’objets Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)|
|[Change Tracking les affichages &#40;catalogue Transact-SQL&#41;](../system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases.md)|[Affichages &#40;catalogue des fonctions de partition Transact-SQL&#41;](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)|
|[Affichages &#40;catalogue de l’assembly CLR Transact-SQL&#41;](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)|[Vues de la Gestion basée sur des stratégies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)|
|[Vues &#40;du collecteur de données Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)|[Resource Governor les affichages &#40;catalogue Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)|
|[Data Spaces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)|[Affichages catalogue du magasin de requêtes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)|
|[Database Mail les &#40;vues Transact-SQL&#41;](../../relational-databases/system-catalog-views/database-mail-views-transact-sql.md)|[Affichages &#40;catalogue de types scalaires Transact-SQL&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)|
|[Affichages &#40;catalogue de la mise en miroir de bases de données Transact-SQL&#41;](../system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)|[Affichages &#40;catalogue de schémas Transact-SQL&#41;](../system-catalog-views/schemas-catalog-views-sys-schemas.md)|
|[Affichages &#40;catalogue de bases de données et de fichiers Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)|[Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)|
|[Affichages &#40;catalogue des points de terminaison Transact-SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)|[Affichages catalogue relatifs à Service Broker &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/service-broker-catalog-views-transact-sql.md)|
|[Affichages catalogue des événements étendus &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)|[Affichages &#40;catalogue de configurations à l’ensemble du serveur Transact-SQL&#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)|
|[Vues de catalogue des propriétés étendues &#40;Transact-SQL&#41;](../system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md)|[Vues de Data Catalog spatiales](../../relational-databases/system-catalog-views/spatial-data-catalog-views.md)|
|[Affichages &#40;catalogue des opérations externes Transact-SQL&#41;](../../relational-databases/system-catalog-views/external-operations-catalog-views-transact-sql.md)|[Affichages catalogue de la SQL Data Warehouse et des Data Warehouse parallèles](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)|
|[Les affichages &#40;catalogue FileStream et filetable Transact-SQL&#41;](../../relational-databases/system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)|[Stretch Database les affichages &#40;catalogue Transact-SQL&#41;](../system-catalog-views/stretch-database-catalog-views-sys-remote-data-archive-databases.md)|
|[Affichages &#40;catalogue de recherche en texte intégral et de recherche sémantique Transact-SQL&#41;](../../relational-databases/system-catalog-views/full-text-search-and-semantic-search-catalog-views-transact-sql.md)|[Types &#40;XML de schémas XML affichages&#41; &#40;catalogue système Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)|
|[Affichages &#40;catalogue des serveurs liés, Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)||

## <a name="see-also"></a>Voir aussi

- [Vues &#40;de schémas d’informations Transact-SQL&#41;](../../relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)
- [Tables système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)
- [Questions fréquentes (FAQ) sur l’interrogation des catalogues système SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)
