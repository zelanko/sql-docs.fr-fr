---
description: Fonctionnalités et limitations de PolyBase
title: Fonctionnalités et limitations de PolyBase | Microsoft Docs
descriptions: This article summarizes PolyBase features available for SQL Server products and services. It lists T-SQL operators supported for pushdown and known limitations.
ms.date: 11/13/2020
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: ''
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2afdc0e62fdd725584c464bda516fc6284d20f01
ms.sourcegitcommit: 3bd188e652102f3703812af53ba877cce94b44a9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97489989"
---
# <a name="polybase-features-and-limitations"></a>Fonctionnalités et limitations de PolyBase

[!INCLUDE[appliesto-ss2016-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

Cet article fournit une synthèse des fonctionnalités PolyBase disponibles pour les services et produits SQL Server.  
  
## <a name="feature-summary-for-product-releases"></a>Synthèse des fonctionnalités pour les versions du produit

Ce tableau contient les principales fonctionnalités de PolyBase et les produits dans lesquels elles sont disponibles.  

|**Fonctionnalité** |**SQL Server** (à compter de 2016) |**Azure SQL Database** |**Azure Synapse Analytics** |**Parallel Data Warehouse** |
|---------|---------|---------|---------|---------|
|Interroger des données Hadoop avec [!INCLUDE[tsql](../../includes/tsql-md.md)]|Oui|Non|Non|Oui|
|Importer des données depuis Hadoop|Oui|Non|Non|Oui|
|Exporter des données vers Hadoop  |Oui|Non|Non| Oui|
|Interroger, importer, exporter vers Azure HDInsights |Non|Non|Non|Non
|Transmettre des calculs de requête à Hadoop|Oui|Non|Non|Oui|  
|Importer des données à partir du stockage d’objets blob Azure|Oui|Oui<sup>*</sup>|Oui|Oui|
|Exporter des données vers le stockage d’objets blob Azure|Oui|Non|Oui|Oui|  
|Importer des données depuis Azure Data Lake Store|Non|Non|Oui|Non|
|Exporter des données vers Azure Data Lake Store|Non|Non|Oui|Non|
|Exécuter des requêtes PolyBase à partir des outils décisionnels Microsoft|Oui|Non|Oui|Oui|

<sup>*</sup> Introduite dans SQL Server 2017. Consultez [Exemples d’accès en bloc à des données dans le Stockage Blob Azure](../import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md).


## <a name="pushdown-computation-supported-by-t-sql-operators"></a>Transmission des calculs prise en charge par les opérateurs T-SQL

Dans SQL Server et APS, tous les opérateurs T-SQL ne peuvent pas être transmis au cluster Hadoop. Ce tableau contient tous les opérateurs pris en charge et un sous-ensemble des opérateurs non pris en charge.

|**Type d’opérateur** |**Transmissible à Hadoop** |**Transmissible au stockage d’objets blob** |
|---------|---------|---------|
|Projections de colonne|Oui|Non|
|Prédicats|Oui|Non|
|Agrégats|Partiel|Non|
|Jointures entre les tables externes|Non|Non|
|Jointures entre les tables externes et les tables locales|Non|Non|
|Tris|Non|Non|

L’agrégation partielle signifie qu’une agrégation finale doit se produire une fois que les données ont atteint SQL Server, mais qu’une partie de l’agrégation se produit dans Hadoop. Il s’agit d’une méthode courante de calcul des agrégations dans les systèmes à traitement parallèle massif.  

## <a name="known-limitations"></a>Limitations connues

PolyBase présente les limitations suivantes :

- Pour pouvoir utiliser PolyBase, vous devez disposer des autorisations de niveau serveur de contrôle ou sysadmin pour la base de données.

- La taille de ligne maximale, qui comprend la longueur totale des colonnes à longueur variable, ne peut pas dépasser 32 Ko dans SQL Server ou 1 Mo dans Azure Synapse Analytics.

- Quand des données sont exportées dans un format de fichier ORC à partir de SQL Server ou Azure Synapse Analytics, les colonnes comportant beaucoup de texte peuvent être limitées. Elles peuvent être limitées à 50 colonnes en raison des messages d’erreur de mémoire Java insuffisante. Pour contourner ce problème, exportez uniquement une partie des colonnes.

- PolyBase ne peut pas se connecter à une instance de Hortonworks si Knox est activé.

- Si vous utilisez des tables Hive avec transactional = true, PolyBase ne peut pas accéder aux données dans le répertoire de la table Hive.

<!--SQL Server 2016-->
::: moniker range="= sql-server-2016 "

- [PolyBase ne s’installe pas quand vous ajoutez un nœud à un cluster de basculement SQL Server 2016](https://support.microsoft.com/help/3173087/fix-polybase-feature-doesn-t-install-when-you-add-a-node-to-a-sql-server-2016-failover-cluster).

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur PolyBase, consultez [Qu’est-ce que PolyBase ?](polybase-guide.md).
