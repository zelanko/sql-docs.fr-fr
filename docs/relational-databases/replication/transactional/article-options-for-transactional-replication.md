---
description: Options d'articles pour la réplication transactionnelle
title: Options d’articles pour la réplication transactionnelle | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 085f991a1adc9a19c5d308ccf1e522ef1f73143e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482290"
---
# <a name="article-options-for-transactional-replication"></a>Options d'articles pour la réplication transactionnelle
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  Il existe un certain nombre d'options pour les articles dans les publications transactionnelles. Avec la réplication transactionnelle, vous pouvez :  
  
-   Spécifier comment les changements sont propagés du serveur de publication vers les Abonnés. Pour plus d’informations, consultez [Spécifier le mode de propagation des modifications des articles transactionnels](../../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
-   Spécifier que l'exécution d'une procédure stockée doit être répliquée. Ceci est particulièrement utile lors de la réplication des résultats de procédures stockées de maintenance qui affectent de gros volumes de données. Pour plus d’informations, consultez [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Spécifier les options de schéma, par exemple si les contraintes et déclencheurs sont copiés sur l'Abonné. Pour plus d’informations, consultez [Spécifier des options de schéma](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
-   Utiliser des filtres de lignes et des filtres de colonnes. Le filtrage des articles d'une table vous permet de créer des partitions de données à publier. Pour plus d’informations, consultez [Filtrer des données publiées](../../../relational-databases/replication/publish/filter-published-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
