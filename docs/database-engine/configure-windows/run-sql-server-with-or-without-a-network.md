---
title: "Ex&#233;cuter SQL Server avec ou sans r&#233;seau | Microsoft Docs"
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
  - "vérification du démarrage du service Server"
  - "net start [SQL Server]"
  - "invite de commandes [SQL Server], connexions"
  - "Services SQL Server, réseaux"
  - "informations d’état [SQL Server], service Server"
  - "exécution de SQL Server"
  - "mise en réseau [SQL Server], SQL Server, avec ou sans"
  - "services [SQL Server], réseaux"
  - "démarrage du service Server"
  - "SQL Server, exécution"
ms.assetid: 54eac961-5c7a-4481-982d-f93a64b5c2f4
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Ex&#233;cuter SQL Server avec ou sans r&#233;seau
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut s'exécuter sur un réseau ou fonctionner sans réseau.  
  
## Exécution de SQL Server sur un réseau  
 Pour permettre à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de communiquer en réseau, le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être en cours d'exécution. Par défaut, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows démarre automatiquement le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] intégré. Pour savoir si le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est lancé, à l'invite de commandes tapez :  
  
 **net start**  
  
 Si les services associés à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ont été démarrés, les services suivants s’affichent dans la sortie **net start** :  
  
-   Analysis Services (MSSQLSERVER)  
  
-   SQL Server (MSSQLSERVER)  
  
-   Agent SQL Server (MSSQLSERVER)  
  
## Exécution de SQL Server sans réseau  
 Lors de l'exécution d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sans réseau, il n'est pas nécessaire de démarrer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] intégré. Étant donné que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], le Gestionnaire de configuration SQL Server et les commandes **net start** et **net stop** sont toujours fonctionnels (même sans réseau), les procédures de démarrage et d’arrêt d’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont identiques, qu’il s’agisse d’un fonctionnement en réseau ou en mode autonome.  
  
 Quand vous vous connectez à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode autonome à partir d’une station cliente locale telle que **sqlcmd**, par exemple, vous ignorez le réseau et vous accédez directement à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’un canal de communication local. La différence entre un canal de communication local et un canal de communication réseau réside dans l'utilisation ou non d'un réseau. Les canaux de communication local et réseau établissent une connexion avec une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide du canal standard (\\\\.\pipe\sql\query), sauf instructions contraires.  
  
 Quand vous vous connectez à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale sans spécifier le nom d'un serveur, vous utilisez un canal de communication local. Lorsque vous vous connectez à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale en spécifiant explicitement le nom d'un serveur, vous utilisez soit un canal réseau, soit un autre mécanisme de réseau IPC, comme IPX/SPX (Internetwork Packet Exchange/Sequenced Packet Exchange) (si vous avez configuré [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour une utilisation multi-réseau). Comme une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autonome ne gère pas les canaux de communication réseau, vous devez omettre l’argument **/***<nom_serveur>*, devenu inutile, quand vous vous connectez à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d’un client. Par exemple, pour vous connecter à une instance autonome de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir de **osql**, tapez :  
  
 **osql /Usa /P** *\<mot_de_passe_sa>*  
  
  