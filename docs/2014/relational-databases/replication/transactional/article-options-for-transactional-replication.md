---
title: Options d’articles pour la réplication transactionnelle | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1cc13a3d11e35ed47eac4ff401fb8b7cb607b32b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060306"
---
# <a name="article-options-for-transactional-replication"></a>Options d'articles pour la réplication transactionnelle
  Il existe un certain nombre d'options pour les articles dans les publications transactionnelles. Avec la réplication transactionnelle, vous pouvez :  
  
-   Spécifier comment les changements sont propagés du serveur de publication vers les Abonnés. Pour plus d’informations, consultez [Spécifier le mode de propagation des modifications des articles transactionnels](transactional-articles-specify-how-changes-are-propagated.md).  
  
-   Spécifier que l'exécution d'une procédure stockée doit être répliquée. Ceci est particulièrement utile lors de la réplication des résultats de procédures stockées de maintenance qui affectent de gros volumes de données. Pour plus d’informations, consultez [Publishing Stored Procedure Execution in Transactional Replication](publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Spécifier les options de schéma, par exemple si les contraintes et déclencheurs sont copiés sur l'Abonné. Pour plus d’informations, consultez [Spécifier des options de schéma](../publish/specify-schema-options.md).  
  
-   Utiliser des filtres de lignes et des filtres de colonnes. Le filtrage des articles d'une table vous permet de créer des partitions de données à publier. Pour plus d’informations, consultez [Filtrer des données publiées](../publish/filter-published-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Publier des données et des objets de base de données](../publish/publish-data-and-database-objects.md)  
  
  
