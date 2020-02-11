---
title: Chargement des données
description: Vous pouvez charger ou insérer des données dans SQL Server Parallel Data Warehouse (PDW) à l’aide de Integration Services, de l’utilitaire bcp, de dwloader ou de l’instruction SQL INSERT.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: fd161820fd53d45642848697bce9589a98dec4ca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401040"
---
# <a name="loading-data-into-parallel-data-warehouse"></a>Chargement de données dans des Data Warehouse parallèles
Vous pouvez charger ou insérer des données dans SQL Server Parallel Data Warehouse (PDW) à l’aide de Integration Services, de l' [utilitaire bcp](../tools/bcp-utility.md), du chargeur de ligne de commande **dwloader** ou de l’instruction SQL INSERT.  

## <a name="loading-environment"></a>Chargement de l’environnement  
Pour charger des données, vous avez besoin d’un ou de plusieurs serveurs de chargement. Vous pouvez utiliser vos propres serveurs ETL existants ou d’autres serveurs, ou vous pouvez acheter de nouveaux serveurs. Pour plus d’informations, consultez [acquérir et configurer un serveur de chargement](acquire-and-configure-loading-server.md). Ces instructions incluent une [feuille de calcul de planification de la capacité du serveur de chargement](loading-server-capacity-planning-worksheet.md) pour vous aider à planifier la bonne solution pour le chargement.  
  
## <a name="load-with-dwloader"></a>Charger avec dwloader  
L’utilisation du [chargeur de ligne de commande dwloader](dwloader.md) est le moyen le plus rapide de charger des données dans PDW.  
  
![Chargement du processus](media/loading-process.png "Chargement du processus")  
  
dwloader charge les données directement sur les nœuds de calcul sans passer les données via le nœud de contrôle. Pour charger des données, dwloader communique tout d’abord avec le nœud de contrôle pour obtenir des informations de contact pour les nœuds de calcul. dwloader configure un canal de communication avec chaque nœud de calcul, puis envoie des blocs de données de 256 Ko aux nœuds de calcul de manière alternée.  
  
Sur chaque nœud de calcul, le service de déplacement des données (DMS) reçoit et traite les segments de données. Le traitement des données comprend la conversion de chaque ligne en SQL Server format natif et le calcul du hachage de distribution pour déterminer le nœud de calcul auquel chaque ligne appartient.  
  
Après le traitement des lignes, DMS utilise un déplacement aléatoire pour transférer chaque ligne vers le nœud de calcul et l’instance de SQL Server appropriés. Comme SQL Server reçoit les lignes, il les traite par lot en fonction du paramètre de taille de lot **-b** défini dans dwloader, puis charge en masse le lot.  

## <a name="load-with-prepared-statements"></a>Charger avec des instructions préparées

Vous pouvez utiliser des instructions préparées pour charger des données dans des tables distribuées et répliquées. Lorsque les données d’entrée ne correspondent pas au type de données cible, une conversion implicite est effectuée. Les conversions implicites prises en charge par les instructions préparées PDW sont un sous-ensemble des conversions prises en charge par SQL Server. Autrement dit, seul un sous-ensemble de conversions est pris en charge, mais les conversions prises en charge correspondent SQL Server conversions implicites. Même si la table cible à charger est définie comme une table distribuée ou répliquée, les conversions implicites sont appliquées (si nécessaire) à toutes les colonnes qui existent dans la table cible. 

<!-- MISSING LINK
For more information, see [Prepared statements](prepared-statements.md).
-->
  
## <a name="related-tasks"></a>Tâches associées  
  
|Tâche|Description|  
|--------|---------------|  
|Créez la base de données intermédiaire.|[Créer la base de données intermédiaire](staging-database.md)|  
|Chargez avec Integration Services.|[Charger avec Integration Services](load-with-ssis.md)|  
|Comprendre les conversions de type pour dwloader.|[Règles de conversion du type de données pour dwloader](dwloader-data-type-conversion-rules.md)|  
|Charger des données avec dwloader.|[Chargeur de ligne de commande dwloader](dwloader.md)|  
|Comprendre les conversions de type pour INSERT.|[Charger des données avec INSERT](load-with-insert.md)|  
 
<!-- MISSING LINKS
## See Also  
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Common metadata query examles](metadata-query-examples.md)  
  
-->
