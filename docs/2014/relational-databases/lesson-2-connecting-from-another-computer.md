---
title: 'Leçon 2 : Connexion depuis un autre ordinateur | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: fd4ddeb8-0cb6-441b-9704-03575c07020f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: eedbde338ad3cc2af5477cc263eac7444707c0d8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63144807"
---
# <a name="lesson-2-connecting-from-another-computer"></a>Leçon 2 : Connexion depuis un autre ordinateur
  Pour une sécurité optimale, vous ne pouvez pas accéder au [!INCLUDE[ssDE](../includes/ssde-md.md)] des éditions Developer, Express et Evaluation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à partir d'un autre ordinateur lors de sa première installation. Dans cette leçon, vous allez apprendre à activer les protocoles et à configurer les ports et le Pare-feu Windows pour la connexion à partir d'autres ordinateurs.  
  
 Cette leçon contient les tâches suivantes :  
  
-   [Activation des protocoles](#protocols)  
  
-   [Configuration d'un port fixe](#port)  
  
-   [Ouverture de ports dans le pare-feu](#firewall)  
  
-   [Connexion au moteur de base de données depuis un autre ordinateur](#otherComp)  
  
-   [Connexion via le service SQL Server Browser](#browser)  
  
##  <a name="protocols"></a>Activation des protocoles  
 Pour une meilleure sécurité, les éditions [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]Developer et Evaluation sont installées uniquement avec une connectivité réseau limitée. Les connexions au [!INCLUDE[ssDE](../includes/ssde-md.md)] peuvent être établies à partir d'outils en cours d'exécution sur le même ordinateur mais pas à partir d'autres ordinateurs. Si vous envisagez de mener vos travaux de développement sur le même ordinateur que le [!INCLUDE[ssDE](../includes/ssde-md.md)], vous n'avez pas à activer des protocoles supplémentaires. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] se connecte au [!INCLUDE[ssDE](../includes/ssde-md.md)] à l'aide du protocole de mémoire partagée. Ce protocole est déjà activé.  
  
 Si vous prévoyez de vous connecter au [!INCLUDE[ssDE](../includes/ssde-md.md)] à partir d’un autre ordinateur, vous devez activer un protocole, tel que le protocole TCP/IP.  
  
#### <a name="how-to-enable-tcpip-connections-from-another-computer"></a>Comment activer des connexions TCP/IP à partir d'un autre ordinateur  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]et sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
    > [!NOTE]  
    >  Il est possible que les options 32 bits et 64 bits soient toutes deux disponibles.  
  
2.  Dans **Gestionnaire de configuration SQL Server**, développez **configuration du réseau SQL Server**, puis cliquez sur **protocoles pour** _ \<InstanceName>_.  
  
     L’instance par défaut (instance sans nom) est répertoriée sous **MSSQLSERVER**. Si vous avez installé une instance nommée, le nom que vous indiquez est répertorié. [!INCLUDE[ssExpressEd11](../includes/ssexpressed11-md.md)]s’installe en tant que **SQLExpress**, sauf si vous avez modifié le nom lors de l’installation.  
  
3.  Dans la liste des protocoles, cliquez avec le bouton droit sur le protocole à activer (**TCP/IP**), puis cliquez sur **Activer**.  
  
    > [!NOTE]  
    >  Lorsque vous avez apporté des modifications aux protocoles réseau, vous devez redémarrer le service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ; toutefois, cette opération est prévue dans la tâche suivante.  
  
##  <a name="port"></a>Configuration d’un port fixe  
 Pour une sécurité optimale, Windows Server 2008, [!INCLUDE[wiprlhlong](../includes/wiprlhlong-md.md)]et Windows 7 activent le Pare-feu Windows. Pour vous connecter à cette instance à partir d'un autre ordinateur, vous devez ouvrir un port de communication dans le pare-feu. L'instance par défaut du [!INCLUDE[ssDE](../includes/ssde-md.md)] écoute sur le port 1433 ; par conséquent, vous n'avez pas besoin de configurer un port fixe. Toutefois, les instances nommées incluant [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] sont à l'écoute sur des ports dynamiques. Avant d'ouvrir un port sur le pare-feu, vous devez configurer le [!INCLUDE[ssDE](../includes/ssde-md.md)] pour l'écoute sur un port spécifique appelé port fixe ou port statique ; le [!INCLUDE[ssDE](../includes/ssde-md.md)] peut également écouter sur un port différent à chaque démarrage. Pour plus d’informations sur les pare-feu, les paramètres par défaut du Pare-feu Windows et pour obtenir une description des ports TCP qui affectent le moteur de base de données, Analysis Services, Reporting Services et Integration Services, consultez [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
> [!NOTE]  
>  Les attributions de numéro de port sont gérées par l’autorité des numéros [http://www.iana.org](https://go.microsoft.com/fwlink/?LinkId=48844)d’Internet affectées et sont répertoriées dans. Les numéros de port doivent être attribués à partir des numéros 49152 à 65535.  
  
#### <a name="configure-sql-server-to-listen-on-a-specific-port"></a>Pour configurer SQL Server pour l'écoute sur un port spécifique  
  
1.  Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , développez **Configuration du réseau SQL Server**, puis cliquez sur l'instance du serveur à configurer.  
  
2.  Dans le volet droit, double-cliquez sur **TCP/IP**.  
  
3.  Dans la boîte de dialogue **Propriétés TCP/IP** , cliquez sur l’onglet **Adresses IP** .  
  
4.  Dans la zone **Port TCP** de la section **IPAll** , tapez un numéro de port disponible. Pour ce didacticiel, nous allons utiliser `49172`.  
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue, puis cliquez à nouveau sur **OK** dès l'apparition du message d'avertissement indiquant que vous devez redémarrer le service.  
  
6.  Dans le volet gauche, cliquez sur **Services SQL Server**.  
  
7.  Dans le volet droit, cliquez avec le bouton droit sur l’instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], puis cliquez sur **Redémarrer**. Lorsque le [!INCLUDE[ssDE](../includes/ssde-md.md)] redémarre, il écoute sur le port `49172`.  
  
##  <a name="firewall"></a>Ouverture de ports dans le pare-feu  
 Les systèmes de pare-feu contribuent à empêcher les accès non autorisés aux ressources informatiques. Pour vous connecter à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à partir d'un autre ordinateur lorsque le pare-feu est activé, vous devez ouvrir un port dans ce pare-feu.  
  
> [!IMPORTANT]  
>  L'ouverture de ports dans votre pare-feu peut exposer votre serveur à des attaques malveillantes. Assurez-vous de bien comprendre le fonctionnement des systèmes de pare-feu avant d'ouvrir des ports. Pour plus d’informations, consultez [Considérations sur la sécurité pour une Installation SQL Server](../sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
 Après avoir configuré le [!INCLUDE[ssDE](../includes/ssde-md.md)] en vue de l'utilisation d'un port fixe, suivez les instructions ci-après pour ouvrir ce port dans votre Pare-feu Windows. (Vous n'avez pas besoin de configurer un port fixe pour l'instance par défaut puisque le port fixe TCP 1433 est déjà défini.)  
  
#### <a name="to-open-a-port-in-the-windows-firewall-for-tcp-access-windows-7"></a>Pour ouvrir un port dans le Pare-feu Windows pour l'accès TCP (Windows 7)  
  
1.  Dans le menu **Démarrer** , cliquez sur **exécuter**, tapez **WF. msc**, puis cliquez sur **OK**.  
  
2.  Dans **Pare-feu Windows avec fonctions avancées de sécurité**, dans le volet gauche, cliquez avec le bouton droit sur **Règles de trafic entrant**, puis sélectionnez **Nouvelle règle** dans le volet Action.  
  
3.  Dans la boîte de dialogue **Type de règle**, sélectionnez **Port**, puis cliquez sur **Suivant**.  
  
4.  Dans la boîte de dialogue **Protocoles et ports**, sélectionnez **TCP**. Sélectionnez **Ports locaux spécifiques**, puis tapez le numéro de port de l'instance du [!INCLUDE[ssDE](../includes/ssde-md.md)]. Tapez 1433 pour l'instance par défaut. Tapez `49172` si vous configurez une instance nommée et que vous avez configuré un port fixe dans la tâche précédente. Cliquez sur **Suivant**.  
  
5.  Dans la boîte de dialogue **Action**, sélectionnez **Autoriser la connexion**, puis cliquez sur **Suivant**.  
  
6.  Dans la boîte de dialogue **Profil** , sélectionnez des profils qui décrivent l'environnement de connexion de l'ordinateur lorsque vous souhaitez vous connecter au [!INCLUDE[ssDE](../includes/ssde-md.md)], puis cliquez sur **Suivant**.  
  
7.  Dans la boîte de dialogue **Nom**, entrez un nom et une description pour cette règle, puis cliquez sur **Terminer**.  
  
 Pour plus d’informations sur la configuration du pare-feu, y compris des instructions concernant [!INCLUDE[wiprlhlong](../includes/wiprlhlong-md.md)], consultez [Configurer un pare-feu Windows pour accéder au moteur de base de données](../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md). Pour plus d’informations sur les paramètres par défaut du Pare-feu Windows et pour obtenir une description des ports TCP qui affectent le moteur de base de données, Analysis Services, Reporting Services et Integration Services, consultez [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
##  <a name="otherComp"></a>Connexion au Moteur de base de données à partir d’un autre ordinateur  
 Après avoir configuré le [!INCLUDE[ssDE](../includes/ssde-md.md)] pour l'écoute d'un port fixe, puis ouvert le port dans le pare-feu, vous pouvez vous connecter à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à partir d'un autre ordinateur.  
  
 Lorsque le service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser est exécuté sur le serveur et que le pare-feu a ouvert le port UDP 1434, vous pouvez établir la connexion à l'aide du nom de l'ordinateur et du nom d'instance. Pour une meilleure sécurité, notre exemple ne fait pas appel au service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser.  
  
#### <a name="to-connect-to-the-database-engine-from-another-computer"></a>Pour vous connecter au moteur de base de données depuis un autre ordinateur  
  
1.  Sur un deuxième ordinateur contenant les outils clients [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , ouvrez une session avec un compte autorisé pour vous connecter à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]et ouvrez [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
2.  Dans la boîte de dialogue **Se connecter au serveur** , confirmez **Moteur de base de données** dans la zone **Type de serveur** .  
  
3.  Dans la zone **Nom du serveur** , tapez **tcp:** pour spécifier le protocole, suivi du nom d'ordinateur, d'une virgule et du numéro de port. Pour vous connecter à l’instance par défaut, le port 1433 est implicite et peut être omis. par conséquent, tapez **TCP :** _<computer_name>_. Dans notre exemple pour une instance nommée, tapez **TCP :** _<computer_name>_ **, 49172**.  
  
    > [!NOTE]  
    >  Si vous omettez **tcp:** dans la zone **Nom du serveur** , le client essaie tous les protocoles activés, dans l’ordre spécifié dans sa configuration.  
  
4.  Dans la zone **Authentification** , confirmez **Authentification Windows**, puis cliquez sur **Se connecter**.  
  
##  <a name="browser"></a>Connexion à l’aide du service SQL Server Browser  
 Le service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser écoute les demandes entrantes des ressources [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et fournit des informations sur les instances [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installées sur l'ordinateur. Lorsque le service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser est en cours d'exécution, les utilisateurs peuvent se connecter à des instances nommées en fournissant les noms de l'ordinateur et de l'instance à la place du nom de l'ordinateur et du numéro de port. Du fait que le service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser reçoit des requêtes UDP non authentifiées, il n'est pas toujours activé lors de l'installation. Pour obtenir une description du service et une indication du moment où il est activé, consultez [Service SQL Server Browser &#40;moteur de base de données et SSAS&#41;](../database-engine/configure-windows/sql-server-browser-service-database-engine-and-ssas.md).  
  
 Pour utiliser le service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser, vous devez suivre la même procédure que précédemment, puis ouvrir le port UDP 1434 dans le pare-feu.  
  
 Cette étape est la dernière de ce didacticiel sommaire sur les notions de connexion de base.  
  
## <a name="return-to-tutorials-portal"></a>Revenir au portail des didacticiels  
 [Didacticiel : mise en route du moteur de base de données](tutorial-getting-started-with-the-database-engine.md)  
  
  
