---
title: Formats de données pour l’importation et l’exportation en bloc
description: SQL Server accepte les données au format caractère ou binaire natif. Utilisez le format caractère entre SQL Server et d’autres applications et le format natif entre des instances de SQL Server.
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], choosing
- bulk importing [SQL Server], data formats
ms.assetid: 73fe6741-9437-4b26-b030-28b863e74399
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.custom: seo-lt-2019
ms.openlocfilehash: a3d18d1e96bba94c1837df191389c11df23164a0
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009914"
---
# <a name="data-formats-for-bulk-import-or-bulk-export-sql-server"></a>Formats de données pour l’importation ou l’exportation en bloc (SQL Server)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut accepter des données dans un format caractère ou binaire natif. Utilisez le format caractère lorsque vous déplacez des données entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et une autre application (telle que [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel) ou un autre serveur de base de données (tel que Oracle ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Vous ne pouvez utiliser le format natif que lorsque vous transférez des données entre des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Dans cette rubrique :**  
  
-   [Formats de données pour l'importation ou l'exportation en bloc](#ComponentsAndConcepts)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="data-formats-for-bulk-import-or-export"></a><a name="ComponentsAndConcepts"></a> Formats de données pour l'importation ou l'exportation en bloc  
 Le tableau suivant indique le format de données à utiliser en fonction de la représentation des données et de la source ou de la cible de l'opération.  
  
|Opération|Natif|Natif Unicode|Caractère|Caractère Unicode|  
|---------------|------------|--------------------|---------------|-----------------------|  
|Transferts en bloc de données entre plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide d'un fichier de données qui ne contient aucun caractère étendu ou codé sur deux octets (DBCS). Sauf si un fichier de format est utilisé, ces tables doivent être définies de façon identique.|Oui*|-|-|-|  
|Pour les colonnes **sql_variant** , il est préférable d’utiliser le format de données natif, car il conserve les métadonnées de chaque valeur **sql_variant** , à la différence des formats caractère ou Unicode.|Oui|-|-|-|  
|Transferts en bloc de données entre plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide d'un fichier de données qui contient des caractères étendus ou DBCS.|-|Oui|-|-|  
|Importation en bloc de données à partir d'un fichier texte généré par un autre programme.|-|-|Oui|-|  
|Exportation en bloc de données vers un fichier texte à utiliser dans un autre programme.|-|-|Oui|-|  
|Transferts en bloc de données entre plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide d'un fichier de données qui contient des données Unicode et qui ne comporte aucun caractère étendu ou DBCS.|-|-|-|Oui|  
  
 \* Méthode la plus rapide pour l’exportation en bloc de données à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lors de l’utilisation de **bcp**.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
-   [Utiliser le format natif pour importer ou exporter des données &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Importer des données au format natif et caractère à partir de versions antérieures de SQL Server](../../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Spécifier des formats de données pour la compatibilité lors de l’utilisation de bcp &#40;SQL Server&#41;](../../relational-databases/import-export/specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)  
  
  
