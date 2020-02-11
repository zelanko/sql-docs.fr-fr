---
title: Configurer un pare-feu Windows pour l’accès au moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], firewall systems
- firewall systems, [Database Engine]
- security [SQL Server], firewalls
ms.assetid: 0093b43c-c6b5-4574-9b30-3a0e91e1a1f9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6e0eafd8a8eb1d9d73f71ab069dc8bf0795a87bc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62812291"
---
# <a name="configure-a-windows-firewall-for-database-engine-access"></a>Configurer un pare-feu Windows pour accéder au moteur de base de données
  Cette rubrique explique comment configurer un pare-feu Windows pour l'accès du moteur de base de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide du Gestionnaire de configuration SQL Server. Les systèmes de pare-feu empêchent les accès non autorisés aux ressources de l'ordinateur. Pour accéder à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] par le biais d'un pare-feu, vous devez configurer le pare-feu de l'ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour autoriser l'accès.  
  
 Pour plus d’informations sur les paramètres par défaut du Pare-feu Windows et pour obtenir une description des ports TCP qui affectent le [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services et Integration Services, consultez [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md). De nombreux systèmes de pare-feu sont disponibles. Pour obtenir des informations spécifiques à votre système, consultez la documentation du pare-feu.  
  
 Deux principales étapes permettent d'autoriser l'accès :  
  
1.  Configurez le [!INCLUDE[ssDE](../../includes/ssde-md.md)] afin qu'il utilise un port TCP/IP particulier. L'instance par défaut du [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilise le port 1433, mais il est possible de modifier ce paramètre. Le port utilisé par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est indiqué dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les instances [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] et [!INCLUDE[ssEW](../../includes/ssew-md.md)], ainsi que les instances nommées du [!INCLUDE[ssDE](../../includes/ssde-md.md)], utilisent des ports dynamiques. Pour configurer ces instances pour utiliser un port spécifique, consultez [Configurer un serveur pour l’écoute sur un port TCP spécifique &#40;Gestionnaire de configuration SQL Server&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md).  
  
2.  Configurez le pare-feu pour permettre l'accès à ce port aux utilisateurs ou aux ordinateurs autorisés.  
  
> [!NOTE]  
>  Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser permet aux utilisateurs de se connecter à des instances du [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui n'écoutent pas sur le port 1433 sans connaître le numéro de port. Pour utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, vous devez ouvrir le port UDP 1434. Pour garantir un environnement sécurisé optimal, laissez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser désactivé et configurez les clients pour qu'ils se connectent avec ce numéro de port.  
  
> [!NOTE]  
>  Par défaut, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows active le pare-feu Windows ; ce dernier ferme alors le port 1433 pour empêcher des ordinateurs reliés à Internet de se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par défaut sur votre ordinateur. Les connexions à l'instance par défaut à l'aide du protocole TCP/IP sont impossibles si vous ne rouvrez pas le port 1433. Les procédures suivantes présentent les étapes de base permettant de configurer le pare-feu Windows. Pour plus d'informations, consultez la documentation Windows.  
  
 Si la configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour l'écoute sur un port fixe et l'ouverture du port est une solution qui ne vous convient pas, vous pouvez également inscrire le fichier exécutable de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (Sqlservr.exe) en tant qu'exception pour les programmes verrouillés. Optez pour cette méthode si vous souhaitez continuer à utiliser des ports dynamiques. Vous ne pouvez accéder qu'à une seule instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec cette méthode.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour configurer un pare-feu Windows donnant accès au moteur de base de données avec :**  
  
     [Gestionnaire de configuration SQL Server](#SSMSProcedure)  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 L'ouverture de ports dans votre pare-feu peut exposer votre serveur à des attaques malveillantes. Assurez-vous de comprendre le fonctionnement des systèmes de pare-feu avant d'ouvrir des ports. Pour plus d'informations, consultez [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
##  <a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
 S'applique à Windows Vista, Windows 7 et Windows Server 2008  
  
 Les procédures suivantes configurent le Pare-feu Windows à l'aide du composant logiciel enfichable MMC (Microsoft Management Console) de fonctions avancées de sécurité. Le Pare-feu Windows avec fonctions avancées de sécurité configure uniquement le profil actuel. Pour plus d’informations sur le Pare-feu Windows avec fonctions avancées de sécurité, consultez [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
#### <a name="to-open-a-port-in-the-windows-firewall-for-tcp-access"></a>Pour ouvrir un port dans le pare-feu Windows pour l'accès TCP  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**, tapez **WF.msc**, puis cliquez sur **OK**.  
  
2.  Dans le **Pare-feu Windows avec fonctions avancées de sécurité**, dans le volet gauche, cliquez avec le bouton droit sur **Règles de trafic entrant**, puis cliquez sur **Nouvelle règle** dans le volet Action.  
  
3.  Dans la boîte de dialogue **Type de règle** , sélectionnez **Port**, puis cliquez sur **Suivant**.  
  
4.  Dans la boîte de dialogue **Protocoles et ports** , sélectionnez **TCP**. Sélectionnez **ports locaux spécifiques**, puis tapez le numéro de port de l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)], par exemple `1433` pour l’instance par défaut. Cliquez sur **Suivant**.  
  
5.  Dans la boîte de dialogue **Action** , sélectionnez **Autoriser la connexion**, puis cliquez sur **Suivant**.  
  
6.  Dans la boîte de dialogue **Profil** , sélectionnez des profils qui décrivent l'environnement de connexion de l'ordinateur lorsque vous souhaitez vous connecter au [!INCLUDE[ssDE](../../includes/ssde-md.md)], puis cliquez sur **Suivant**.  
  
7.  Dans la boîte de dialogue **Nom**, entrez un nom et une description pour cette règle, puis cliquez sur **Terminer**.  
  
#### <a name="to-open-access-to-sql-server-when-using-dynamic-ports"></a>Pour ouvrir l'accès à SQL Server lors de l'utilisation de ports dynamiques  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**, tapez **WF.msc**, puis cliquez sur **OK**.  
  
2.  Dans le **Pare-feu Windows avec fonctions avancées de sécurité**, dans le volet gauche, cliquez avec le bouton droit sur **Règles de trafic entrant**, puis cliquez sur **Nouvelle règle** dans le volet Action.  
  
3.  Dans la boîte de dialogue **Type de règle** , sélectionnez **Programme**, puis cliquez sur **Suivant**.  
  
4.  Dans la boîte de dialogue **Programme** , sélectionnez **Ce chemin d'accès au programme**. Cliquez sur **Parcourir**et accédez à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous voulez accéder par le biais du pare-feu, puis cliquez sur **Ouvrir**. Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se trouve dans **C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe**. Cliquez sur **Suivant**.  
  
5.  Dans la boîte de dialogue **Action** , sélectionnez **Autoriser la connexion**, puis cliquez sur **Suivant**.  
  
6.  Dans la boîte de dialogue **Profil** , sélectionnez des profils qui décrivent l'environnement de connexion de l'ordinateur lorsque vous souhaitez vous connecter au [!INCLUDE[ssDE](../../includes/ssde-md.md)], puis cliquez sur **Suivant**.  
  
7.  Dans la boîte de dialogue **Nom**, entrez un nom et une description pour cette règle, puis cliquez sur **Terminer**.  
  
  
