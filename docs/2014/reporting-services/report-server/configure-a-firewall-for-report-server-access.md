---
title: Configurer un pare-feu pour accéder au serveur de rapports | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [Reporting Services]
- configuring servers [Reporting Services]
ms.assetid: 04dae07a-a3a4-424c-9bcb-a8000e20dc93
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 00590faa3ef5fb63338465d85202f4010cd3b72d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66104161"
---
# <a name="configure-a-firewall-for-report-server-access"></a>Configurer un pare-feu pour accéder au serveur de rapports
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et les rapports publiés sont accessibles via les URL qui spécifient une adresse IP, un port et un répertoire virtuel. Si le Pare-feu Windows est activé, le port que le serveur de rapports est configuré pour utiliser est très probablement fermé. La présence d'une page Web vierge après la demande d'un rapport ou l'affichage d'une page vierge lorsque vous tentez d'ouvrir le Gestionnaire de rapports à partir d'un ordinateur client distant constituent une indication qu'un port peut être fermé.  
  
 Pour ouvrir un port, vous devez utiliser le Pare-feu Windows sur le serveur de rapports. Reporting Services n'ouvrent pas de ports automatiquement ; vous devez effectuer cette étape manuellement.  
  
 Par défaut, le serveur de rapports écoute les requêtes HTTP sur le port 80. De ce fait, les instructions suivantes incluent les étapes qui spécifient ce port. Si vous avez configuré les URL du serveur de rapports pour utiliser un autre port, vous devez spécifier ce numéro de port lors des instructions ci-après.  
  
 Si vous accédez à des bases de données relationnelles [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur des ordinateurs externes, ou si la base de données du serveur de rapports se trouve sur une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] externe, vous devez ouvrir les ports 1433 et 1434 sur l'ordinateur externe. Pour plus d’informations, consultez [Configurer un pare-feu Windows pour accéder au moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations sur les paramètres par défaut du Pare-feu Windows et pour obtenir une description des ports TCP qui affectent le [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]et [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Ces instructions supposent que vous avez déjà configuré le compte de service, créé la base de données du serveur de rapports et configuré les URLS du service Web Report Server et du Gestionnaire de rapports. Pour plus d’informations, consultez [Gérer un serveur de rapports Reporting Services (SSRS) en mode natif](manage-a-reporting-services-native-mode-report-server.md).  
  
 Vous devez aussi avoir vérifié que le serveur de rapports est accessible via une connexion locale du navigateur Web à l'instance locale du serveur de rapports. Cette étape établit que votre installation est en état de marche. Vous devez vérifier que l'installation est configurée correctement avant de commencer à ouvrir les ports. Pour compléter cette étape sur Windows Server, vous devez également avoir ajouté le site du serveur de rapports aux Sites de confiance. Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="opening-ports-in-windows-firewall"></a>Ouverture des ports dans le Pare-feu Windows  
 Il existe des instructions distinctes selon les différentes versions du Pare-feu Windows.  
  
#### <a name="to-open-port-80-on-windows-7-windows-server-2008-r2-windows-server-2012-and-2012-r2"></a>Pour ouvrir le port 80 sur Windows 7, Windows Server 2008 R2, Windows Server 2012 et Windows Server 2012 R2  
  
1.  Dans le menu **Démarrer** , cliquez sur **Panneau de configuration**, cliquez sur **Système et sécurité**, puis sur **Pare-feu Windows**. Le Panneau de configuration n'est pas configuré pour l'affichage de « Catégorie », vous devez seulement sélectionner le **Pare-feu Windows**.  
  
2.  Cliquez sur **Paramètres avancés**.  
  
3.  Cliquez sur **Règles de trafic entrant**.  
  
4.  Cliquez sur **nouvelle règle** dans la fenêtre **actions** **.**  
  
5.  Cliquez sur **Type de règle** de **Port**.  
  
6.  Cliquez sur **Suivant**.  
  
7.  Dans la page **Protocole et ports** , cliquez sur **TCP**.  
  
8.  Sélectionnez **Ports locaux spécifiques** et tapez la valeur **80**.  
  
9. Cliquez sur **Suivant**.  
  
10. Dans la page **Action** , cliquez sur **Autoriser la connexion**.  
  
11. Cliquez sur **Suivant**.  
  
12. Dans la page **Profil** , cliquez sur les options appropriées pour votre environnement.  
  
13. Cliquez sur **Suivant**.  
  
14. Dans la page **Nom** , entrez un nom de**ReportServer (TCP sur le port 80)** .  
  
15. Cliquez sur **Terminer**.  
  
16. Redémarrez l'ordinateur.  
  
#### <a name="to-open-port-80-on-windows-vista-or-windows-server-2008"></a>Pour ouvrir le port 80 sur Windows Vista ou Windows Server 2008  
  
1.  Dans le menu **Démarrer** , cliquez sur **panneau de configuration**, sur **sécurité**, puis sur **pare-feu Windows**.  
  
2.  Cliquez sur **Autoriser un programme via le Pare-feu Windows**.  
  
3.  Cliquez sur **Continuer**.  
  
4.  Sous l’onglet exceptions, cliquez sur **Ajouter un port**.  
  
5.  Dans nom, tapez **reportserver (TCP sur le port 80)**.  
  
6.  Dans numéro de port, tapez **80**.  
  
7.  Vérifiez que **TCP** est sélectionné.  
  
8.  Cliquez sur **Modifier l'étendue**.  
  
9. Cliquez sur **mon réseau (sous-réseau) uniquement**, puis sur **OK**.  
  
10. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
11. Redémarrez l'ordinateur.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Après avoir ouvert le port et avant de confirmer si les utilisateurs distants peuvent accéder au serveur de rapports sur le port que vous ouvrez, vous devez accorder l'accès utilisateur au serveur de rapports à travers les attributions de rôle sur la page d'Accueil et au niveau du site. Vous pouvez ouvrir un port correctement et que les connexions du serveur de rapports échouent si les utilisateurs n'ont pas les autorisations suffisantes. Pour plus d’informations, consultez [Accorder à un utilisateur l’accès à un serveur de rapports &#40;Gestionnaire de rapports&#41;](../security/grant-user-access-to-a-report-server.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Vous pouvez également vérifier que le port est ouvert correctement en démarrant le Gestionnaire de rapports sur un autre ordinateur. Pour plus d’informations, consultez [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le compte de service Report Server &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Créer une base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)   
 [Configurer le compte de service Report Server &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Gérer un serveur de rapports Reporting Services en mode natif](manage-a-reporting-services-native-mode-report-server.md)  
  
  
