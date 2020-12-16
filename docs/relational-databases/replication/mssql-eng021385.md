---
description: MSSQL_ENG021385
title: MSSQL_ENG021385 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021385 error
ms.assetid: a2c0444f-d97b-4760-8905-3574791c2e26
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: 84cd64ba75f7a87fa7d4f93173d8b0537ddc7f93
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97469080"
---
# <a name="mssql_eng021385"></a>MSSQL_ENG021385
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Détails du message  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|21385|  
|Source de l’événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|L'instantané n'a pas réussi à traiter la publication '%1!'. L'incident peut être dû à une activité de changement de schéma actif ou à l'ajout de nouveaux articles.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur est générée si l'Agent d'instantané démarre au moment où des modifications de la base de données de publication sont en cours, par exemple l'ajout ou la suppression d'articles ou des modifications de schéma sur des objets publiés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Redémarrez l'Agent d'instantané au terme de la modification de la base de données de publication. Pour plus d’informations, consultez [Démarrer et arrêter un Agent de réplication &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) et [Concepts des exécutables de l’agent de réplication](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
