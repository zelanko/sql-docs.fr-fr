---
title: Configurer une URL (Gestionnaire de configuration de SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], syntax
ms.assetid: 851e163a-ad2a-491e-bc1e-4df92327092f
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 676bbf12efa9b8640ef244f6dd57325b047d79ba
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018920"
---
# <a name="configure-a-url--ssrs-configuration-manager"></a>Configurer une URL (Gestionnaire de configuration de SSRS)
  Avant de pouvoir utiliser le Gestionnaire de rapports ou le service Web Report Server, vous devez configurer au moins une URL pour chaque application. La configuration des URL est obligatoire si vous avez installé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode « fichiers uniquement » (autrement dit, en sélectionnant l'option **Installer mais ne pas configurer le serveur** sur la page Options d'installation du serveur de rapports dans l'Assistant Installation). Si vous avez installé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans la configuration par défaut, les URL sont déjà configurées pour chaque application. Si vous disposez d'un serveur de rapports configuré pour s'exécuter en mode intégré SharePoint et que vous mettez à jour l'URL du service Web Report Server à l'aide de l'outil de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vous devez également mettre à jour l'URL dans l'Administration centrale de SharePoint.  
  
 Utilisez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour configurer les URL. Toutes les parties de l'URL sont définies dans cet outil. Contrairement aux versions précédentes, les sites Web IIS (Internet Information Services) ne fournissent plus l'accès aux applications [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les versions ultérieures.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit les valeurs par défaut qui fonctionnent bien dans la plupart des scénarios de déploiement, y compris les déploiements côte à côte avec les autres applications et services web. Les URL par défaut incorporent les noms d'instance, réduisant le risque de conflits d'URL si vous exécutez plusieurs instances de serveur de rapports sur le même ordinateur.  
  
 Cette rubrique fournit des instructions relatives aux tâches suivantes :  
  
-   Créer une URL pour le service Web Report Server.  
  
-   Créer une URL pour le Gestionnaire de rapports.  
  
-   Définir les propriétés URL avancées pour définir des URL supplémentaires.  
  
 Pour plus d’informations sur comment les URL sont stockés et gérés ou des problèmes d’interopérabilité, consultez [sur les réservations d’URL et l’inscription &#40;Gestionnaire de Configuration de SSRS&#41; ](about-url-reservations-and-registration-ssrs-configuration-manager.md) et [Install Reporting Services et Internet Information Services côte à côte &#40;SSRS en Mode natif&#41;](install-reporting-and-internet-information-services-side-by-side.md)dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne. Pour obtenir des exemples d'URL souvent utilisées dans une installation Reporting Services, consultez [Exemples d'URL](#URLExamples) dans cette rubrique.  
  
## <a name="prerequisites"></a>Prérequis  
 Avant de créer ou de modifier une URL, souvenez-vous des points suivants :  
  
-   Vous devez être membre du groupe Administrateurs local sur le serveur de rapports.  
  
-   Si IIS 6.0 ou 7.0 sont installés sur le même ordinateur, vérifiez les noms des répertoires virtuels sur les sites Web qui utilisent le port 80. Si vous consultez les répertoires virtuels qui utilisent les noms de répertoire virtuel Reporting Services par défaut (autrement dit, Reports et ReportServer), choisissez des noms de répertoire virtuel différents pour les URL [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que vous configurez.  
  
-   Vous devez utiliser l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour configurer l'URL : N'utilisez pas d'utilitaire système. Ne modifiez jamais directement les réservations d'URL dans la section `URLReservations` du fichier RSReportServer.config. L'utilisation de l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est nécessaire pour mettre à jour la réservation d'URL sous-jacente stockée en interne et pour synchroniser les paramètres URL stockés dans le fichier RSReportServer.config.  
  
-   Choisissez une heure qui présente une activité de rapport basse. À chaque modification de la réservation d'URL, vous pouvez vous attendre à ce que les domaines d'application pour le service Web Report Server et le Gestionnaire de rapports soient recyclés.  
  
-   Pour une présentation de la création et de l’utilisation des URL dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](configure-report-server-urls-ssrs-configuration-manager.md).  
  
### <a name="to-configure-a-url-for-the-report-server-web-service"></a>Pour configurer une URL pour le service Web Report Server  
  
1.  Démarrez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , puis connectez-vous à l'instance du serveur de rapports locale.  
  
2.  Cliquez sur **URL du service Web**.  
  
3.  Spécifiez le répertoire virtuel. Le nom de répertoire virtuel identifie l'application qui reçoit la demande. Comme une adresse IP et un port peuvent être partagés par plusieurs applications, le nom de répertoire virtuel spécifie quelle application reçoit la demande.  
  
     Cette valeur doit être unique pour garantir que la demande atteint sa destination prévue. Cette valeur est requise. Elle ne respecte pas la casse. Il existe une correspondance univoque entre un nom de répertoire virtuel et une instance d'une application [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Si vous créez plusieurs URL vers la même instance d'application, vous devez utiliser le même nom de répertoire virtuel dans toutes les URL que vous définissez pour cette instance d'application.  
  
     Pour le service Web Report Server, le nom du répertoire virtuel par défaut est **ReportServer**.  
  
4.  Spécifiez l'adresse IP qui identifie de façon unique le serveur de rapports sur le réseau. Si vous souhaitez spécifier un en-tête de l'hôte ou définir des URL supplémentaires pour la même instance d'application, vous devez cliquer sur **Avancé**. Pour obtenir des instructions sur la façon de définir les propriétés avancées sur l'URL, consultez les instructions plus loin dans cette rubrique. Sinon, utilisez la page **URL du service Web** pour effectuer une sélection parmi les valeurs suivantes :  
  
    -   **Assigné** spécifie que chacune des adresses IP assignées à l'ordinateur peut être utilisée dans une URL qui pointe sur une application du serveur de rapports. Cette valeur comprend également les noms d'hôte conviviaux (tels que les noms d'ordinateur) qui peuvent être résolus par un serveur de noms de domaine en une adresse IP assignée à l'ordinateur. Il s'agit de la valeur par défaut pour une URL [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
    -   **Non assigné** spécifie que le serveur de rapports reçoit une demande qui n'a pas été gérée par une autre application. Il est recommandé d'éviter cette option. Si vous sélectionnez cette option, il devient possible pour une autre application qui possède une réservation d'URL plus forte d'intercepter les demandes prévues pour le serveur de rapports.  
  
    -   **127.0.0.1** est l'adresse IPv4 utilisée pour l'accès à localhost. Cette valeur prend en charge l'administration locale sur le serveur de rapports. Si vous sélectionnez uniquement cette valeur, seuls les utilisateurs qui se connectent localement au serveur de rapports ont accès à l'application.  
  
    -   **::1** désigne l'adresse de bouclage au format IPv6.  
  
    -   Les adresses IP spécifiques apparaissent également dans cette liste. Les adresses IP peuvent être aux formats IPv4 et IPv6. *Nnn.nnn.nnn.nnn* est l’adresse IPv4 32 bits d’une carte réseau sur votre ordinateur. Les adresses IPv6 ont une taille de 128 bits et sont formées de huit champs de 4 octets séparés par le signe deux-points : <préfixe\<:*nnnn:nnnn:nnnn:nnnn:nnnn:nnnn*  
  
         Si vous avez plusieurs cartes ou si votre réseau prend en charge les adresses IPv4 et les adresses IPv6, vous visualisez plusieurs adresses IP. Si vous sélectionnez une seule adresse IP, elle limitera l'accès de l'application à la seule adresse IP (et à tout nom d'hôte qu'un serveur de noms de domaine mappe sur cette adresse). Vous ne pouvez pas utiliser localhost pour accéder à un serveur de rapports, et vous ne pouvez pas utiliser les adresses IP des autres cartes réseau installées sur le serveur de rapports. En général, si vous sélectionnez cette valeur, c'est parce que vous configurez plusieurs réservations d'URL qui spécifient aussi des adresses IP explicites ou des noms d'hôte (par exemple, un premier pour une carte réseau utilisée pour les connexions intranet et un second utilisé pour les connexions extranet).  
  
5.  Spécifiez le port. Le port 80 est le port par défaut pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] et Windows Server 2008, car il peut être partagé avec d'autres applications. Si vous souhaitez utiliser un numéro de port personnalisé, souvenez-vous que vous devrez toujours le spécifier dans l'URL utilisée pour accéder au serveur de rapports. Vous pouvez utiliser les techniques suivantes pour rechercher un port disponible :  
  
    -   À partir d'une invite de commandes, tapez la commande suivante pour retourner la liste des ports TCP utilisés :  
  
         `netstat -a -n -p tcp`  
  
    -   Lisez l’article du support Microsoft [Informations relatives aux affectations de ports TCP/IP](https://support.microsoft.com/kb/174904)pour comprendre les attributions de port TCP et les différences entre les ports bien identifiés (0 à 1023), les ports inscrits (1024 à 49151) et les ports dynamiques ou privés (49152 à 65535).  
  
    -   Si vous utilisez le Pare-feu Windows, vous devez ouvrir le port. Pour obtenir des instructions, consultez [Configure a Firewall for Report Server Access](../report-server/configure-a-firewall-for-report-server-access.md).  
  
6.  Si vous ne l'avez pas déjà fait, vérifiez qu'IIS (s'il est installé) n'a pas de répertoire virtuel ayant le même nom que celui que vous projetez d'utiliser.  
  
7.  Si vous avez installé un certificat SSL, vous pouvez le sélectionner pour lier l'URL au certificat SSL installé sur votre ordinateur.  
  
8.  Le cas échéant, si vous sélectionnez un certificat SSL, vous pouvez spécifier un port personnalisé. La valeur par défaut est 443, mais vous pouvez utiliser tout port disponible.  
  
9. Cliquez sur **Appliquer** pour créer l'URL.  
  
10. Testez l'URL en cliquant sur le lien dans la section **URL** de la page. Notez que la base de données du serveur de rapports doit être créée et configurée avant que vous puissiez tester l'URL. Pour obtenir des instructions, consultez [Créer une base de données du serveur de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
11. De plus, si votre serveur de rapports est configuré pour utiliser le mode intégré SharePoint, configurez l'URL du service Web Report Server dans l'Administration centrale de SharePoint. Pour plus d’informations sur comment mettre à jour l’URL du service Web Report Server dans l’Administration centrale de SharePoint, consultez [Configuration et Administration d’un serveur de rapports &#40;Reporting Services SharePoint Mode&#41; ](../configure-administer-report-server-reporting-services-sharepoint-mode.md) et [Reporting Services Report Server &#40;Mode SharePoint&#41;](../reporting-services-report-server-sharepoint-mode.md).  
  
### <a name="to-create-a-url-reservation-for-report-manager"></a>Pour créer une réservation d'URL pour le Gestionnaire de rapports  
  
1.  Démarrez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , puis connectez-vous à l'instance du serveur de rapports.  
  
2.  Cliquez sur **URL du Gestionnaire de rapports**.  
  
3.  Spécifiez le répertoire virtuel. Le Gestionnaire de rapports écoute sur la même adresse IP et le même port que le service Web Report Server. Si vous avez configuré le Gestionnaire de rapports pour pointer sur un service Web Report Server différent, vous devez modifier les paramètres d'URL du Gestionnaire de rapports dans le fichier RSReportServer.config. Pour obtenir des instructions, consultez [configurer le Gestionnaire de rapports &#40;en Mode natif&#41; ](../report-server/configure-web-portal.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
4.  Si vous avez installé un certificat SSL, vous pouvez le sélectionner pour exiger que toutes les demandes adressées au Gestionnaire de rapports soient acheminées via le protocole HTTPS.  
  
     Le cas échéant, si vous sélectionnez un certificat SSL, vous pouvez spécifier un port personnalisé. La valeur par défaut est 443, mais vous pouvez utiliser tout port disponible.  
  
5.  Cliquez sur **Appliquer** pour créer l'URL.  
  
6.  Testez l'URL en cliquant sur le lien dans la section **URL** de la page.  
  
## <a name="setting-advanced-properties-to-specify-additional-urls"></a>Définition de propriétés avancées pour spécifier les URL supplémentaires  
 Vous pouvez réserver plusieurs URL pour le service Web Report Server ou le Gestionnaire de rapports en spécifiant des ports ou des noms d'hôte différents (une adresse IP ou un nom d'en-tête de l'hôte qu'un serveur de noms de domaine peut résoudre en une adresse IP assignée à l'ordinateur). En créant plusieurs URL, vous pouvez définir différents chemins d'accès à la même instance de serveur de rapports. Par exemple, pour activer l'accès intranet et extranet à un serveur de rapports, vous pouvez utiliser l'URL par défaut pour l'accès intranet et un nom d'hôte complet supplémentaire pour l'accès extranet :  
  
-   http://myserver01/reportserver  
  
-   http://www.adventure-works.com/reportserver  
  
 Vous ne pouvez pas définir plusieurs noms de répertoire virtuel pour la même instance d'application. Chaque instance d'application de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est mappée sur un nom de répertoire virtuel unique. Si vous avez plusieurs instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur le même ordinateur, le nom de répertoire virtuel d'une application doit inclure le nom de l'instance pour garantir que chaque demande atteint sa cible prévue.  
  
#### <a name="to-set-advanced-properties-on-a-url"></a>Pour définir les propriétés avancées sur une URL  
  
1.  Dans l' **URL du service Web** ou sur la page **URL du Gestionnaire de rapports** , cliquez sur **Avancé**.  
  
2.  Cliquez sur **Ajouter**.  
  
3.  Cliquez sur l'adresse IP ou le nom d'en-tête de l'hôte. Si vous spécifiez un en-tête de l'hôte, veillez bien à spécifier un nom que le service DNS peut résoudre. Si vous spécifiez un nom de domaine disponible publiquement, indiquez la totalité de l’URL, y compris http://www.  
  
4.  Spécifiez le port. Si vous spécifiez un port personnalisé, l'URL de l'application doit toujours inclure le numéro de port.  
  
5.  Cliquez sur **OK**.  
  
6.  Testez l'URL en ouvrant une fenêtre de navigateur et en entrant l'URL.  
  
## <a name="urls-for-multiple-report-server-instances-on-the-same-computer"></a>URL de plusieurs instances de Report Server sur le même ordinateur  
 Si vous réservez les URL pour plusieurs instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous devez suivre les conventions d'affectation de noms afin d'éviter les conflits de noms. Pour plus d’informations, consultez [Réservations d’URL pour les déploiements de serveur de rapports multi-instance &#40;Gestionnaire de configuration de SSRS&#41;](url-reservations-for-multi-instance-report-server-deployments.md).  
  
##  <a name="URLExamples"></a> Exemples de configurations d'URL  
 La liste suivante présente quelques exemples d'URL de serveur de rapports :  
  
-   http://localhost/reportserver  
  
-   http://localhost/reportserver_SQLEXPRESS  
  
-   http://sales01/reportserver  
  
-   http://sales01:8080/reportserver  
  
-   https://sales.adventure-works.com/reportserver  
  
-   https://www.adventure-works.com:8080/reportserver01  
  
 Les URL que vous utilisez pour accéder au Gestionnaire de rapports partagent le même format et sont généralement créées sous le site Web qui héberge le serveur de rapports. La seule différence est le nom du répertoire virtuel (dans ce cas, le nom est **rapports** , mais vous pouvez configurer le répertoire virtuel pour qu’il utilise le nom de votre choix) :  
  
-   http://localhost/reports  
  
-   http://localhost/reports_SQLEXPRESS  
  
-   http://sales01/reports  
  
-   http://sales01:8080/reports  
  
-   https://sales.adventure-works.com/reports  
  
-   https://www.adventure-works.com:8080/reports  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
