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
ms.openlocfilehash: 197d485fe851298a8e8d365c9fd1a52bf1251101
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553455"
---
# <a name="mssqlserver_21871"></a>MSSQLSERVER_21871
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
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
  
  
