---
title: Fonctionnalités et limitations de PolyBase | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.technology: polybase
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8f7520a4e9bdc346113e4777bd6899f5ccc0e01c
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49460314"
---
# <a name="polybase-features-and-limitations"></a>Fonctionnalités et limitations de PolyBase

[!INCLUDE[appliesto-ss2016-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

Récapitulatif des fonctionnalités PolyBase disponibles pour les services et produits SQL Server.  
  
## <a name="feature-summary-for-product-releases"></a>Synthèse des fonctionnalités pour les versions du produit

Ce tableau récapitule les principales fonctionnalités de PolyBase et des produits dans lesquels elles sont disponibles.  
  
||||||
|-|-|-|-|-|   
|**Fonctionnalité**|**SQL Server 2016**|**Azure SQL Database**|**Azure SQL Data Warehouse**|**Parallel Data Warehouse**| 
|Interroger des données Hadoop avec [!INCLUDE[tsql](../../includes/tsql-md.md)]|oui|non|non|oui|
|Importer des données depuis Hadoop|oui|non|non|oui|
|Exporter des données vers Hadoop  |oui|non|non| oui|
|Interroger, importer, exporter vers HDInsights |non|non|non|non
|Transmettre des calculs de requête à Hadoop|oui|non|non|oui|  
|Importer des données depuis le stockage d’objets blob Azure|oui|non|oui|oui| 
|Exporter des données vers le stockage d’objets blob Azure|oui|non|oui|oui|  
|Importer des données depuis Azure Data Lake Store|non|non|oui|non|    
|Exporter des données depuis Azure Data Lake Store|non|non|oui|non|
|Exécuter des requêtes PolyBase à partir des outils décisionnels de Microsoft|oui|non|oui|oui|   

## <a name="pushdown-computation-supported-t-sql-operators"></a>Opérateurs T-SQL pris en charge pour la transmission des calculs

Dans SQL Server et APS, tous les opérateurs T-SQL ne peuvent pas être transmis au cluster hadoop. Le tableau ci-dessous répertorie tous les opérateurs pris en charge et une partie des opérateurs non pris en charge. 

||||
|-|-|-| 
|**Type d’opérateur**|**Transmissible à Hadoop**|**Transmissible au Stockage Blob**|
|Projections de colonne|oui|non|
|Prédicats|oui|non|
|Agrégats|partielles|non|
|Jointures entre les tables externes|non|non|
|Jointures entre les tables externes et les tables locales|non|non|
|Tris|non|non|

Une agrégation partielle signifie qu’une agrégation finale doit se produire une fois que les données atteignent SQL Server, mais qu’une partie de l’agrégation se produit dans Hadoop. Il s’agit d’une méthode courante de calcul des agrégations dans les systèmes à traitement parallèle massif.  

## <a name="known-limitations"></a>Limitations connues

PolyBase présente les limitations suivantes :

- La taille de ligne maximale, incluant la longueur totale des colonnes à longueur variable, ne peut pas dépasser 32 Ko dans SQL Server ou 1 Mo dans Azure SQL Data Warehouse.

- PolyBase ne prend pas en charge les types de données Hive 0.12+ (c’est-à-dire Char(), VarChar()).

- Durant l’exportation de données dans un format de fichier ORC à partir de SQL Server ou Azure SQL Data Warehouse, le nombre de colonnes de texte lourdes peut être limité à seulement 50, en raison d’erreurs de mémoire insuffisante Java. Pour contourner ce problème, exportez uniquement une partie des colonnes.

- Impossible de lire ou d’écrire des données chiffrées au repos dans Hadoop. Cela inclut le chiffrement transparent ou les zones chiffrées HDFS.

- PolyBase ne peut pas se connecter à une instance de Hortonworks si Knox est activé.

- Si vous utilisez des tables Hive avec transactional = true, PolyBase ne peut pas accéder aux données dans le répertoire de la table Hive.

<!--SQL Server 2016-->
::: moniker range="= sql-server-2016 || =sqlallproducts-allversions"

- [PolyBase ne s’installe pas quand vous ajoutez un nœud à un cluster de basculement SQL Server 2016](https://support.microsoft.com/en-us/help/3173087/fix-polybase-feature-doesn-t-install-when-you-add-a-node-to-a-sql-server-2016-failover-cluster)

::: moniker-end

- L’authentification intégrée n’est pas prise en charge. Seule l’authentification par nom d’utilisateur et mot de passe est prise en charge actuellement.  

- Le chiffrement est activé par défaut.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur PolyBase, consultez [Qu’est-ce que PolyBase ?](polybase-guide.md).
