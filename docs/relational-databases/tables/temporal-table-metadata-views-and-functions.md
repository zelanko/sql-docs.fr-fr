---
description: Vues et fonctions de métadonnées de table temporelle
title: Vues et fonctions de métadonnées de table temporelle | Microsoft Docs
ms.custom: ''
ms.date: 03/28/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: e5d23ec9-7d18-40f6-add4-bea13132d0b9
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2d71f195f6432a5d27598d7861526f2a6475307c
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89537830"
---
# <a name="temporal-table-metadata-views-and-functions"></a>Vues et fonctions de métadonnées de table temporelle


[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]


[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] incluent un certain nombre de vues et de fonctions de métadonnées qui permettent aux administrateurs de récupérer des informations sur les tables temporelles.

Les informations sur les tables temporelles sont exposées dans les vues de métadonnées suivantes :

- [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)
- [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)
- [sys.periods &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-periods-transact-sql.md)

 Les informations sur les tables temporelles sont exposées dans les fonctions de métadonnées suivantes :

- [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)

- [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/objectpropertyex-transact-sql.md)

- [COLUMNPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/columnproperty-transact-sql.md)

## <a name="next-steps"></a>Étapes suivantes

- [Tables temporelles](../../relational-databases/tables/temporal-tables.md)
- [Prise en main des tables temporelles avec versions gérées par le système](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)
- [Vérifications de cohérence système des tables temporelles](../../relational-databases/tables/temporal-table-system-consistency-checks.md)
- [Partitionnement des tables temporelles](../../relational-databases/tables/partitioning-with-temporal-tables.md)
- [Considérations et limitations liées aux tables temporelles](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)
- [Sécurité de la table temporelle](../../relational-databases/tables/temporal-table-security.md)
- [Gérer la rétention des données d’historique dans les tables temporelles avec contrôle de version par le système](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)
- [Tables temporelles avec version gérée par le système avec tables à mémoire optimisée](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)
