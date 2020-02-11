---
title: Publier des données sur Internet à l’aide d’un réseau privé virtuel | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- VPNs [SQL Server replication]
- Web publishing [SQL Server replication], VPNs
- Internet [SQL Server replication], VPNs
ms.assetid: 9ffb6546-9973-4574-aaa0-8fe0017e3601
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f090e48f97f4756f6c87b7cac2a6db64105ef265
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63021060"
---
# <a name="publish-data-over-the-internet-using-vpn"></a>Publier des données sur Internet à l'aide d'un réseau privé virtuel
  La technologie des réseaux privés virtuels (VPN, Virtual Private Network) permet aux utilisateurs qui travaillent à domicile, dans des succursales, sur des clients distants et dans d'autres sociétés de se connecter à un réseau d'entreprise via Internet, tout en préservant des communications sécurisées. Les utilisateurs peuvent recourir à l'authentification Windows comme s'ils faisaient partie d'un réseau local (LAN, Local Area Network). Tous les types [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de réplication peuvent répliquer des données sur un réseau privé virtuel (VPN), mais envisagent d’utiliser la synchronisation Web si vous utilisez la réplication de fusion, car la synchronisation Web élimine la nécessité d’un VPN. Pour plus d’informations, voir [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).  
  
 Un réseau privé virtuel utilise un logiciel client qui permet aux ordinateurs de se connecter via Internet (ou, dans certains cas particuliers, même via un intranet) à un logiciel situé sur un ordinateur dédié ou sur un serveur. La sécurité des données est éventuellement assurée par le chiffrement aux deux extrémités et par des méthodes d'authentification des utilisateurs. La connexion au réseau privé virtuel via Internet fonctionne, sur le plan logique, comme une liaison de réseau étendu (WAN, Wide Area Network) entre les sites.  
  
 Un réseau privé virtuel connecte les composants d'un réseau par l'intermédiaire d'un autre réseau. Pour se connecter, l'utilisateur se sert d'une connexion tunnel à Internet ou un autre réseau privé à l'aide d'un protocole tel que [!INCLUDE[msCoName](../../includes/msconame-md.md)] PPTP (Point-to-Point Tunneling Protocol) ou L2TP (Layer Two Tunneling Protocol). Ce processus offre les fonctionnalités et la sécurité qui étaient autrefois l'apanage d'un réseau privé. Le protocole PPTP est disponible sur les systèmes d'exploitation Microsoft Windows NT version 4.0 et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 (et ultérieurs) et le protocole L2TP est disponible dans Windows 2000 et ultérieur.  
  
 Pour l'utilisateur, l'infrastructure de routage intermédiaire d'Internet n'est pas visible, et tout se passe comme si les données étaient envoyées via une liaison privée dédiée. Du point de vue des utilisateurs, le VPN est une connexion de point à point entre l'ordinateur de l'utilisateur et un serveur d'entreprise.  
  
 Dès que le client distant a été configuré pour se connecter via un VPN, qu'il bénéficie d'un accès à Internet et qu'il est connecté au réseau local d'entreprise, vous pouvez configurer la réplication comme si le client distant était directement connecté au réseau local. Par souci de sécurité, il est possible de différencier les ressources réseau mises à la disposition des utilisateurs connectés via le VPN et de ceux qui bénéficient d'une connexion directe au réseau local.  
  
 Pour plus d'informations sur la configuration d'un réseau privé virtuel (VPN), consultez la documentation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication sur Internet](replication-over-the-internet.md)  
  
  
