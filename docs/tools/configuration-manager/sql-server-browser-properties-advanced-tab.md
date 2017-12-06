---
title: "Propriétés de serveur SQL Browser (onglet Avancé) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba79137a-cb72-4bf3-a650-e11d02cfce10
caps.latest.revision: "19"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 718dbda167f9293aa688ebbc0a7abcab340d64b2
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-browser-properties-advanced-tab"></a>Propriétés de SQL Server Browser (onglet Avancé)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] navigateur s’exécute en tant que service sur le serveur. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser est à l'écoute des demandes entrantes pour les ressources [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et fournit des informations sur les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l'ordinateur.  
  
## <a name="options"></a>Options  
 **Cluster**  
 Indique si ce service est installé en tant que ressource d'un serveur cluster.  
  
 **Commentaires client**  
 Indique si le contrôle SQM (Service Quality Monitoring) a été activé sur ce service. Pour plus d'informations sur Commentaires client, recherchez dans la documentation en ligne la rubrique « Paramètres des rapports d'erreurs et d'utilisation ».  
  
 **Répertoire de vidage**  
 Emplacement où sont placés les vidages de mémoire en cas d'erreur.  
  
 **Rapport d'erreurs**  
 Quand cette option a pour valeur **Oui**, le programme Dr. Watson transfère les informations à [!INCLUDE[msCoName](../../includes/msconame-md.md)] ou au serveur d'erreur en cas de problème sérieux. Pour plus d'informations sur les rapports d'erreurs, recherchez dans la documentation en ligne la rubrique « Paramètres des rapports d'erreurs et d'utilisation ».  
  
 **ID d'instance**  
 Indique l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui a utilisé cette instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. L’instance par défaut est **MSSQL10_50.MSSQLSERVER**.  
  
## <a name="see-also"></a>Voir aussi  
 [Service SQL Server Browser](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
