---
title: Catégorie d’événement d’Audit de sécurité | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Security Audit event category [SQL Server]
- event classes [Analysis Services], security audit
- security events [Analysis Services]
ms.assetid: 9686a495-68d7-4137-8e30-2655aa519f6c
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e4973e777105531b63fb5aacdae298e57f6f9e40
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="security-audit-event-category"></a>Catégorie d'événement Audit de sécurité
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  La catégorie d'événement Audit de sécurité contient les classes d'événements décrites dans le tableau ci-dessous.  
  
|Classe d'événements|ID d'événement|Description|  
|-----------------|--------------|-----------------|  
|Audit Login|1|Enregistre tous les événements de connexion depuis le début de la trace, tels qu’une demande de connexion d’un client à un serveur qui exécute une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|Audit Logout|2|Enregistre tous les nouveaux événements de déconnexion depuis le début de la trace, tels que l'émission par un client d'une commande de déconnexion.|  
|Audit Server Starts And Stops|4|Enregistre l'arrêt, le début et la suspension des activités des services.|  
|Audit Object Permission Event|18|Enregistre toutes les modifications d'autorisations sur les objets.|  
|Audit Admin Operations Event|19|Enregistre des opérations de serveur pour la sauvegarde, la restauration, la synchronisation, l'attachement, le détachement, ainsi que pour le chargement et la sauvegarde d'images.|  
  
 Pour plus d’informations sur les colonnes associées à chaque classe d’événements Security Audit, consultez [Colonnes de données Audit de sécurité](../../analysis-services/trace-events/security-audit-data-columns.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de Trace Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
