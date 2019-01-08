---
title: Filtrer des données publiées en vue de la réplication de fusion | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], filtering published data
- replication [SQL Server], filtering published data
ms.assetid: 46c5023d-7a3b-4455-becc-e159fcb5d6c4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 463a9385f4622f85cd1cbd5666517464be3cffd4
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52780841"
---
# <a name="filter-published-data-for-merge-replication"></a>Filtrer des données publiées en vue de la réplication de fusion
  Outre les filtres de lignes statiques et les filtres de colonnes que vous pouvez définir dans les autres types de réplications, la réplication de fusion vous offre des filtres de lignes paramétrés et des filtres de jointure. Pour plus d’informations sur les filtres de lignes statiques et les filtres de colonnes, consultez [Filtrer les données publiées](../publish/filter-published-data.md).  
  
 La réplication de fusion est utilisée dans de nombreuses applications qui prennent en charge les utilisateurs mobiles ; ces applications gèrent en général un grand nombre d'abonnements, chacun recevant un jeu de données spécifique. Les filtres paramétrés combinés aux filtres de jointure permettent à un administrateur de configurer une publication (ou tout au plus un petit nombre de publications) et néanmoins de fournir aux utilisateurs des jeux de données différents, ce qui réduit la charge de gestion que nécessiterait la création de nombreuses publications.  
  
-   Les filtres paramétrés permettent d'envoyer des partitions de données différentes à des Abonnés différents sans nécessiter la création de publications multiples. Par exemple, une table peut être filtrée de telle sorte que les données concernant un représentant donné ne soient répliquées que vers ce représentant. Les filtres paramétrés proposent diverses options qui vous permettent de personnaliser le filtrage afin d'optimiser les performances et de mieux répondre à vos besoins en matière de données et d'applications. Pour plus d'informations, voir [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).  
  
-   Les filtres de jointure sont en général associés aux filtres paramétrés pour étendre le filtrage aux tables connexes (ils peuvent aussi être associés aux filtres statiques). Par exemple, un représentant détient en général des données dans d'autres tables, comme les tables de clients et de commandes. Ces données peuvent être filtrées pour que ce représentant ne reçoive que les données relatives à ses clients et aux commandes de ses clients. Pour plus d’informations, voir [Join Filters](join-filters.md).  
  
 Aucun filtre ne doit inclure le `rowguidcol` utilisé par la réplication pour identifier les lignes. Par défaut, il s'agit de la colonne ajoutée lorsque vous avez configuré la réplication de fusion et qui a pour nom **rowguid**.  
  
## <a name="see-also"></a>Voir aussi  
 [Publier des données et des objets de base de données](../publish/publish-data-and-database-objects.md)  
  
  
