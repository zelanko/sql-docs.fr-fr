---
title: Chargement des données dans Parallel Data Warehouse | Microsoft Docs
description: Vous pouvez charger ou insérer des données dans SQL Server Parallel Data Warehouse (PDW) à l’aide des Services d’intégration, utilitaire bcp, dwloader ou l’instruction SQL INSERT.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: b046839b7c4932b43230d28cc106db1e2ea5d5a7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960694"
---
# <a name="loading-data-into-parallel-data-warehouse"></a>Chargement des données dans Parallel Data Warehouse
Vous pouvez charger ou insérer des données dans SQL Server Parallel Data Warehouse (PDW) à l’aide des Services d’intégration, [utilitaire bcp](../tools/bcp-utility.md), **dwloader** du chargeur de ligne de commande ou l’instruction SQL INSERT.  

## <a name="loading-environment"></a>Chargement de l’environnement  
Pour charger des données, vous avez besoin d’un ou plusieurs serveurs de chargement. Vous pouvez utiliser votre propre ETL existant ou autres serveurs, ou vous pouvez acheter de nouveaux serveurs. Pour plus d’informations, consultez [obtenir et configurer un serveur de chargement](acquire-and-configure-loading-server.md). Ces instructions incluent un [le chargement des feuille de planification de capacité de serveur](loading-server-capacity-planning-worksheet.md) pour vous aider à planifier la solution adaptée pour le chargement.  
  
## <a name="load-with-dwloader"></a>Charger des données avec dwloader  
À l’aide de la [dwloader du chargeur de ligne de commande](dwloader.md) est le moyen le plus rapide pour charger des données dans PDW.  
  
![Processus de chargement](media/loading-process.png "processus de chargement")  
  
dwloader charge les données directement aux nœuds de calcul sans passer les données via le nœud de contrôle. Pour charger des données, dwloader communique en premier lieu avec le nœud de contrôle pour obtenir des informations de contact pour les nœuds de calcul. dwloader configure un canal de communication avec chaque nœud de calcul, puis envoie les segments de 256 Ko de données pour les nœuds de calcul de manière alternée.  
  
Sur chaque nœud de calcul, Service de déplacement des données (DMS) reçoit et traite les segments de données. Traitement des données inclut convertir chaque ligne de SQL Server au format natif et calculer le hachage de distribution pour déterminer le nœud de calcul auquel appartient chaque ligne.  
  
Après avoir traité les lignes, DMS utilise un déplacement aléatoire pour chaque ligne de transfert pour le nœud de calcul appropriées et l’instance de SQL Server. Comme SQL Server reçoit les lignes, il les met en correspondance en fonction de la **-b** paramètre de taille de lot défini dans dwloader et en bloc charge ensuite le lot.  

## <a name="load-with-prepared-statements"></a>Charger avec des instructions préparées

Vous pouvez utiliser des instructions préparées pour charger des données dans des tables répliquées et distribuées. Lorsque les données d’entrée ne correspondent pas le type de données cible, une conversion implicite est effectuée. Les conversions implicites pris en charge par PDW d’instructions préparées sont un sous-ensemble des conversions prises en charge par SQL Server. Autrement dit, uniquement un sous-ensemble de conversions sont prises en charge, mais les conversions prises en charge correspondent à des conversions implicites de SQL Server. Que la table cible à charger est défini comme une table répliquée ou distribuée, les conversions implicites sont appliquées (si nécessaire) pour toutes les colonnes qui existent dans la table cible. 

<!-- MISSING LINK
For more information, see [Prepared statements](prepared-statements.md).
-->
  
## <a name="related-tasks"></a>Tâches associées  
  
|Tâche|Description|  
|--------|---------------|  
|Créer la base de données intermédiaire.|[Créer la base de données intermédiaire](staging-database.md)|  
|Charger avec Integration Services.|[Charger avec Integration Services](load-with-ssis.md)|  
|Comprendre les conversions de types de dwloader.|[Règles de conversion du type de données pour dwloader](dwloader-data-type-conversion-rules.md)|  
|Charger des données avec dwloader.|[dwloader du chargeur de ligne de commande](dwloader.md)|  
|Comprendre les conversions de types de INSERT.|[Charger des données avec INSERT](load-with-insert.md)|  
 
<!-- MISSING LINKS
## See Also  
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Common metadata query examles](metadata-query-examples.md)  
  
-->
