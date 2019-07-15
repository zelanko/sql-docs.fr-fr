---
title: Fonctionnalités et limitations de PolyBase | Microsoft Docs
ms.date: 09/24/2018
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: aboke
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e4a267e98b38ff294366ce198518ffdb3062d460
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67731953"
---
# <a name="polybase-features-and-limitations"></a>Fonctionnalités et limitations de PolyBase

[!INCLUDE[appliesto-ss2016-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

Cet article fournit une synthèse des fonctionnalités PolyBase disponibles pour les services et produits SQL Server.  
  
## <a name="feature-summary-for-product-releases"></a>Synthèse des fonctionnalités pour les versions du produit

Ce tableau contient les principales fonctionnalités de PolyBase et les produits dans lesquels elles sont disponibles.  
  
||||||
|-|-|-|-|-|   
|**Fonctionnalité**|**SQL Server 2016**|**Azure SQL Database**|**Azure SQL Data Warehouse**|**Parallel Data Warehouse**| 
|Interroger des données Hadoop avec [!INCLUDE[tsql](../../includes/tsql-md.md)]|Oui|Non|Non|Oui|
|Importer des données depuis Hadoop|Oui|Non|Non|Oui|
|Exporter des données vers Hadoop  |Oui|Non|Non| Oui|
|Interroger, importer, exporter vers Azure HDInsights |Non|Non|Non|Non
|Transmettre des calculs de requête à Hadoop|Oui|Non|Non|Oui|  
|Importer des données à partir du stockage d’objets blob Azure|Oui|Non|Oui|Oui| 
|Exporter des données vers le stockage d’objets blob Azure|Oui|Non|Oui|Oui|  
|Importer des données depuis Azure Data Lake Store|Non|Non|Oui|Non|    
|Exporter des données depuis Azure Data Lake Store|Non|Non|Oui|Non|
|Exécuter des requêtes PolyBase à partir des outils décisionnels Microsoft|Oui|Non|Oui|Oui|   

## <a name="pushdown-computation-supported-by-t-sql-operators"></a>Transmission des calculs prise en charge par les opérateurs T-SQL

Dans SQL Server et APS, tous les opérateurs T-SQL ne peuvent pas être transmis au cluster Hadoop. Ce tableau contient tous les opérateurs pris en charge et un sous-ensemble des opérateurs non pris en charge. 

||||
|-|-|-| 
|**Type d’opérateur**|**Transmissible à Hadoop**|**Transmissible au stockage d’objets blob**|
|Projections de colonne|Oui|Non|
|Prédicats|Oui|Non|
|Agrégats|Partielle|Non|
|Jointures entre les tables externes|Non|Non|
|Jointures entre les tables externes et les tables locales|Non|Non|
|Tris|Non|Non|

L’agrégation partielle signifie qu’une agrégation finale doit se produire une fois que les données ont atteint SQL Server, mais qu’une partie de l’agrégation se produit dans Hadoop. Il s’agit d’une méthode courante de calcul des agrégations dans les systèmes à traitement parallèle massif.  

## <a name="known-limitations"></a>Limitations connues

PolyBase présente les limitations suivantes :

- Pour pouvoir utiliser PolyBase, vous devez disposer des autorisations de niveau serveur de contrôle ou sysadmin pour la base de données.

- La taille de ligne maximale, qui comprend la longueur totale des colonnes à longueur variable, ne peut pas dépasser 32 Ko dans SQL Server ou 1 Mo dans Azure SQL Data Warehouse.

- Quand des données sont exportées dans un format de fichier ORC à partir de SQL Server ou SQL Data Warehouse, les colonnes comportant beaucoup de texte peuvent être limitées. Elles peuvent être limitées à 50 colonnes en raison des messages d’erreur de mémoire Java insuffisante. Pour contourner ce problème, exportez uniquement une partie des colonnes.

- PolyBase ne peut pas se connecter à une instance de Hortonworks si Knox est activé.

- Si vous utilisez des tables Hive avec transactional = true, PolyBase ne peut pas accéder aux données dans le répertoire de la table Hive.

<!--SQL Server 2016-->
::: moniker range="= sql-server-2016 || =sqlallproducts-allversions"

- [PolyBase ne s’installe pas quand vous ajoutez un nœud à un cluster de basculement SQL Server 2016](https://support.microsoft.com/help/3173087/fix-polybase-feature-doesn-t-install-when-you-add-a-node-to-a-sql-server-2016-failover-cluster).

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur PolyBase, consultez [Qu’est-ce que PolyBase ?](polybase-guide.md).
