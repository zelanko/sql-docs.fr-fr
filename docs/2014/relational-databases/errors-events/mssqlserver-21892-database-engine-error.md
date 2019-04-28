---
title: MSSQLSERVER_21892 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21892 (Database Engine error)
ms.assetid: 199818e8-28f4-440e-ad85-7bea88f51153
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 18916e8287841015727c37ed8833fbc29b1e6ba2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869146"
---
# <a name="mssqlserver21892"></a>MSSQLSERVER_21892
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|21892|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum21892|  
|Texte du message|Impossible d’interroger sys.availability_replicas sur le groupe de disponibilité principal associé au nom de réseau virtuel « %1!s! » pour les noms de serveur des réplicas membres : erreur = « %2!s! », message d’erreur = « %3!s! ».',|  
  
## <a name="explanation"></a>Explication  
 `sp_validate_replica_hosts_as_publishers` interroge le principal actuel du groupe de disponibilité associé au serveur de publication redirigé pour déterminer les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui hébergent les réplicas membres.  Lorsque cette requête échoue, l'erreur 21892 est retournée.  
  
 `sp_validate_replica_hosts_as_publishers` est généralement la première utilisation qui est faite du serveur lié temporaire, par conséquent, si des problèmes de connectivité sont présents, ils sont susceptibles d'apparaître d'abord avec `sp_validate_replica_hosts_as_publishers`. Contrairement à `sp_validate_redirected_publisher`, le serveur lié utilisé par `sp_validate_replica_hosts_as_publishers` utilise toujours les informations d'identification de l'appelant lors de la connexion à n'importe quel hôte de réplica de groupe de disponibilité.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Lorsque vous exécutez cette procédure stockée, assurez-vous que vous utilisez une connexion valide sur tous les réplicas. La connexion nécessite des autorisations suffisantes pour interroger les tables de métadonnées du groupe de disponibilité ainsi que les tables de métadonnées d'abonnement dans le réplica de base de données du serveur de publication.  
  
 Examinez l'erreur référencée d'origine pour déterminer la cause de l'échec et l'action corrective appropriée.  
  
  
