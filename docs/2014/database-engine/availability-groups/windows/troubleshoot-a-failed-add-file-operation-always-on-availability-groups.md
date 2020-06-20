---
title: Résoudre les problèmes liés à l’échec d’une opération d’ajout de fichier (groupes de disponibilité AlwaysOn) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary databases [SQL Server], Availability Groups
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 31ceaebf-864b-4dd0-9112-0d047b0316ad
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f44caf9a9968c35c8beeff9c218de6fb05f333a9
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936330"
---
# <a name="troubleshoot-a-failed-add-file-operation-alwayson-availability-groups"></a>Résoudre une opération d'ajout de fichier ayant échoué (groupes de disponibilité AlwaysOn)
  Pour certains déploiements de groupes de disponibilité AlwaysOn, les chemins d'accès aux fichiers varient entre le système qui héberge le réplica principal et les systèmes qui hébergent un réplica secondaire. Si le chemin d'accès aux fichiers d'une opération d'ajout de fichier n'existe pas sur le réplica secondaire, l'opération d'ajout de fichier réussit sur la base de données principale. Cependant, l'opération d'ajout e fichier entraîne l'interruption de la base de données secondaire. Par voie de conséquence, le réplica secondaire passe à l'état NOT SYNCHRONIZING.  
  
> [!NOTE]  
>  Nous recommandons, si possible, que le chemin d'accès au fichier (y compris la lettre de lecteur) d'une base de données secondaire donnée soit identique au chemin d'accès de la base de données primaire correspondante.  
  
## <a name="problem-resolution"></a>Résolution des problèmes  
 Pour résoudre ce problème, le propriétaire de la base de données doit effectuer les opérations suivantes :  
  
1.  Supprimer la base de données secondaire du groupe de disponibilité. Pour plus d’informations, consultez [Supprimer une base de données secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md).  
  
2.  Sur la base de données secondaire existante, restaurer une sauvegarde complète du groupe de fichiers contenant le fichier ajouté à la base de données secondaire à l'aide de WITH NORECOVERY et de WITH MOVE (en spécifiant le chemin d'accès au fichier sur l'instance de serveur qui héberge le réplica secondaire). Pour plus d’informations, consultez [Restaurer une base de données à un nouvel emplacement &#40;SQL Server&#41;](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md).  
  
3.  Sauvegarder le journal des transactions qui contient l'opération d'ajout de fichier sur la base de données primaire, puis restaurer manuellement la sauvegarde du journal sur la base de données secondaire à l'aide de WITH NORECOVERY et de WITH MOVE.  
  
4.  Préparer la base de données secondaire pour rejoindre le groupe de disponibilité, en restaurant, à l'aide de WITH NORECOVERY, toutes les autres sauvegardes de journal en attente de la base de données primaire.  
  
5.  Réintégrer la base de données secondaire au groupe de disponibilité. Pour plus d’informations, consultez [Joindre une base de données secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)   
 [Dépanner des utilisateurs orphelins &#40;SQL Server&#41;](../../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)   
 [Résoudre les problèmes de configuration de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;supprimé](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
