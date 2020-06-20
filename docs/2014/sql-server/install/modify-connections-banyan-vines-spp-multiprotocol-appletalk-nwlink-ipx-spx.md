---
title: Modifier les connexions qui utilisent les protocoles réseau Banyan VINEs Séquencéd paquet Protocol (SPP), Multiprotocol, AppleTalk ou NWLink IPX SPX | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- network protocols [SQL Server], modifying connections
- SPP [SQL Server]
- NWLink IPX/SPX [SQL Server]
- connections [SQL Server]
- AppleTalk [SQL Server]
- Sequenced Packet Protocol [SQL Server]
- Multiprotocol Net-Library [SQL Server]
- Banyan VINES Sequenced Package Protocol [SQL Server]
- IPX/SPX [SQL Server]
- protocols [SQL Server], modifying connections
- RPC [SQL Server]
ms.assetid: 5c5ae453-cc5b-4898-95c7-ad34157b1f60
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 750b9c0b76ab6c3b43908ecb8454f31ac1a25b1a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054712"
---
# <a name="modify-connections-that-use-banyan-vines-sequenced-packet-protocol-spp-multiprotocol-appletalk-or-nwlink-ipx-spx-network-protocols"></a>Modifier les connexions utilisant les protocoles réseau Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk ou NWLink IPX/SPX
  Le Conseiller de mise à niveau a détecté des protocoles de connexion serveur client qui ne sont pas pris en charge dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Les applications clientes qui utilisent les protocoles réseau Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol (RPC), AppleTalk ou NWLink IPX/SPX doivent se connecter à l'aide d'un protocole pris en charge.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ne prend pas en charge les protocoles réseau Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk ou NWLink IPX/SPX. Les clients précédemment connectés au moyen de ces protocoles doivent sélectionner un autre protocole.  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez les applications clientes pour qu'elles utilisent un protocole pris en charge lorsqu'elles se connectent au serveur. Si un alias est défini, qui utilise l'un des protocoles non pris en charge, cet alias doit alors être modifié pour utiliser un protocole pris en charge.  
  
 Si la chaîne de connexion de votre application utilise ou charge spécifiquement l’un de ces protocoles, soit en spécifiant NETWORK = DBMSRPCN pour RPC, NETWORK = DBMSADSN pour AppleTalk ou NETWORK = DBMSVINN pour la propriété Banyan VINEs, ou en utilisant un préfixe explicite tel que « SPX :*server\instance*» pour SPX, « BV :*serveur*» pour Banyan VINES, « ADSP :*serveur*» pour AppleTalk ou « RPC :*serveur*» pour le multiprotocole, vous devez modifier votre application pour utiliser l’un des protocoles pris en charge.  
  
 Pour plus d'informations, consultez « Choix d'un protocole réseau » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
