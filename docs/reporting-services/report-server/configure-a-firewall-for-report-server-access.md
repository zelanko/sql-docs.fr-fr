---
title: Configurer un pare-feu pour accéder au serveur de rapports | Microsoft Docs
description: Découvrez comment configurer le Pare-feu Windows pour autoriser l’accès aux rapports publiés et aux applications Report Server accessibles via des URL.
ms.date: 05/14/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [Reporting Services]
- configuring servers [Reporting Services]
ms.assetid: 04dae07a-a3a4-424c-9bcb-a8000e20dc93
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 08a80c8307d551813a30becbed6d12507e6b2947
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545583"
---
# <a name="configure-a-firewall-for-report-server-access"></a>Configurer un pare-feu pour accéder au serveur de rapports
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et les rapports publiés sont accessibles via les URL qui spécifient une adresse IP, un port et un répertoire virtuel. Si le Pare-feu Windows est activé, le port que le serveur de rapports est configuré pour utiliser est très probablement fermé. Un port peut être fermé si une page vierge s’affiche quand vous tentez d’ouvrir le portail web à partir d’un ordinateur client distant ou si une page web vierge apparaît après la demande d’un rapport.  
  
 Pour ouvrir un port, vous devez utiliser le Pare-feu Windows sur le serveur de rapports. Reporting Services n'ouvrent pas de ports automatiquement ; vous devez effectuer cette étape manuellement.  
  
 Par défaut, le serveur de rapports écoute les requêtes HTTP sur le port 80. De ce fait, les instructions suivantes incluent les étapes qui spécifient ce port. Si vous avez configuré les URL du serveur de rapports pour utiliser un autre port, vous devez spécifier ce numéro de port lors des instructions ci-après.  
  
 Si vous accédez à des bases de données relationnelles [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur des ordinateurs externes, ou si la base de données du serveur de rapports se trouve sur une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] externe, vous devez ouvrir les ports 1433 et 1434 sur l'ordinateur externe. Pour plus d’informations, consultez [Configurer un pare-feu Windows pour accéder au moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md). Pour plus d’informations sur les paramètres par défaut du Pare-feu Windows et pour obtenir une description des ports TCP qui affectent le [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]et [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Ces instructions supposent que vous avez déjà configuré le compte de service, créé la base de données du serveur de rapports et configuré les URLS du service Web Report Server et le portail web. Pour plus d’informations, consultez [Gérer un serveur de rapports Reporting Services (SSRS) en mode natif](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md).  
  
 Vous devez aussi avoir vérifié que le serveur de rapports est accessible via une connexion locale du navigateur Web à l'instance locale du serveur de rapports. Cette étape établit que votre installation est en état de marche. Vous devez vérifier que l'installation est configurée correctement avant de commencer à ouvrir les ports. Pour compléter cette étape sur Windows Server, vous devez également avoir ajouté le site du serveur de rapports aux Sites de confiance. Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="opening-ports-in-windows-firewall"></a>Ouverture des ports dans le Pare-feu Windows  
  
#### <a name="to-open-port-80"></a>Pour ouvrir le port 80  
  
1.  Dans le menu **Démarrer** , cliquez sur **Panneau de configuration**, cliquez sur **Système et sécurité**, puis sur **Pare-feu Windows**. Le Panneau de configuration n'est pas configuré pour l'affichage de « Catégorie », vous devez seulement sélectionner le **Pare-feu Windows**.  
  
2.  Cliquez sur **Paramètres avancés**.  
  
3.  Cliquez sur **Règles de trafic entrant**.  
  
4.  Cliquez sur **Nouvelle règle** dans la fenêtre **Actions**.  
  
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
  
## <a name="next-steps"></a>Étapes suivantes  
 Après avoir ouvert le port et avant de confirmer si les utilisateurs distants peuvent accéder au serveur de rapports sur le port que vous ouvrez, vous devez accorder l'accès utilisateur au serveur de rapports à travers les attributions de rôle sur la page d'Accueil et au niveau du site. Vous pouvez ouvrir un port correctement et que les connexions du serveur de rapports échouent si les utilisateurs n'ont pas les autorisations suffisantes. Pour plus d’informations, consultez [Accorder à un utilisateur l’accès à un serveur de rapports](../../reporting-services/security/grant-user-access-to-a-report-server.md).  
  
 Vous pouvez également vérifier que le port est ouvert correctement en démarrant le portail web sur un autre ordinateur. Pour plus d’informations, consultez [Le portail web d’un serveur de rapports](../../reporting-services/web-portal-ssrs-native-mode.md).
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le compte de service Report Server &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Créer une base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-report-server-database.md)   
 [Configurer le compte de service Report Server &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Gérer un serveur de rapports Reporting Services en mode natif](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)  
  
  
