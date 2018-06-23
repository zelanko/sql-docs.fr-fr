---
title: Protocoles clients - TCP et les propriétés de l’IP (onglet protocole) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TCP/IP [SQL Server], client protocols
- client protocols [SQL Server]
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
caps.latest.revision: 24
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2495b6c504083189313acf15e2bf8ecd0567aca2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142389"
---
# <a name="client-protocols---tcp-and-ip-properties-protocol-tab"></a>Protocoles clients - TCP et les propriétés de l’IP (onglet protocole)
  Dans le Gestionnaire de connexions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , utilisez l’onglet **Protocole** de la boîte de dialogue **Propriétés TCP/IP** pour afficher ou spécifier les options suivantes. Pour vous connecter à un autre port, tapez le numéro du port dans la zone **Port par défaut** . Pour plus d’informations sur les chaînes de connexion, consultez [Création d’une chaîne de connexion valide à l’aide du protocole TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md).  
  
## <a name="options"></a>Options  
 **Port par défaut**  
 Spécifie le port par défaut que la Net-Library TCP/IP essaie d'utiliser pour se connecter à l'instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le port par défaut est 1433.  
  
 Lorsqu'un client se connecte à une instance par défaut du [!INCLUDE[ssDE](../../includes/ssde-md.md)], il utilise cette valeur. Si une instance par défaut a été configurée pour écouter sur un port différent, remplacez cette valeur par ce numéro de port.  
  
 Lorsqu'un client se connecte à une instance nommée de [!INCLUDE[ssDE](../../includes/ssde-md.md)], il essaie d'obtenir le numéro de port auprès du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser exécuté sur l'ordinateur serveur. Si le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser n'est pas en cours d'exécution, le numéro de port doit être spécifié par le biais de ce paramètre ou dans la chaîne de connexion.  
  
 **Activé**  
 Les valeurs possibles sont **Yes** et **No**.  
  
 **Keep Alive**  
 Ce paramètre (en millisecondes) contrôle la fréquence à laquelle TCP tente de vérifier qu’une connexion inactive est toujours intacte en envoyant un paquet **KEEPALIVE** . La valeur par défaut est 30  000 millisecondes.  
  
 **Intervalle Keep Alive**  
 Ce paramètre (en millisecondes), détermine l’intervalle qui sépare les retransmissions **KEEPALIVE** jusqu’à ce qu’une réponse soit reçue. La valeur par défaut est 1 000 millisecondes.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d’un protocole réseau](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Nouvel alias &#40;onglet Alias&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md)   
 [&#60;Alias&#62; propriétés &#40;onglet Alias&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)  
  
  