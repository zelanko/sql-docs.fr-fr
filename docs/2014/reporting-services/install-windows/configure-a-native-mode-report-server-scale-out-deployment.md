---
title: Configurer un déploiement de montée en puissance de serveurs de rapports en Mode natif (Gestionnaire de Configuration de SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], deployments
- deploying [Reporting Services], scale-out deployment model
- scale-out deployments [Reporting Services]
ms.assetid: b30d0308-4d9b-4f85-9f83-dece4dcb2775
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0281a487de123adfeb3739066628694b1da17a3
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66108897"
---
# <a name="configure-a-native-mode-report-server-scale-out-deployment-ssrs-configuration-manager"></a>Configurer un déploiement par montée en puissance parallèle de serveurs de rapports en mode natif (Gestionnaire de configuration de SSRS)

  Le mode natif de Reporting Services prend en charge un modèle de déploiement par montée en puissance parallèle qui vous permet d'exécuter plusieurs instances de serveur de rapports partageant une base de données du serveur de rapports unique. Les déploiements avec montée en puissance parallèle sont utilisés pour augmenter l'évolutivité des serveurs de rapports afin de gérer davantage d'utilisateurs simultanés et de plus grandes charges d'exécution de rapport. Ils peuvent également être utilisés pour dédier des serveurs spécifiques au traitement des rapports interactifs ou planifiés.  
  
 Les serveurs de rapports en mode SharePoint utilisent l'infrastructure de produits SharePoint pour la montée en puissance parallèle. La montée en puissance parallèle en mode SharePoint est effectuée en ajoutant des serveurs de rapports en mode SharePoint à la batterie de serveurs SharePoint. Pour plus d’informations sur la montée en puissance parallèle en mode SharePoint, consultez [Ajouter un serveur de rapports supplémentaires à une batterie de serveurs &#40;SSRS Scale-out&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md).  
  
 **Les déploiements avec montée en puissance parallèle sont constitués de :**  
  
-   Plusieurs instances de serveurs de rapports qui partagent une base de données de serveur de rapports unique.  
  
-   Éventuellement, un cluster à charge réseau équilibrée pour répartir la charge utilisateur interactive parmi les instances de serveurs de rapports.  
  
 Lorsque vous déployez Reporting Services sur un cluster à équilibrage de la charge réseau, vous devez vous assurer que le nom du serveur virtuel d'équilibrage de la charge réseau est utilisé dans la configuration des URL de serveurs de rapports et que les serveurs sont configurés pour partager le même état d'affichage.  
  
 Reporting Services ne participe pas aux clusters Microsoft Cluster Services. Toutefois, vous pouvez créer la base de données du serveur de rapports sur une instance de Moteur de base de données qui fait partie d'un cluster de basculement.  
  
 **Pour planifier, installer et configurer un déploiement avec montée en puissance parallèle, suivez ces étapes :**  
  
