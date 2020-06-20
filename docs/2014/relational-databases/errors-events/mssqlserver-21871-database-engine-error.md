---
title: MSSQLSERVER_21871 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f26211da21829a0a898dfb36ff9fefd453c7ad44
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85034648"
---
# <a name="mssqlserver_21871"></a>MSSQLSERVER_21871
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|21871|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum21871|  
|Texte du message|Le serveur de publication %s de la base de données %s n'a pas été redirigé.|  
  
## <a name="explanation"></a>Explication  
 `sp_validate_replica_hosts_as_publishers` vérifie la table MSredirected_publishers dans la base de données de distribution pour les entrées du serveur de publication et de la base de données du serveur de publication identifiées.  `sp_validate_replica_hosts_as_publishers` retourne l'erreur 21871 lorsqu'aucune entrée n'est trouvée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 `sp_validate_replica_hosts_as_publishers` est uniquement applicable aux serveurs de publication redirigés. Si la base de données du serveur de publication est membre d'un groupe de disponibilité, utilisez la procédure stockée `sp_redirect_publisher` pour associer le serveur de publication et la base de données du serveur de publication au nom d'écouteur du groupe de disponibilité.  
  
  
