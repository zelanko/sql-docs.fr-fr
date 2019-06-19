---
title: Installation de fichiers uniquement (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- files-only installation [Reporting Services]
- installation options [Reporting Services]
ms.assetid: bdc74a8f-046c-4aa0-bfbd-4f1711dfb9ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a854de693bce88fcba0de2f1c08e4b0fe296b512
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66108840"
---
# <a name="files-only-installation-reporting-services"></a>Installation de fichiers uniquement (Reporting Services)
  *L’installation de fichiers uniquement* fait référence à une installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans laquelle le programme d’installation crée l’arborescence pour les fichiers programme [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , copie les fichiers sur disque, inscrit le service Report Server sur l’ordinateur local, configure le compte de service, accorde les autorisations de fichiers au compte de service et inscrit le fournisseur WMI [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Une installation de fichiers uniquement inclut les éléments suivants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fonctionnalités : Le service Report Server (qui héberge le service Web Report Server, application et le Gestionnaire de rapports de traitement en arrière-plan), Générateur de rapports, le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] outil de Configuration et le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilitaires de ligne de commande (rsconfig.exe, rskeymgmt.exe et RS.exe). Elle ne s’applique pas aux fonctionnalités partagées telles que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ou [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], qui doivent être spécifiées comme éléments séparés si vous souhaitez les installer.  
  
 Par opposition avec d'autres modes d'installation, un serveur de rapports installé en mode fichiers uniquement n'est pas opérationnel lorsque l'installation est terminée. Une configuration supplémentaire sera nécessaire pour mettre le serveur de rapports en ligne à l’aide du [Gestionnaire de configuration de Reporting Services &#40;Mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="when-to-select-files-only-installation-mode"></a>Quand sélectionner le mode d'installation Fichiers uniquement  
 Une installation de fichiers uniquement doit être effectuée lorsque :  
  
-   vous souhaitez connecter le serveur de rapports à une base de données de serveur de rapports distante ;  
  
-   vous souhaitez installer le serveur de rapports en tant qu'instance nommée ;  
  
-   vous devez respecter des spécifications de déploiement qui incluent l'utilisation de paramètres ou de fonctionnalités personnalisés et vous souhaitez disposer d'un contrôle total sur le moment et la manière dont le serveur est configuré.  
  
-   Installation d'un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui inclut [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="how-to-perform-a-files-only-installation"></a>Comment effectuer une installation de fichiers uniquement  
 L'installation de fichiers uniquement est le mode d'installation par défaut pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Vous pouvez spécifier une installation de fichiers uniquement par le biais de la ligne de commande ou dans l'Assistant Installation. Les rubriques suivantes fournissent des instructions pas à pas :  
  
-   [Installer SQL Server 2014 à partir de l’Assistant Installation &#40;le programme d’installation&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).  
  
-   [Installer SQL Server 2014 à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
#### <a name="example-command-line-script"></a>Exemple de script de ligne de commande  
 Pour plus de clarté, l'exemple inclut /RSINSTALLMODE="FilesOnlyMode". Toutefois, le mode fichiers uniquement étant le mode par défaut, vous pouvez omettre ceci et obtenir tout de même une installation en mode fichiers uniquement.  
  
```  
setup /q /ACTION=install /FEATURES=RS /InstanceName=MSSQLSERVER /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /RSINSTALLMODE="FilesOnlyMode"  
```  
  
#### <a name="installation-wizard"></a>Assistant Installation  
 Lorsque vous sélectionnez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans la page Sélection de fonctionnalités, le programme d'installation fournit une page de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui vous permet de spécifier le mode d'installation. Pour spécifier une installation de fichiers uniquement, sélectionnez **Installer mais ne pas configurer le serveur** dans la page Configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Vérifier une installation de Reporting Services](verify-a-reporting-services-installation.md)   
 [Configurer le compte de service Report Server &#40;Gestionnaire de configuration de SSRS&#41;](configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](configure-report-server-urls-ssrs-configuration-manager.md)   
 [Configurer une connexion à la base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Installation en Mode SharePoint de Reporting Services &#40;SharePoint 2010 et SharePoint 2013&#41;](install-reporting-services-sharepoint-mode.md)   
 [Installer le serveur de rapports Reporting Services en mode natif](install-reporting-services-native-mode-report-server.md)   
 [Outils de Reporting Services](../tools/reporting-services-tools.md)  
  
  
