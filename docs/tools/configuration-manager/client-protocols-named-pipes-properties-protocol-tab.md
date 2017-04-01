---
title: "Protocoles clients - Propri&#233;t&#233;s de Canaux nomm&#233;s (onglet Protocole) | Microsoft Docs"
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
  - "canaux [SQL Server], connexion à"
  - "Canaux nommés [SQL Server], canal par défaut"
  - "protocoles clients [SQL Server]"
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Protocoles clients - Propri&#233;t&#233;s de Canaux nomm&#233;s (onglet Protocole)
  Dans le Gestionnaire de configuration [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , utilisez l'onglet **Protocole** de la boîte de dialogue **Propriétés de Canaux nommés** pour visualiser ou modifier la description du canal par défaut. Pour vous connecter à un autre canal, tapez son nom dans la zone **Canal par défaut** . Pour plus d'informations sur les chaînes de connexion, consultez [Creating a Valid Connection String Using Named Pipes](../Topic/Creating%20a%20Valid%20Connection%20String%20Using%20Named%20Pipes.md).  
  
## Options  
 **Canal par défaut**  
 Spécifie le canal par défaut que la Net-Library des canaux nommés essaie d'utiliser pour se connecter à l'instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est à l'écoute sur : `\\.\pipe\sql\query`  
  
 Pour vous connecter au canal par défaut, entrez `sql\query`  
  
 **Activé**  
 Les valeurs possibles sont **Yes** et **No**.  
  
## Voir aussi  
 [Choix d'un protocole réseau](../Topic/Choosing%20a%20Network%20Protocol.md)  
  
  