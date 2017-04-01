---
title: "Publier des donn&#233;es sur Internet &#224; l&#39;aide d&#39;un r&#233;seau priv&#233; virtuel | Microsoft Docs"
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
  - "réseaux privés virtuels [réplication SQL Server]"
  - "publication web [réplication SQL Server], VPN"
  - "Internet [réplication SQL Server], VPN"
ms.assetid: 9ffb6546-9973-4574-aaa0-8fe0017e3601
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Publier des donn&#233;es sur Internet &#224; l&#39;aide d&#39;un r&#233;seau priv&#233; virtuel
  La technologie des réseaux privés virtuels (VPN, Virtual Private Network) permet aux utilisateurs qui travaillent à domicile, dans des succursales, sur des clients distants et dans d'autres sociétés de se connecter à un réseau d'entreprise via Internet, tout en préservant des communications sécurisées. Les utilisateurs peuvent recourir à l'authentification Windows comme s'ils faisaient partie d'un réseau local (LAN, Local Area Network). Tous les types de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] réplication peut répliquer des données via une connexion VPN, mais envisagez d’utiliser la synchronisation Web si vous utilisez la réplication de fusion, car la synchronisation Web élimine le besoin d’une connexion VPN. Pour plus d’informations, voir [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
 Un réseau privé virtuel utilise un logiciel client qui permet aux ordinateurs de se connecter via Internet (ou, dans certains cas particuliers, même via un intranet) à un logiciel situé sur un ordinateur dédié ou sur un serveur. La sécurité des données est éventuellement assurée par le chiffrement aux deux extrémités et par des méthodes d'authentification des utilisateurs. La connexion au réseau privé virtuel via Internet fonctionne, sur le plan logique, comme une liaison de réseau étendu (WAN, Wide Area Network) entre les sites.  
  
 Un réseau privé virtuel connecte les composants d'un réseau par l'intermédiaire d'un autre réseau. Pour se connecter, l'utilisateur se sert d'une connexion tunnel à Internet ou un autre réseau privé à l'aide d'un protocole tel que [!INCLUDE[msCoName](../../includes/msconame-md.md)] PPTP (Point-to-Point Tunneling Protocol) ou L2TP (Layer Two Tunneling Protocol). Ce processus offre les fonctionnalités et la sécurité qui étaient autrefois l'apanage d'un réseau privé. PPTP est disponible avec Microsoft Windows NT version 4.0 et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 (et versions ultérieures) systèmes d’exploitation L2TP est disponible avec Windows 2000 et versions ultérieures.  
  
 Pour l'utilisateur, l'infrastructure de routage intermédiaire d'Internet n'est pas visible, et tout se passe comme si les données étaient envoyées via une liaison privée dédiée. Du point de vue des utilisateurs, le VPN est une connexion de point à point entre l'ordinateur de l'utilisateur et un serveur d'entreprise.  
  
 Dès que le client distant a été configuré pour se connecter via un VPN, qu'il bénéficie d'un accès à Internet et qu'il est connecté au réseau local d'entreprise, vous pouvez configurer la réplication comme si le client distant était directement connecté au réseau local. Par souci de sécurité, il est possible de différencier les ressources réseau mises à la disposition des utilisateurs connectés via le VPN et de ceux qui bénéficient d'une connexion directe au réseau local.  
  
 Pour plus d'informations sur la configuration d'un réseau privé virtuel (VPN), consultez la documentation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
## Voir aussi  
 [Réplication sur Internet](../../relational-databases/replication/replication-over-the-internet.md)  
  
  