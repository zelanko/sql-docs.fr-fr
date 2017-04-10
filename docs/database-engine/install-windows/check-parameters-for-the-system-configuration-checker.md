---
title: "Param&#232;tres de l&#39;outil d&#39;analyse de configuration syst&#232;me | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installation de SQL Server, vérifications de la configuration système"
  - "échec des vérifications de la configuration système [SQL Server]"
  - "contrôle de la configuration avant l'installation"
  - "SCC [SQL Server]"
  - "outil d'analyse de configuration système"
  - "analyse de l'ordinateur avant l'installation [SQL Server]"
  - "vérification de la configuration avant l'installation"
  - "informations d’état [SQL Server], outil d’analyse de configuration système"
  - "paramètres [SQL Server], outil d’analyse de configuration système"
  - "outils d'analyse de la configuration [SQL Server]"
  - "programme d’installation [SQL Server], outil d’analyse de configuration système"
ms.assetid: 8e712c15-6bfa-4d71-b303-9526101e5594
caps.latest.revision: 46
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 46
---
# Param&#232;tres de l&#39;outil d&#39;analyse de configuration syst&#232;me
  Lors de l'exécution du programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'outil d'analyse de configuration système (SCC) analyse l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sera installé. L'outil SCC recherche toute anomalie susceptible d'empêcher une installation correcte de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Avant que le programme d'installation ne démarre l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le SCC extrait l'état de chaque élément. Puis, il compare le résultat avec les conditions requises et fournit une aide pour la suppression des problèmes importants.  
  
 L'Outil d'analyse de configuration système génère un rapport qui contient une brève description de chaque règle exécutée et de l'état d'exécution. Le rapport d’analyse de configuration système se trouve à l’emplacement %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMJJ_HHMM>\\.  
  
## Voir aussi  
 [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)   
 [Considérations sur la sécurité pour une installation SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
 [Mises à niveau de la version et de l'édition prises en charge](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
  