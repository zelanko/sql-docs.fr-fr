---
title: Configurer et administrer un serveur de rapports (SSRS en mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Reporting Services, components
- deploying [Reporting Services], component options
- report servers [Reporting Services], component options
- configuration options [Reporting Services]
- administering Reporting Services
- components [Reporting Services], configuring
- configuring servers [Reporting Services]
ms.assetid: cfec012b-56f1-4346-9814-247acf22351c
caps.latest.revision: 50
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: d5a004993ab886151ce9e3f5e3f7b2a2970f60d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044890"
---
# <a name="configure-and-administer-a-report-server-ssrs-native-mode"></a>Configurer et administrer un serveur de rapports (SSRS en mode natif)
  Cette rubrique récapitule les approches que vous pouvez utiliser pour configurer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Elle inclut également une liste de rubriques qui expliquent comment configurer des composants, des fonctions ou des fonctionnalités de serveur spécifiques. Pour configurer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous pouvez :  
  
-   utiliser le Gestionnaire de configuration de Reporting Services. Un grand nombre de rubriques de cette section contiennent des informations décrivant comment configurer des fonctions spécifiques par le biais de cet outil ;  
  
-   utiliser [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour personnaliser les propriétés du serveur, activer Mes rapports, d’activer les journaux des traces et définir des valeurs par défaut à l’échelle du site. Pour plus d’informations sur les paramètres du site, consultez [Reporting Services Report Server &#40;en Mode natif&#41; ](reporting-services-report-server-native-mode.md) de Management Studio. Notez que vous pouvez créer et exécuter un script qui définit des propriétés de serveur par programmation. Pour plus d’informations, consultez [tâches d’administration et déploiement de Script](../tools/script-deployment-and-administrative-tasks.md) et [Report Server System Properties](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md).  
  
-   utiliser le Gestionnaire de rapports pour accorder des autorisations d'accès au serveur de rapports. Les autorisations sont fournies via des attributions de rôles que vous définissez pour chaque compte d'utilisateur ou de groupe. Pour plus d’informations, consultez [Rôles et autorisations &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md).  
  
-   modifier éventuellement les fichiers de configuration afin de changer les paramètres d'application. Pour plus d’informations sur chaque fichier et les consignes concernant leur modification, consultez [fichiers de Configuration de Reporting Services](reporting-services-configuration-files.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 Décrit comment définir les URL d'accès au serveur de rapports et au Gestionnaire de rapports.  
  
 [Configurer le compte de Service Report Server &#40;Gestionnaire de Configuration de SSRS&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 Fournit des recommandations et des procédures pour la modification du compte de service et du mot de passe.  
  
 [Créer une base de données du serveur de rapports &#40;Gestionnaire de Configuration de SSRS&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
 Décrit le mode de création d'une base de données du serveur de rapports, tel qu'il est exigé pour le stockage des objets et des métadonnées de serveur.  
  
 [Configurer une connexion de base de données de serveur de rapports &#40;Gestionnaire de Configuration de SSRS&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 Décrit le mode de modification de la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la base de données du serveur de rapports.  
  
 [Configurer un serveur de rapports pour la remise du courrier électronique &#40;Gestionnaire de Configuration de SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 Décrit comment configurer un serveur de rapports pour la prise en charge de la distribution des rapports par courrier électronique.  
  
 [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de Configuration de SSRS&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 Décrit comment configurer un compte d'utilisateur de manière à traiter les rapports en mode sans assistance.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer l’accès au Générateur de rapports](configure-report-builder-access.md)   
 [Fichiers de configuration de Reporting Services](reporting-services-configuration-files.md)   
 [Gestionnaire de Configuration de Reporting Services &#40;en Mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Sécurité et protection de Reporting Services](../security/reporting-services-security-and-protection.md)   
 [Serveur de rapports Reporting Services &#40;mode natif&#41;](reporting-services-report-server-native-mode.md)  
  
  