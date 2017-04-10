---
title: "S&#233;curit&#233; de la r&#233;plication sur Internet | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sécurité [réplication SQL Server], Internet"
  - "Internet [réplication SQL Server], sécurité"
ms.assetid: 25b7af05-2721-4b24-9083-fb671e8bf4e0
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# S&#233;curit&#233; de la r&#233;plication sur Internet
  La réplication sur Internet est une solution souple, notamment pour les Abonnés itinérants, à condition qu'elle soit configurée correctement afin d'assurer une sécurité adaptée. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] recommande d’utiliser une des deux techniques pour partager des informations en toute sécurité sur Internet :  
  
-   le réseau privé virtuel (VPN, Virtual Private Network) ;  
  
-   l'option de synchronisation Web pour la réplication de fusion.  
  
## Réseau privé virtuel (VPN)  
 Les réseaux privés virtuels fournissent une méthode en couche simple et sécurisée pour répliquer des données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Internet. La connexion au réseau privé virtuel via Internet fonctionne, sur le plan logique, comme une liaison de réseau étendu (WAN, Wide Area Network) entre les sites.  
  
 Cela est possible en autorisant l’utilisateur à tunnel via Internet ou un autre réseau public à l’aide d’un protocole tel que [!INCLUDE[msCoName](../../../includes/msconame-md.md)] point à point Tunneling Protocol (PPTP) disponibles avec le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows NT version 4.0 ou [!INCLUDE[msCoName](../../../includes/msconame-md.md)] système d’exploitation Windows 2000 ou Layer Two Tunneling Protocol (L2TP) disponibles avec le système d’exploitation Windows 2000. Ce processus offre la sécurité et des fonctionnalités similaires à celles qui sont disponibles dans un réseau privé.  
  
 Pour plus d'informations sur la configuration d'un réseau privé virtuel (VPN), consultez la documentation [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows.  
  
## Synchronisation Web par le biais d'IIS  
 L'option de synchronisation Web pour la réplication de fusion permet de répliquer des données via le protocole HTTPS, ce qui peut être une méthode de réplication des données pratique via un pare-feu. Pour plus d’informations, consultez [configurer la synchronisation Web](../../../relational-databases/replication/configure-web-synchronization.md) et [Architecture de sécurité pour la synchronisation Web](../../../relational-databases/replication/security/security-architecture-for-web-synchronization.md).  
  
## Voir aussi  
 [Méthodes préconisées en matière de sécurité de réplication](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sécurité et Protection & #40 ; Réplication & #41 ;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  