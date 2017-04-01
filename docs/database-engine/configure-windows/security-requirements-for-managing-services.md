---
title: "Sp&#233;cifications de s&#233;curit&#233; pour la gestion des services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service SQL Server Agent, sécurité"
  - "services [SQL Server], sécurité"
  - "services SQL Server, sécurité"
  - "fournisseurs WMI [SQL Server]"
  - "configuration du serveur [SQL Server]"
  - "sécurité SQL Server, services"
  - "services [SQL Server], WMI"
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Sp&#233;cifications de s&#233;curit&#233; pour la gestion des services
  Pour gérer les services [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, utilisez le Gestionnaire de configuration SQL Server ou [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour gérer les services sur des serveurs clusters, utilisez l'Administrateur de cluster.  
  
 Pour gérer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et définir les options de configuration du serveur, vous devez être membre du rôle serveur fixe **serveradmin** ou **sysadmin**. Les membres du groupe **Administrateurs** Windows peuvent démarrer et arrêter des services et configurer les options serveur fournies par Windows.  
  
> [!NOTE]  
>  Pour bien fonctionner, les comptes utilisés pour les services doivent être configurés correctement au niveau du domaine, du système de fichiers et des autorisations de Registre. Pour plus d’informations sur les autorisations requises, consultez [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## Windows Management Instrumentation  
 Le Gestionnaire de configuration SQL Server et [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] utilisent Windows Management Instrumentation pour afficher et modifier une partie des propriétés de serveur. Pour gérer les services et obtenir l'état des services, l'utilisateur doit posséder les droits nécessaires pour accéder à l'objet WMI. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], voici les pages de propriétés de serveur qui utilisent WMI :  
  
-   Démarrage automatique des services  
  
-   Paramètres de démarrage  
  
-   Sécurité  
  
-   Paramètres divers du serveur  
  
## Tâches associées  
 [Configurer WMI pour afficher l'état du serveur dans les outils SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
## Contenu connexe  
 [Fournisseur WMI pour les concepts de gestion de configuration](../Topic/WMI%20Provider%20for%20Configuration%20Management%20Concepts.md)  
  
  