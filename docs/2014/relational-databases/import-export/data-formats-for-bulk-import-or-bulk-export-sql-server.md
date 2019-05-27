---
title: Formats de données pour l’importation en bloc ou l’exportation en bloc (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], choosing
- bulk importing [SQL Server], data formats
ms.assetid: 73fe6741-9437-4b26-b030-28b863e74399
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c43cb42cffba31f20b0e9717204f5475b5bb156d
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66012075"
---
# <a name="data-formats-for-bulk-import-or-bulk-export-sql-server"></a>Formats de données pour l'importation en bloc ou l'exportation en bloc (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut accepter des données dans un format caractère ou binaire natif. Utilisez le format caractère lorsque vous déplacez des données entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et une autre application (telle que [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel) ou un autre serveur de base de données (tel que Oracle ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Vous ne pouvez utiliser le format natif que lorsque vous transférez des données entre des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Dans cette rubrique :**  
  
-   [Formats de données pour l'importation ou l'exportation en bloc](#ComponentsAndConcepts)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="ComponentsAndConcepts"></a> Formats de données pour l'importation ou l'exportation en bloc  
 Le tableau suivant indique le format de données à utiliser en fonction de la représentation des données et de la source ou de la cible de l'opération.  
  
|Opération|Natif|Natif Unicode|Caractère|Caractère Unicode|  
|---------------|------------|--------------------|---------------|-----------------------|  
|Transferts en bloc de données entre plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide d'un fichier de données qui ne contient aucun caractère étendu ou codé sur deux octets (DBCS). Sauf si un fichier de format est utilisé, ces tables doivent être définies de façon identique.|Oui<sup>1</sup>|-|-|-|  
|Pour les colonnes `sql_variant`, il est préférable d'utiliser le format de données natif, car il conserve les métadonnées de chaque valeur `sql_variant`, à la différence des formats caractère ou Unicode.|Oui|-|-|-|  
|Transferts en bloc de données entre plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide d'un fichier de données qui contient des caractères étendus ou DBCS.|-|Oui|-|-|  
|Importation en bloc de données à partir d'un fichier texte généré par un autre programme.|-|-|Oui|-|  
|Exportation en bloc de données vers un fichier texte à utiliser dans un autre programme.|-|-|Oui|-|  
|Transferts en bloc de données entre plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide d'un fichier de données qui contient des données Unicode et qui ne comporte aucun caractère étendu ou DBCS.|-|-|-|Oui|  
  
 <sup>1</sup> méthode la plus rapide pour l’exportation en bloc de données à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lors de l’utilisation **bcp**.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Utiliser le format natif pour importer ou exporter des données &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Importer des données au format natif et caractère à partir de versions antérieures de SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Spécifier des formats de données pour la compatibilité lors de l’utilisation de bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)  
  
  
