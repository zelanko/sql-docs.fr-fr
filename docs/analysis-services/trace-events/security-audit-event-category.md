---
title: "Cat&#233;gorie d&#39;&#233;v&#233;nement Audit de s&#233;curit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "catégorie d'événement Audit de sécurité [SQL Server]"
  - "classes d’événements [Analysis Services], audit de sécurité"
  - "événements sécurité [Analysis Services]"
ms.assetid: 9686a495-68d7-4137-8e30-2655aa519f6c
caps.latest.revision: 25
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 25
---
# Cat&#233;gorie d&#39;&#233;v&#233;nement Audit de s&#233;curit&#233;
  La catégorie d'événement Audit de sécurité contient les classes d'événements décrites dans le tableau ci-dessous.  
  
|Classe d'événements|ID d'événement|Description|  
|-----------------|--------------|-----------------|  
|Audit Login|1|Enregistre tous les événements de connexion depuis le début de la trace, tels qu’une demande de connexion d’un client à un serveur qui exécute une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|Audit Logout|2|Enregistre tous les nouveaux événements de déconnexion depuis le début de la trace, tels que l'émission par un client d'une commande de déconnexion.|  
|Audit Server Starts And Stops|4|Enregistre l'arrêt, le début et la suspension des activités des services.|  
|Audit Object Permission Event|18|Enregistre toutes les modifications d'autorisations sur les objets.|  
|Audit Admin Operations Event|19|Enregistre des opérations de serveur pour la sauvegarde, la restauration, la synchronisation, l'attachement, le détachement, ainsi que pour le chargement et la sauvegarde d'images.|  
  
 Pour plus d’informations sur les colonnes associées à chaque classe d’événements Security Audit, consultez [Colonnes de données Audit de sécurité](../../analysis-services/trace-events/security-audit-data-columns.md).  
  
## Voir aussi  
 [Événements de trace Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  