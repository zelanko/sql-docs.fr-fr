---
title: Gérer un serveur de rapports Reporting Services (SSRS) en mode natif | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- configuration options [Reporting Services]
- report servers [Reporting Services], configuring
ms.assetid: 6ca03a09-d6a8-4c93-ba12-1c99dcbfb618
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2c6190ec6494e5a723aa449c5d4053c12979076c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48206109"
---
# <a name="manage-a-reporting-services-native-mode-report-server"></a>Gérer un serveur de rapports Reporting Services (SSRS) en mode natif
  Cette section contient des procédures qui indiquent comment configurer une instance de serveur de rapports en mode natif à l'aide du Gestionnaire de configuration de Reporting Services.  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques de cette section sont organisées en catégories afin que vous puissiez rechercher plus aisément les instructions que vous souhaitez. La première section contient les rubriques pour les tâches de configuration de base pour un serveur de rapports en mode natif. La deuxième section contient les rubriques de configuration avancées. La troisième section contient les rubriques pour configurer un serveur de rapports afin qu'il s'exécute en mode intégré SharePoint.  
  
### <a name="basic-configuration"></a>Configuration de base  
 [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
 Indique la procédure à suivre pour démarrer l'outil de configuration de Reporting Services.  
  
 [Configurer un compte de Service &#40;Gestionnaire de Configuration de SSRS&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)  
 Explique comment spécifier des informations de compte et de mot de passe pour le service Web Report Server.  
  
 [Inscrire un nom de principal du Service &#40;SPN&#41; pour un serveur de rapports](register-a-service-principal-name-spn-for-a-report-server.md)  
 Explique comment enregistrer manuellement un SPN pour un serveur de rapports qui s'exécute sous un compte d'utilisateur de domaine sur un réseau qui utilise l'authentification Kerberos.  
  
 [Configurer une URL &#40;Gestionnaire de Configuration de SSRS&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md)  
 Explique comment établir une ou plusieurs URL utilisées pour accéder au service Web Report Server et au Gestionnaire de rapports.  
  
 [Créer une base de données du serveur de rapports en Mode natif &#40;Gestionnaire de Configuration de SSRS&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)  
 Indique la procédure à suivre pour créer une base de données du serveur de rapports. Cette étape est nécessaire pour déployer une installation de Reporting Services.  
  
### <a name="advanced-or-optional-configuration"></a>Configuration avancée ou facultative  
 [Configurer un déploiement évolutif de serveurs de rapports en Mode natif &#40;Gestionnaire de Configuration de SSRS&#41;](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
 Indique la procédure à suivre pour configurer plusieurs serveurs de rapports afin qu'ils partagent une base de données du serveur de rapports.  
  
 [Configurer un serveur de rapports pour la remise du courrier électronique &#40;Gestionnaire de Configuration de SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 Fournit des instructions de configuration d'un serveur de rapports pour la distribution par messagerie.  
  
 [Configurer un pare-feu pour accéder au serveur de rapports](configure-a-firewall-for-report-server-access.md)  
 Explique comment ouvrir les ports utilisés pour les demandes entrantes et les réponses sortantes d'un serveur de rapports.  
  
 [Configurer un serveur de rapports en Mode natif pour l’Administration locale &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md)  
 Décrit les étapes supplémentaires requises pour se connecter au Gestionnaire de rapports ou à un serveur de rapports en utilisant http://localhost.  
  
 [Configurer un serveur de rapports pour l'administration à distance](configure-a-report-server-for-remote-administration.md)  
 Explique comment configurer une instance de serveur de rapports distante afin que vous puissiez vous y connecter et le configurer à partir d'un autre ordinateur.  
  
 [Activer ou désactiver les fonctionnalités Reporting Services](turn-reporting-services-features-on-or-off.md)  
 Explique comment supprimer les fonctionnalités inutilisées dans une installation Reporting Services.  
  
 [Activer les erreurs distantes &#40;Reporting Services&#41;](enable-remote-errors-reporting-services.md)  
 Explique comment définir des propriétés de serveur sur un serveur de rapports de façon à retourner des informations supplémentaires concernant les conditions d'erreur qui se produisent sur des serveurs distants.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer et administrer un serveur de rapports &#40;SSRS en mode natif&#41;](configure-and-administer-a-report-server-ssrs-native-mode.md)   
 [Configuration et administration d’un serveur de rapports &#40;mode SharePoint de Reporting Services&#41;](../configure-administer-report-server-reporting-services-sharepoint-mode.md)  
  
  
