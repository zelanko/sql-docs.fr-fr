---
title: Choix d’un protocole réseau | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
- Named Pipes [SQL Server]
- TCP [SQL Server]
- network protocols [SQL Server], choosing
- protocols [SQL Server], choosing
- NWLink IPX/SPX [SQL Server]
- client configuration [SQL Server], protocols
- VIA
- Multiprotocol Net-Library [SQL Server]
- IPX/SPX [SQL Server]
- Banyan VINES
- protocols [SQL Server], client configuration
ms.assetid: 6565fb7d-b076-4447-be90-e10d0dec359a
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 9c167994c7145bce348b6959a57533e398e1d6bb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63035281"
---
# <a name="choosing-a-network-protocol"></a>Choix d'un protocole réseau
  Pour se connecter au [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , un protocole réseau doit être activé. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut traiter les demandes sur plusieurs protocoles en même temps. Les clients se connectent à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec un seul protocole. Si le programme client ne connaît pas le protocole sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écoute, configurez le client pour qu'il essaie plusieurs protocoles en séquence. Le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous permet d'activer, de désactiver et de configurer des protocoles réseau.  
  
## <a name="shared-memory"></a>Mémoire partagée  
 Il s'agit du protocole le plus simple à utiliser et pour lequel aucun paramètre ne doit être configuré. Étant donné que les clients qui utilisent le protocole de mémoire partagée peuvent se connecter uniquement à une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exécutée sur le même ordinateur, il n'est pas utile pour la plupart des activités de base de données. Utilisez le protocole de mémoire partagée pour débloquer une situation dans laquelle vous suspectez que les autres protocoles ne sont pas configurés correctement.  
  
> [!NOTE]  
>  Les clients utilisant MDAC 2.8 ou une version antérieure ne peuvent pas utiliser le protocole de mémoire partagée. S'ils tentent d'utiliser ce protocole, ils sont automatiquement basculés sur le protocole de canaux nommés.  
  
## <a name="tcpip"></a>TCP/IP  
 TCP/IP est un protocole courant dont l'utilisation est largement répandue sur Internet. Il communique à travers des réseaux interconnectés d'ordinateurs dotés de différentes architectures matérielles et de divers systèmes d'exploitation. Le protocole TCP/IP comprend des normes qui permettent d'acheminer le trafic réseau et offre des fonctionnalités de sécurité avancées. Il est aujourd'hui le plus utilisé dans le monde de l'entreprise. La configuration de votre ordinateur pour l'utilisation du protocole TCP/IP peut s'avérer complexe, mais la plupart des ordinateurs en réseau sont déjà correctement configurés. Pour configurer les paramètres du protocole TCP/IP qui ne sont pas exposés dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez la documentation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
## <a name="named-pipes"></a>Canaux nommés  
 Les canaux nommés sont développés pour les réseaux locaux. Une partie de la mémoire est utilisée par un processus pour transmettre des informations à un autre processus, de sorte que la sortie d'un processus constitue l'entrée de l'autre. Le deuxième processus peut être local (situé sur le même ordinateur que le premier) ou distant (sur un ordinateur du réseau).  
  
## <a name="named-pipes-vs-tcpip-sockets"></a>Canaux nommés ou sockets TCP/IP  
 Dans un environnement de réseau local rapide, les clients utilisant les canaux nommés et les sockets TCP/IP (Transmission Control Protocol/Internet Protocol) sont comparables au niveau des performances. Toutefois, la différence de performances entre les clients utilisant les canaux nommés et ceux utilisant les sockets TCP/IP devient évidente avec des réseaux plus lents, comme les réseaux étendus (WAN) ou les réseaux commutés. Ceci est dû aux différences dans la manière dont les mécanismes de communication interprocessus IPC communiquent entre homologues.  
  
 Pour les canaux nommés, les communications réseau sont généralement plus interactives. Un homologue n'envoie pas de données tant qu'un autre homologue ne l'a pas demandé par le biais d'une commande de lecture. Une lecture via un réseau implique généralement une série de messages lus par les canaux nommés avant qu'elle ne commence à lire les données. Ces dernières peuvent se révéler très coûteuses sur un réseau lent et provoquer un trafic excessif qui finit par affecter d'autres clients du réseau.  
  
 Il est également important de faire la distinction entre les canaux locaux et les canaux réseau. Si l'application serveur fonctionne localement sur l'ordinateur exécutant une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le protocole local des canaux nommés est envisageable. Les canaux nommés locaux fonctionnent en mode noyau et sont extrêmement rapides.  
  
 Pour les sockets TCP/IP, les transmissions de données sont plus rationalisées et représentent une charge inférieure. Les transmissions de données peuvent également bénéficier des mécanismes d'amélioration des performances des sockets TCP/IP telles que le fenêtrage, les accusés de réception différés, etc. Cette option peut s'avérer fort utile dans le cadre d'un réseau lent. Selon le type d'application, les différences de performances peuvent être importantes.  
  
 Les sockets TCP/IP prennent également en charge une file d'attente de backlog, ce qui peut procurer un effet de lissage limité par rapport aux canaux de communication nommés, et conduire à des erreurs liées à l'encombrement des canaux lorsque vous tentez de vous connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 En général, il est préférable d'utiliser TCP/IP dans un réseau local, étendu (WAN) ou distant lent, alors que les canaux nommés peuvent s'avérer un meilleur choix si la vitesse du réseau ne pose pas problème ; TCP/IP offre davantage de fonctions et d'options de configuration et il est plus facile à utiliser.  
  
## <a name="enabling-the-protocol"></a>Activation du protocole  
 Pour pouvoir fonctionner, le protocole doit être activé sur le client et le serveur. Le serveur peut écouter les demandes simultanément sur tous les protocoles activés. Les ordinateurs clients peuvent en choisir un ou essayer d'utiliser les protocoles dans l'ordre dans lequel ils figurent dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Pour vous procurer un didacticiel sommaire sur la manière de configurer les protocoles et de vous connecter au [!INCLUDE[ssDE](../../includes/ssde-md.md)], consultez [Tutoriel : Bien démarrer avec le moteur de base de données](../../relational-databases/tutorial-getting-started-with-the-database-engine.md).  
  
  
