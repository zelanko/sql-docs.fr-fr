---
title: Sys.dm_db_xtp_merge_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: c1224e88-af74-4c99-ae32-d5d2c552a1f5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9fa5034f83f537afa3b7678b57637ffedada6680
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47630717"
---
# <a name="sysdmdbxtpmergerequests-transact-sql"></a>sys.dm_db_xtp_merge_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]


Suit les demandes de fusion de bases de données. La demande de fusion peut avoir été générée par SQL Server ou de la demande ont été apportée par un utilisateur avec [sys.sp_xtp_merge_checkpoint_files (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql.md).

> [!NOTE]
> Cette vue de gestion dynamique (DMV), sys.dm_db_xtp_merge_requests, existe jusqu'à ce que Microsoft SQL Server 2014.
> 
> Mais à partir de SQL Server 2016 cette DMV ne s’applique plus.

## <a name="columns-in-the-report"></a>Colonnes dans le rapport

| Nom de colonne | Type de données | Description |
| :-- | :-- | :-- |
| request_state | TINYINT | État de la demande de fusion :<br/>0 = demandé<br/>1 = en attente<br/>2 = installé<br/>3 = abandonné |
| request_state_desc | nvarchar(60) | Signification pour l’état actuel de la demande :<br/><br/>Une demande merge demandée - existe.<br/>En attente - la fusion est en cours de traitement.<br/>Installé - la fusion est terminée.<br/>Abandonné - la fusion n'a pas pu terminer, peut-être en raison d’une insuffisance de stockage. |
| destination_file_id | GUID | Identificateur unique du fichier de destination pour la fusion des fichiers sources. |
| lower_bound_tsn | BIGINT | Horodateur minimal pour le fichier de fusion cible. Horodateur de transaction le plus bas pour tous les fichiers sources à fusionner. |
| upper_bound_tsn | BIGINT | Horodateur maximal pour le fichier de fusion cible. Horodateur de transaction le plus haut pour tous les fichiers sources à fusionner. |
| collection_tsn | BIGINT | Horodateur auquel la ligne actuelle peut être collectée.<br/><br/>Une ligne dans l'état Installé est supprimée lorsque checkpoint_tsn est supérieur à collection_tsn.<br/><br/>Une ligne dans l'état Abandonné est supprimée lorsque checkpoint_tsn est inférieur à collection_tsn. |
| checkpoint_tsn | BIGINT | Heure de démarrage du point de contrôle.<br/><br/>Toutes les suppressions effectuées par des transactions avec un horodateur inférieur à celui-ci sont prises en compte pour le nouveau fichier de données. Les suppressions restantes sont déplacées dans le fichier delta cible. |
| sourcenumber_file_id | GUID | Jusqu'à 16 ID de fichier interne qui identifient de façon unique les fichiers sources dans la fusion. |

## <a name="permissions"></a>Permissions

Nécessite l'autorisation VIEW DATABASE STATE sur la base de données active.

## <a name="see-also"></a>Voir aussi

[Vues de gestion dynamique de Table mémoire optimisée (Transact-SQL)](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)


