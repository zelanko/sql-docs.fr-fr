---
title: Configurer un serveur de rapports (mode natif de Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report server configuration
- report servers [Reporting Services], configuring
ms.assetid: ef84ce9d-9156-48e9-8073-7e0535476932
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 10e4a4befd8300863d8637a87e8c9bd03622d0af
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66104067"
---
# <a name="configure-a-report-server-reporting-services-native-mode"></a>Configurer un serveur de rapports (mode natif de Reporting Services)
  Selon les options que vous avez sélectionnées pendant l'installation, le serveur de rapports peut requérir une configuration supplémentaire avant de pouvoir fonctionner. Dans sa configuration minimale, un serveur de rapports se compose des éléments suivants :  
  
-   Un compte de service Report Server (configuré au cours de l'installation).  
  
-   Un URL du service Web qui permet d'accéder au serveur de rapports.  
  
-   Une base de données du serveur de rapports qui stocke des données d'application, des rapports et d'autres éléments.  
  
 Le programme d’installation configure les paramètres minimum si vous sélectionnez une des options d’installation suivantes : Configuration par défaut du mode natif ou configuration par défaut de mode intégré SharePoint. Si vous avez installé le serveur de rapports en mode de fichiers uniquement (option **Installer mais ne pas configurer** dans l’Assistant Installation), seul le compte de service est configuré. L'URL du service Web et la base de données du serveur de rapports doivent être configurés à l'issue de l'installation.  
  
 Le Gestionnaire de rapports est une fonctionnalité en option pour un serveur de rapports en mode natif, mais il vous est recommandé de configurer le Gestionnaire de rapports pour vous permettre d'accorder à l'utilisateur l'accès au serveur de rapports et gérer le contenu de ce serveur. Si vous déployez un serveur de rapports en mode intégré SharePoint, utilisez le frontal Web d'un serveur SharePoint pour accorder l'accès.  
  
 Des fonctionnalités supplémentaires, telles que la messagerie électronique de serveur de rapports et le compte d'exécution sans assistance, peuvent être configurées si nécessaire. Pour plus d’informations, consultez [Gérer un serveur de rapports Reporting Services (SSRS) en mode natif](manage-a-reporting-services-native-mode-report-server.md).  
  
 Pour configurer un serveur de rapports, utilisez l'outil de configuration de Reporting Services.  
  
### <a name="to-minimally-configure-a-report-server-installation"></a>Pour installer la configuration minimale d'un serveur de rapports  
  
1.  Démarrez le Gestionnaire de configuration de Reporting Services, puis connectez-vous à l'instance du serveur de rapports. Pour obtenir des instructions, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
2.  Cliquez sur **URL du service Web** pour ouvrir la page de configuration d'une URL pour le serveur de rapports. Pour obtenir des instructions sur la définition de l’URL, consultez [Configurer une URL &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md).  
  
3.  Cliquez sur **Base de données** pour créer la base de données du serveur de rapports. Pour obtenir des instructions, consultez [Créer une base de données du serveur de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
4.  Revenez à la page **URL du service Web** et cliquez sur l'URL pour vérifier son fonctionnement.  
  
5.  Suivez les instructions dans « Étapes suivantes » pour achever votre déploiement.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour achever votre déploiement, vous devez configurer le Gestionnaire de rapports ou l'intégration SharePoint. Pour plus d’informations, consultez [Configurer le Gestionnaire de rapports &#40;mode natif&#41;](configure-web-portal.md).  
  
 Si le Pare-feu Windows est activé, le port que le serveur de rapports est configuré pour utiliser est très probablement fermé. Un port peut être fermé si une page vide apparaît lorsque vous essayez d'ouvrir le Gestionnaire de rapports à partir d'un ordinateur client distant. Pour plus d'informations sur la configuration du pare-feu, consultez [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).  
  
 Si vous utilisez Windows Vista ou Windows Server 2008, des étapes supplémentaires peuvent être requises avant d'ouvrir le Gestionnaire de rapports en local. Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
 Vérifiez votre installation en créant des dossiers, en téléchargeant des éléments, et en exécutant des rapports. Suivez les instructions de la rubrique [Vérifier une installation de Reporting Services](../install-windows/verify-a-reporting-services-installation.md) pour vérifier votre installation.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer un serveur de rapports Reporting Services (SSRS) en mode natif](manage-a-reporting-services-native-mode-report-server.md)   
 [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md)   
 [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md)   
 [Configurer un serveur de rapports pour l'administration à distance](configure-a-report-server-for-remote-administration.md)   
 [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
