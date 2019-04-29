---
title: Configurer un pare-feu pour accéder au serveur de rapports | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [Reporting Services]
- configuring servers [Reporting Services]
ms.assetid: 04dae07a-a3a4-424c-9bcb-a8000e20dc93
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a8c43d75b0b070a73f89a16300694fc11234d6a7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63017087"
---
# <a name="configure-a-firewall-for-report-server-access"></a>Configurer un pare-feu pour accéder au serveur de rapports
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Applications du serveur de rapports et les rapports publiés sont accessibles via les URL qui spécifient une adresse IP, le port et le répertoire virtuel. Si Windows Firewall est activé, le port que le serveur de rapports est configuré pour utiliser est très probablement fermé. Indications qu’un port peut être fermé sont l’apparence d’une page Web vierge après la demande d’un rapport ou une page vierge lorsque vous essayez d’ouvrir le Gestionnaire de rapports à partir d’un ordinateur client distant.  
  
 Pour ouvrir un port, vous devez utiliser l’utilitaire de pare-feu de Windows sur l’ordinateur de serveur de rapports. Reporting Services s’ouvre pas de ports pour vous ; Vous devez effectuer cette étape manuellement.  
  
 Par défaut, le serveur de rapports écoute les requêtes HTTP sur le port 80. Par conséquent, les instructions suivantes incluent des étapes qui spécifient ce port. Si vous avez configuré les URL de serveur de rapports pour utiliser un port différent, vous devez spécifier ce numéro de port lorsque vous suivez les instructions ci-dessous.  
  
 Si vous accédez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des bases de données relationnelles sur des ordinateurs externes, ou si la base de données de serveur de rapports se trouve sur un externe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, vous devez ouvrir les ports 1433 et 1434 sur l’ordinateur externe. Pour plus d’informations, consultez [configurer un pare-feu Windows pour accéder au moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne. Pour plus d’informations sur les paramètres du pare-feu Windows par défaut et une description de TCP ports qui affectent le [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], et [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [configurer le pare-feu Windows pour permettre à SQL Server Accès](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="prerequisites"></a>Prérequis  
 Ces instructions supposent que vous déjà configuré le compte de service et créé la base de données de serveur de rapports et configurez les URL pour le service Web Report Server et Gestionnaire de rapports. Pour plus d’informations, consultez [gérer un Reporting Services en Mode serveur de rapports natif](manage-a-reporting-services-native-mode-report-server.md).  
  
 Vous devez aussi avoir vérifié que le serveur de rapports est accessible via une connexion de navigateur Web locale à l’instance de serveur de rapports local. Cette étape établit que vous disposez d’une installation de travail. Vous devez vérifier que l’installation est correctement configurée avant de commencer l’ouverture des ports. Pour compléter cette étape sur Windows Server, vous devez également avoir ajouté le site du serveur de rapports aux Sites de confiance. Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="opening-ports-in-windows-firewall"></a>Ouverture des ports dans le Pare-feu Windows  
 Il existe des instructions distinctes pour les différentes versions du pare-feu de Windows.  
  
#### <a name="to-open-port-80-on-windows-7-windows-server-2008-r2-windows-server-2012-and-2012-r2"></a>Pour ouvrir le port 80 sur Windows 7, Windows Server 2008 R2, Windows Server 2012 et 2012 R2  
  
1.  À partir de la **Démarrer** menu, cliquez sur **le panneau de configuration**, cliquez sur **système et sécurité**, puis cliquez sur **Windows Firewall**. Le panneau de configuration n’est pas configuré pour l’affichage de « Catégorie », vous devez uniquement sélectionner **pare-feu de Windows.**  
  
2.  Cliquez sur **paramètres avancés**.  
  
3.  Cliquez sur **Règles de trafic entrant**.  
  
4.  Cliquez sur **Nouvelle règle** dans la fenêtre **Actions****.**  
  
5.  Cliquez sur **Type de règle** de **Port**.  
  
6.  Cliquez sur **Suivant**.  
  
7.  Sur le **protocole et Ports** page, cliquez sur **TCP**.  
  
8.  Sélectionnez **Ports locaux spécifiques** et tapez la valeur **80**.  
  
9. Cliquez sur **Suivant**.  
  
10. Sur le **Action** page, cliquez sur **autoriser la connexion**.  
  
11. Cliquez sur **Suivant**.  
  
12. Sur le **profil** page, cliquez sur les options appropriées pour votre environnement.  
  
13. Cliquez sur **Suivant**.  
  
14. Sur le **nom** page Entrez un nom de**ReportServer (TCP sur le port 80)**  
  
15. Cliquez sur **Terminer**.  
  
16. Redémarrez l'ordinateur.  
  
#### <a name="to-open-port-80-on-windows-vista-or-windows-server-2008"></a>Pour ouvrir le port 80 sur Windows Vista ou Windows Server 2008  
  
1.  À partir de la **Démarrer** menu, cliquez sur **le panneau de configuration**, cliquez sur **sécurité**, puis cliquez sur **Windows Firewall**.  
  
2.  Cliquez sur **autoriser un programme via le pare-feu de Windows**.  
  
3.  Cliquez sur **Continuer**.  
  
4.  Sous l’onglet Exceptions, cliquez sur **ajouter un Port**.  
  
5.  Dans nom, tapez **ReportServer (TCP sur le port 80)**.  
  
6.  Dans le numéro de Port, tapez **80**.  
  
7.  Vérifiez que **TCP** est sélectionné.  
  
8.  Cliquez sur **modifier l’étendue**.  
  
9. Cliquez sur **uniquement mon réseau (sous-réseau)**, puis cliquez sur **OK**.  
  
10. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
11. Redémarrez l'ordinateur.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Après avoir ouvert le port et avant de confirmer si les utilisateurs distants peuvent accéder au serveur de rapports sur le port que vous ouvrez, vous devez accorder l’accès utilisateur au serveur de rapports via les attributions de rôle sur l’accueil et au niveau du site. Vous pouvez ouvrir un port correctement et ont toujours des connexions de serveur de rapports échouer si les utilisateurs n’ont pas d’autorisations suffisantes. Pour plus d’informations, consultez [accorder l’accès utilisateur à un serveur de rapports &#40;le Gestionnaire de rapports&#41; ](../security/grant-user-access-to-a-report-server.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
 Vous pouvez également vérifier que le port est ouvert correctement en démarrant le Gestionnaire de rapports sur un autre ordinateur. Pour plus d’informations, consultez [le Gestionnaire de rapports &#40;SSRS en Mode natif&#41; ](../report-manager-ssrs-native-mode.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le compte de Service Report Server &#40;Gestionnaire de Configuration de SSRS&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Configurer des URL de serveur de rapports &#40;Gestionnaire de Configuration de SSRS&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Créer une base de données de serveur de rapports &#40;Gestionnaire de Configuration de SSRS&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)   
 [Configurer le compte de Service Report Server &#40;Gestionnaire de Configuration de SSRS&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Gérer un serveur de rapports Reporting Services en Mode natif](manage-a-reporting-services-native-mode-report-server.md)  
  
  
