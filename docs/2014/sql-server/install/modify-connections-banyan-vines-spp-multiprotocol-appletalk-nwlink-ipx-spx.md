---
title: Modifier les connexions qui utilisent des protocoles réseau Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk ou NWLink IPX SPX | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: cdbcaa39e3d9630bd4ea50919f31cdbb15a36d14
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66093897"
---
# <a name="modify-connections-that-use-banyan-vines-sequenced-packet-protocol-spp-multiprotocol-appletalk-or-nwlink-ipx-spx-network-protocols"></a>Modifier les connexions utilisant les protocoles réseau Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk ou NWLink IPX/SPX
  Le Conseiller de mise à niveau a détecté des protocoles de connexion serveur client qui ne sont pas pris en charge dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Les applications clientes qui utilisent les protocoles réseau Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol (RPC), AppleTalk ou NWLink IPX/SPX doivent se connecter à l'aide d'un protocole pris en charge.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ne prend pas en charge les protocoles réseau Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk ou NWLink IPX/SPX. Les clients précédemment connectés au moyen de ces protocoles doivent sélectionner un autre protocole.  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez les applications clientes pour qu'elles utilisent un protocole pris en charge lorsqu'elles se connectent au serveur. Si un alias est défini, qui utilise l'un des protocoles non pris en charge, cet alias doit alors être modifié pour utiliser un protocole pris en charge.  
  
 Si votre connexion de l’application chaîne spécifiquement utilise ou charge d’un de ces protocoles, par un réseau en spécifiant = des DBMSRPCN pour RPC, NETWORK = DBMSADSN pour Appletalk ou réseau = DBMSVINN pour la propriété de Banyan VINES, ou à l’aide d’un préfixe explicite tel que « spx : *serveur\instance*» pour SPX, « bv :*server*» pour Banyan VINES, » adsp :*server*» pour AppleTalk, ou » rpc :*server*« pour multiprotocole, puis vous devez modifier votre application pour utiliser un des protocoles pris en charge.  
  
 Pour plus d'informations, consultez « Choix d'un protocole réseau » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
