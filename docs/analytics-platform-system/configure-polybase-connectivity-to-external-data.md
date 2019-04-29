---
title: Configurer la connectivité PolyBase - Analytique Platform System | Microsoft Docs
description: Explique comment configurer PolyBase dans Parallel Data Warehouse pour se connecter à Hadoop ou Microsoft Azure storage blob sources de données externes. Utilisez PolyBase pour exécuter des requêtes qui intègrent des données provenant de plusieurs sources, dont Hadoop, stockage blob Azure et Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: da6d71521f72ff23b4caf2f27dbc663dee684592
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63057807"
---
# <a name="what-is-polybase"></a>Qu’est-ce que PolyBase ?
PolyBase permet à votre Analytique Platform System (APS) pour traiter les requêtes Transact-SQL qui peuvent lire les données et écrire des données dans les sources de données externes. Les mêmes requêtes qui accèdent aux données externes peuvent également inclure des tables de relations dans vos points d’accès. Cela vous permet de combiner des données provenant de sources externes avec les données relationnelles de grande valeur dans vos bases de données de points d’accès.

![Logique de PolyBase](media/polybase/polybase-logical.png)

PolyBase sur les points d’accès prend en charge la lecture et écriture dans le système de fichiers Hadoop (HDFS) et le stockage d’objets Blob Azure. PolyBase a également la possibilité de déléguer les certains calculs pour les nœuds Hadoop en tant que travaux mapreduce pour optimiser les performances globales de la requête. PolyBase sur les points d’accès peut fonctionner sur texte délimité, ORC et Parquet de fichiers. Consultez [What ' s PolyBase](https://docs.microsoft.com/sql/relational-databases/polybase/polybase-guide) pour une description complète et de ses fonctionnalités.

> [!NOTE]
> Points d’accès actuellement prend uniquement en charge standard à usage général v1 localement redondant (LRS) le stockage Blob Azure.

## <a name="features-and-limitations"></a>Fonctionnalités et limitations
Consultez [fonctionnalités et limitations de](https://docs.microsoft.com/sql/relational-databases/polybase/polybase-versioned-feature-summary) pour un résumé de PolyBase fonctionnalités limitations connues et disponibles sur les points d’accès et d’autres produits de SQL Server.

> [!NOTE] 
> Le reste de PolyBase liés aux articles décrivent la configuration PolyBase sur APS 2016 (AU6) et versions ultérieures.

## <a name="see-also"></a>Voir aussi
- [Hadoop](polybase-configure-hadoop.md)
- [Stockage Blob Azure](polybase-configure-azure-blob-storage.md)
<!-- MISSING LINKS [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  -->  
  
