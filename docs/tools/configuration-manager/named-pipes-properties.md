---
title: "Propri&#233;t&#233;s de Canaux nomm&#233;s | Microsoft Docs"
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
  - "canaux [SQL Server]"
  - "écoute [SQL Server], canaux"
  - "canaux [SQL Server], écoute"
  - "canaux nommés [SQL Server], écoute"
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# Propri&#233;t&#233;s de Canaux nomm&#233;s
  Utilisez la page **Protocole** de la boîte de dialogue **Propriétés des canaux nommés** pour afficher ou modifier le canal nommé sur lequel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écoute, pendant l’utilisation du protocole Canaux nommés.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Pour activer ou désactiver le protocole, ou modifier le canal nommé, doit être redémarré.  
  
## Options  
 **Activé**  
 Les valeurs possibles sont **Yes** et **No**.  
  
 **Nom du canal**  
 Spécifie le canal nommé sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écoute. Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est à l'écoute sur `\\.\pipe\sql\query` pour l'instance par défaut et sur `\\.\pipe\MSSQL$<instancename>\sql\query` pour une instance nommée. Ce champ est limité à 2 047 caractères.  
  
## Création d'un autre canal nommé  
 Pour modifier le canal nommé, tapez le nom du nouveau canal dans la zone **Nom du canal** puis arrêtez et redémarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Étant donné que **sql\query** est connu comme étant le canal nommé utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le fait de modifier ce canal peut permettre de réduire les risques d’attaques par des programmes malveillants.  
  
### Exemple  
 Tapez **\\\\.\pipe\unit\app** pour écouter sur le canal **unit\app**.  
  
 Tapez **\\\\.\pipe\acct** pour écouter sur le canal **acct**.  
  
## Voir aussi  
 [Activer ou désactiver un protocole réseau de serveur](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [Choix d'un protocole réseau](../Topic/Choosing%20a%20Network%20Protocol.md)   
 [Création d'une chaîne de connexion valide à l'aide de canaux nommés](../Topic/Creating%20a%20Valid%20Connection%20String%20Using%20Named%20Pipes.md)  
  
  