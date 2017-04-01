---
title: "Se connecter &#224; SQL&#160;Server par le biais d&#39;un serveur proxy (Gestionnaire de configuration SQL&#160;Server) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Remote WinSock"
  - "RWS"
  - "LAT (table d'adresses locales)"
  - "serveurs proxy [SQL Server]"
  - "connexions [SQL Server], serveur proxy"
  - "Microsoft Proxy Server [SQL Server]"
  - "tables d'adresses locales [SQL Server]"
ms.assetid: 39714de0-2a1f-4179-9091-5c3fa4612545
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Se connecter &#224; SQL&#160;Server par le biais d&#39;un serveur proxy (Gestionnaire de configuration SQL&#160;Server)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette rubrique explique comment se connecter à SQL Server via un serveur proxy dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide du Gestionnaire de configuration SQL Server. Pour pouvoir écouter à distance au moyen de RWS (Remote WinSock), définissez la table d'adresses locales (LAT, Local Address Table) du serveur proxy pour que l'adresse du nœud à l'écoute se situe en dehors de la plage des entrées LAT.  
  
##  <a name="a-namessmsprocedurea-using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
  
#### <a name="to-enable-connections-to-sql-server-through-microsoft-proxy-server"></a>Pour autoriser les connexions à SQL Server via Microsoft Proxy Server  
  
1.  Suivez les étapes décrites dans [Configurer un serveur pour écouter un port TCP spécifique &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/configure a server to listen on a specific tcp port.md) pour déterminer quels ports TCP/IP sont utilisés par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ou pour configurer le [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour qu’il utilise le port de votre choix.  
  
2.  Dans votre serveur proxy, définissez la table d'adresses locales de ce serveur pour que l'adresse du nœud à l'écoute se situe en dehors de la plage des entrées de la table. Pour plus d'informations, consultez la documentation de votre serveur proxy.  
  
>  [!NOTE]
>  Cette rubrique s’applique à [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] en local. En cas de problèmes de connexion associés à [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], consultez [Résoudre des problèmes de connexion à la base de données SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-troubleshoot-common-connection-issues).  