-   Révision [installer SQL Server 2014 à partir de l’Assistant Installation &#40;le programme d’installation&#41; ](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne pour obtenir des instructions sur l’installation des instances de serveur de rapports.  
  
-   Si vous prévoyez d'héberger le déploiement avec montée en puissance parallèle sur un cluster à charge réseau équilibrée, vous devez configurer le cluster avant de configurer le déploiement avec montée en puissance parallèle. Pour plus d’informations, consultez [Configurer un serveur de rapports sur un cluster avec équilibrage de la charge réseau](../report-server/configure-a-report-server-on-a-network-load-balancing-cluster.md).  
  
-   Consultez les procédures dans cette rubrique pour obtenir des instructions sur le partage d'une base de données du serveur de rapports et la jointure des serveurs de rapports avec montée en puissance parallèle.  
  
     Les procédures suivantes expliquent comment configurer un déploiement avec montée en puissance parallèle d'un serveur de rapports à deux nœuds. Répétez les étapes décrites dans cette rubrique pour ajouter des nœuds de serveur de rapports supplémentaires au déploiement.  
  
    -   Utilisez le programme d'installation pour installer chaque instance de serveur de rapports qui sera jointe au déploiement avec montée en puissance parallèle.  
  
         Pour éviter des erreurs de compatibilité de base de données lorsque vous connectez les instances du serveur à la base de données partagée, assurez-vous que toutes les instances soient de la même version. Par exemple, si vous créez la base de données du serveur de rapports à l'aide d'une instance du serveur de rapports [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , l'édition de toutes les autres instances du même déploiement doit également être [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    -   Utilisez le gestionnaire de configuration de Reporting Services pour connecter chaque serveur de rapports à la base de données partagée. Vous ne pouvez connecter et configurer qu'un seul serveur de rapports à la fois.  
  
    -   Utilisez l'outil de configuration de Reporting Services pour procéder au déploiement avec montée en puissance parallèle en joignant de nouvelles instances de serveur de rapports à la première instance déjà connectée à la base de données de serveur de rapports.  
  
### <a name="to-install-a-sql-server-instance-to-host-the-report-server-databases"></a>Pour installer une instance de SQL Server en vue d'héberger les bases de données du serveur de rapports  
  
1.  Installez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur qui hébergera les bases de données du serveur de rapports. Au minimum, installez [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
2.  Si nécessaire, activez le serveur de rapports pour les connexions distantes. Certaines versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'autorisent pas les connexions TCP/IP et Canaux nommés distantes par défaut. Pour déterminer si les connexions distantes sont autorisées ou non, utilisez l'outil Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et vérifiez les paramètres de configuration réseau de l'instance cible. Si l'instance distante est également une instance nommée, vérifiez que le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser est activé et en cours d'exécution sur le serveur cible. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser fournit le numéro de port utilisé pour se connecter à l’instance nommée.  
  
### <a name="to-install-the-first-report-server-instance"></a>Pour installer la première instance du serveur de rapports  
  
1.  Installez la première instance du serveur de rapports faisant partie du déploiement. Quand vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], choisissez l’option **Installer mais ne pas configurer le serveur** dans la page Options d’installation du serveur de rapports.  
  
2.  Démarrez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
3.  Configurez l'URL de service Web Report Server, l'URL du Gestionnaire de rapports et la base de données du serveur de rapports. Pour plus d’informations, consultez [Configurer un serveur de rapports &#40;mode natif de Reporting Services&#41;](../report-server/configure-a-report-server-reporting-services-native-mode.md) dans la documentation en ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
4.  Vérifiez le fonctionnement du serveur de rapports. Pour plus d’informations, consultez [Vérifier une installation de Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md) dans la documentation en ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="to-install-and-configure-the-second-report-server-instance"></a>Pour installer et configurer la deuxième instance du serveur de rapports  
  
1.  Exécutez le programme d'installation pour installer une deuxième instance de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur un ordinateur différent ou comme instance nommée sur le même ordinateur. Quand vous installez Reporting Services, choisissez l’option **Installer mais ne pas configurer le serveur** dans la page Options d’installation du serveur de rapports.  
  
2.  Démarrez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et connectez-vous à la nouvelle instance que vous venez d'installer.  
  
3.  Connectez le serveur de rapports à la même base de données que celle utilisée pour la première instance de serveur de rapports.  
  
    1.  Cliquez sur **base de données** pour ouvrir la page de base de données.  
  
    2.  Cliquez sur **Modifier la base de données**.  
  
    3.  Cliquez sur **Choisir une base de données de serveur de rapports existante**.  
  
    4.  Tapez le nom de serveur de l'instance du moteur de base de données SQL Server qui héberge la base de données du serveur de rapports que vous voulez utiliser. Vous devez spécifier le serveur auquel vous vous êtes connecté lors de la procédure précédente.  
  
    5.  Cliquez sur **tester la connexion**, puis cliquez sur **suivant**.  
  
    6.  Dans **base de données du serveur de rapports**, sélectionnez la base de données que vous avez créé pour le premier serveur de rapports, puis cliquez sur **suivant**. Le nom par défaut est ReportServer. Ne sélectionnez pas ReportServerTempDB ; il est utilisé uniquement pour stocker les données temporaires lors du traitement des rapports. Si la liste de bases de données est vide, répétez les quatre étapes précédentes pour établir une connexion au serveur.  
  
    7.  Dans la page Informations d'identification, sélectionnez le type de compte et les informations d'identification que le serveur de rapports utilisera pour se connecter à la base de données du serveur de rapports. Vous pouvez utiliser les mêmes informations d'identification que la première instance du serveur de rapports, ou des informations d'identification différentes. Cliquer sur **Suivant**.  
  
    8.  Cliquez sur **Résumé** puis cliquez sur **Terminer**.  
  
4.  Configurez l'URL du service Web Report Server. Ne testez pas encore l'URL. Elle ne sera pas résolue tant que le serveur de rapports est joint au déploiement avec montée en puissance parallèle.  
  
5.  Configurez l'URL du Gestionnaire de rapports. Ne testez pas encore l'URL ou essayez de vérifier le déploiement. Le serveur de rapports ne sera pas disponible tant que le serveur de rapports n'est pas joint au déploiement avec montée en puissance parallèle.  
  
### <a name="to-join-the-second-report-server-instance-to-the-scale-out-deployment"></a>Pour joindre la deuxième instance de serveur de rapports au déploiement avec montée en puissance parallèle  
  
1.  Ouvrez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , puis reconnectez-vous à la première instance du serveur de rapports. Le premier serveur de rapports étant déjà initialisé pour les opérations de chiffrement réversible ; il est utilisé pour joindre de nouvelles instances du serveur de rapports au déploiement avec montée en puissance parallèle.  
  
2.  Cliquez sur **Déploiement avec montée en puissance parallèle** pour ouvrir la page du même nom. Vous devez voir deux entrées, l'une pour chaque instance de serveur de rapports connectée à la base de données du serveur de rapports. La première instance de serveur de rapports doit être jointe. Le deuxième serveur de rapports doit être en attente de rattachement. Si vous ne voyez pas de telles entrées pour votre déploiement, vérifiez que vous êtes connecté au premier serveur de rapports qui est déjà configuré et initialisé pour utiliser la base de données du serveur de rapports.  
  
     ![Capture d’écran partielle de la page de déploiement avec montée en puissance parallèle](../../../2014/sql-server/install/media/scaloutscreen.gif "Capture d’écran partielle de la page de déploiement avec montée en puissance parallèle")  
  
3.  Sur la page déploiement avec montée en puissance, sélectionnez l’instance de serveur de rapports qui est en attente de joindre le déploiement, puis cliquez sur **ajouter un serveur**.  
  
    > [!NOTE]  
    >  **Problème :** Lorsque vous tentez de joindre une instance de serveur de rapports Reporting Services au déploiement avec montée en puissance, vous pouvez rencontrer des messages d’erreur semblables à « Accès refusé ».  
    >   
    >  **Solution de contournement :** Sauvegarder le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] clé de chiffrement à partir de la première [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] d’instance et restaurer la clé à la seconde [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] serveur de rapports. Puis, essayez de joindre le second serveur au déploiement avec montée en puissance parallèle de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
4.  Vous devez maintenant être en mesure de vérifier que les deux instances de serveur de rapports sont opérationnelles. Pour vérifier la deuxième instance, vous pouvez utiliser l'outil de configuration de Reporting Services pour vous connecter au serveur de rapports et cliquer sur l'URL du service Web ou l'URL du Gestionnaire de rapports.  
  
 Si vous envisagez d'exécuter les serveurs de rapports dans un cluster de serveurs avec équilibrage de charge, une configuration supplémentaire est requise. Pour plus d’informations, consultez [Configurer un serveur de rapports sur un cluster avec équilibrage de la charge réseau](../report-server/configure-a-report-server-on-a-network-load-balancing-cluster.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un compte de service &#40;Gestionnaire de configuration de SSR&#41;](../../../2014/sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)   
 [Configurer une URL &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [Créer une base de données du serveur de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Configurer une connexion à la base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Ajouter et supprimer des clés de chiffrement pour un déploiement évolutif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md)   
 [Gérer un serveur de rapports Reporting Services en mode natif](../report-server/manage-a-reporting-services-native-mode-report-server.md)  
  
  
