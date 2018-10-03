---
title: Configurer un serveur pour écouter un port de TCP spécifique (Gestionnaire de Configuration SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- fixed port
- static ports
- ports [SQL Server], assigning numbers
- assigning port numbers
- dynamic ports [SQL Server]
- TCP/IP [SQL Server], port numbers
ms.assetid: 2276a5ed-ae3f-4855-96d8-f5bf01890640
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d408c25216139a173dced0ae19f9ddea7d1ba4d5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088069"
---
# <a name="configure-a-server-to-listen-on-a-specific-tcp-port-sql-server-configuration-manager"></a>Configurer un serveur pour écouter un port TCP spécifique (Gestionnaire de configuration SQL Server)
  Cette rubrique explique comment configurer une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] pour l'écoute sur un port fixe spécifique à l'aide du Gestionnaire de configuration SQL Server. Si elle est activée, l’instance par défaut du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] écoute le port TCP 1433. Les instances nommées du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et de [!INCLUDE[ssEW](../../includes/ssew-md.md)] sont configurées pour des ports dynamiques. Cela signifie qu'elles sélectionnent un port disponible lorsque le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est démarré. Lorsque vous vous connectez à une instance nommée par l'intermédiaire d'un pare-feu, configurez le [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour écouter un port spécifique, de façon à pouvoir ouvrir le port approprié dans le pare-feu.  
  
 Pour plus d’informations sur les paramètres par défaut du Pare-feu Windows et pour obtenir une description des ports TCP qui affectent le moteur de base de données, Analysis Services, Reporting Services et Integration Services, consultez [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
> [!TIP]  
>  Lors de la sélection du numéro de port, consultez [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers) pour obtenir la liste des numéros de ports attribués aux applications spécifiques. sélectionnez un numéro de port non assigné. Pour plus d’informations, consultez [La plage de port dynamique par défaut pour le protocole TCP/IP a changé dans Windows Vista et dans Windows Server 2008](http://support.microsoft.com/kb/929851).  
  
> [!WARNING]  
>  Le moteur de base de données commence l'écoute sur un nouveau port une fois redémarré. Toutefois le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser surveille le Registre et signale le nouveau numéro de port dès que la configuration est modifiée, même si le moteur de base de données ne l'utilise pas. Redémarrez le moteur de base de données pour assurer la cohérence et éviter les échecs de connexion.  
  
 **Dans cette rubrique**  
  
-   **Pour configurer un serveur pour l'écoute sur un port TCP spécifique, utilisez :**  
  
     [Gestionnaire de configuration SQL Server](#SSMSProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
  
#### <a name="to-assign-a-tcpip-port-number-to-the-sql-server-database-engine"></a>Pour affecter un numéro de port TCP/IP au moteur de base de données SQL Server  
  
1.  Dans le Gestionnaire de configuration SQL Server, dans le volet de la console, développez **Configuration du réseau SQL Server**, **Protocoles pour \<nom_instance>** puis double-cliquez sur **TCP/IP**.  
  
2.  Dans la boîte de dialogue **Propriétés TCP/IP** , sous l’onglet **Adresses IP** , plusieurs adresses IP apparaissent au format **IP1**, **IP2**, jusqu’à **IPAll**. Une de ces adresses correspond à l'adresse IP de la carte de bouclage, 127.0.0.1. D'autres adresses sont affichées pour chaque adresse IP sur l'ordinateur. Cliquez avec le bouton droit sur chaque adresse, puis cliquez sur **Propriétés** pour identifier l'adresse IP que vous voulez configurer.  
  
3.  Si la boîte de dialogue **Ports TCP dynamiques** contient **0**pour indiquer que [!INCLUDE[ssDE](../../includes/ssde-md.md)] écoute les ports dynamiques, supprimez le 0.  
  
4.  Dans la boîte de dialogue **Propriétés* **IP***n**, dans la zone **Port TCP**, tapez le numéro du port sur lequel vous voulez que cette adresse IP écoute, puis cliquez sur **OK**.  
  
5.  Dans le volet de la console, cliquez sur **Services SQL Server**.  
  
6.  Dans le volet Détails, cliquez avec le bouton droit sur **SQL Server (**\<nom_instance>**)** puis cliquez sur **Redémarrer** pour arrêter et redémarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Après avoir configuré [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour écouter un port spécifique, il existe trois manières de vous connecter à un port spécifique avec une application cliente :  
  
-   Exécutez le service Explorateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le serveur à connecter à l'instance [!INCLUDE[ssDE](../../includes/ssde-md.md)] par le nom.  
  
-   Créez un alias sur le client, en spécifiant le numéro du port.  
  
-   Programmer le client pour une connexion à l'aide d'une chaîne de connexion personnalisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer ou supprimer un alias de serveur devant être utilisé par un client &#40;Gestionnaire de configuration SQL Server&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md)  
  
  
