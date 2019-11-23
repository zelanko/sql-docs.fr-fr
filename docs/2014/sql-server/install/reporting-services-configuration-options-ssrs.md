---
title: Reporting Services les options de configuration (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.ins.instwizard.reportserverinstoptions.f1
helpviewer_keywords:
- Report Server Installation Options page [SQL Server Installation Wizard]
- report servers [Reporting Services], installing
- SQL Server Installation Wizard, Report Server Installation Options page
ms.assetid: e4561f6c-bc7f-467e-821a-cde8e5cd7391
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 1b54661c47ff40af595be55d444f6c0ffb4bc2cd
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952122"
---
# <a name="reporting-services-configuration-options-ssrs"></a>Options de configuration Reporting Services (SSRS)
  Utilisez la page **Configuration de Reporting Services** de l’Assistant Installation de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour spécifier le mode d’installation et de configuration d’un serveur de rapports. La disponibilité d’une option d’installation dépend des options que vous avez choisies précédemment dans la page **Sélection de fonctionnalités** , ainsi que du fait que vous installez également ou non une instance locale du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] lors de l’installation du serveur de rapports.  
  
 Dans certains cas, si un certificat SSL (Secure Sockets Layer) est installé sur l'ordinateur et lié à un caractère générique fort, le programme d'installation crée les URL Reporting Services à l'aide du préfixe HTTPS. Pour plus d’informations sur la façon dont les certificats sont mappés à des URL Reporting Services, consultez [configuration d’un serveur de rapports pour les connexions protocole SSL (SSL)](https://go.microsoft.com/fwlink/?LinkId=199089) (https://go.microsoft.com/fwlink/?LinkId=199089) dans documentation en ligne de SQL Server.  
  
 Pour obtenir les informations les plus récentes concernant les [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et l’installation et la configuration de cette version, consultez [informations supplémentaires sur l’installation](https://go.microsoft.com/fwlink/?LinkId=207425) (https://go.microsoft.com/fwlink/?LinkId=207425).  
  
## <a name="options"></a>Options  
  
### <a name="reporting-services-native-mode"></a>Mode natif de Reporting Services  
 Si le programme d'installation ne peut pas configurer le serveur de rapports par défaut, car une ou plusieurs conditions requises ne sont pas respectées, l'Assistant Installation n'autorise que l'option d'installation minimale ; les fichiers dont vous avez besoin sont copiés mais vous êtes obligé d'utiliser le Gestionnaire de configurations de Reporting Services pour configurer un serveur de rapports en mode natif à la fin de l'installation.  
  
> [!NOTE]  
>  Un fichier de base de données de serveur de rapports existant peut entraîner l'échec de l'installation si vous choisissez l'une des options d'installation par défaut. Lorsque vous choisissez une option d'installation par défaut, le programme d'installation tente de créer une base de données de serveur de rapports à l'aide du nom par défaut. Si une base de données existe déjà sous ce nom, le programme d'installation échoue et vous devez restaurer l'installation. Pour éviter ce problème, vous pouvez renommer la base de données existante avant d’exécuter le programme d’installation ou choisir l’option **Installer uniquement** afin de pouvoir spécifier des paramètres de base de données personnalisés une fois l’installation terminée.  
  
#### <a name="install-and-configure"></a>Installation et configuration  
 Installe une instance du serveur de rapports en mode natif en utilisant les valeurs par défaut pour les bases de données, le compte de service et les réservations d'URL du serveur de rapports. Lorsque vous choisissez cette option, l'instance du serveur de rapports est prête à être utilisée à la fin de l'installation. Le programme d'installation crée la base de données du serveur de rapports à l'aide d'une instance locale du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , puis configure un serveur de rapports pour l'utilisation des valeurs par défaut.  
  
 Cette option n'est disponible que si les valeurs par défaut utilisées dans l'installation d'un serveur de rapports sont valides pour votre système. Cette option est recommandée pour les développeurs qui souhaitent installer tous les composants localement, ainsi que pour les utilisateurs qui évaluent le logiciel.  
  
 Pour afficher les informations relatives aux paramètres par défaut utilisés par le programme d’installation ou pour déterminer la raison pour laquelle la configuration par défaut ne peut pas être installée, cliquez sur **Détails**. Pour plus d’informations sur la configuration par défaut d’un serveur de rapports en mode natif, consultez [configuration par défaut pour une installation en mode natif (Reporting Services)](https://go.microsoft.com/fwlink/?LinkId=199091) (https://go.microsoft.com/fwlink/?LinkId=199091).  
  
#### <a name="install-only"></a>Installer uniquement  
 Installe les fichiers programme du serveur de rapports, crée le compte de service Report Server et inscrit le fournisseur WMI (Windows Management Instrumentation) du serveur de rapports. Cette option d'installation porte également le nom d'installation de « fichiers uniquement ». Sélectionnez cette option si vous ne souhaitez pas utiliser la configuration par défaut. Si la configuration par défaut ne peut pas être installée, ou si vous installez un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui inclut [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], cette option est la seule disponible. Pour plus d’informations sur l’installation de fichiers uniquement, consultez [installation de fichiers uniquement (Reporting Services)](https://go.microsoft.com/fwlink/?LinkId=199093) (https://go.microsoft.com/fwlink/?LinkId=199093).  
  
 Une fois l'installation terminée, vous devez créer la base de données du serveur de rapports et configurer le serveur de rapports de sorte qu'il puisse être utilisé. Pour configurer un serveur de rapports et créer la base de données correspondante, utilisez le gestionnaire de configuration de Reporting Services. Pour plus d’informations, consultez [procédure : créer une base de données du serveur de rapports (Reporting Services Configuration)](https://go.microsoft.com/fwlink/?LinkId=199094) (https://go.microsoft.com/fwlink/?LinkId=199094) et [configuration d’une connexion à la base de données du serveur de rapports](https://go.microsoft.com/fwlink/?LinkId=199095) (https://go.microsoft.com/fwlink/?LinkId=199095).  
  
### <a name="reporting-services-sharepoint-mode"></a>Mode SharePoint de Reporting Services  
  
#### <a name="install-only"></a>Installer uniquement  
 Installe les fichiers programmes du serveur de rapports, ainsi que les applets de commande PowerShell. Une fois l'installation terminée, vous devez démarrer les services [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint et créer une application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d'informations, consultez les documents suivants :  
  
-   [Installation d’Reporting Services serveur de rapports en mode SharePoint pour les Power View et les alertes de données](https://go.microsoft.com/fwlink/?LinkId=207543) (https://go.microsoft.com/fwlink/?LinkId=207543).  
  
-   [Installez Reporting Services mode SharePoint en tant que batterie de serveurs unique](https://go.microsoft.com/fwlink/?LinkId=207544) (https://go.microsoft.com/fwlink/?LinkId=207544).  
  
-   [Reporting Services serveur de rapports (SSRS)](https://go.microsoft.com/fwlink/?LinkID=207244) (https://go.microsoft.com/fwlink/?LinkID=207244).  
  
## <a name="installing-the-reporting-services-add-in-for-sharepoint-technologies"></a>Installation du complément Reporting Services pour les technologies SharePoint  
 À partir de la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] le complément peut être installé avec l'installation de SQL Server, dans la page de sélection de fonctionnalités de l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Toutefois, vous pouvez installer le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour SharePoint 2010 à l'aide d'une des méthodes suivantes :  
  
-   Exécutez l’outil de préparation des produits SharePoint 2010, **PreRequisiteInstaller.exe**.  
  
-   Effectuez l'installation depuis le support d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cliquez sur le fichier **rsSharePoint.msi** dans le dossier d’installation sur le support d’installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une fois l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] terminée.  
  
-   Téléchargez et installez le complément. Pour plus d’informations, consultez [où trouver le complément Reporting Services pour les produits SharePoint](https://go.microsoft.com/fwlink/?LinkID=208634) (https://go.microsoft.com/fwlink/?LinkID=208634).  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer Gestionnaire de configuration de Reporting Services](https://go.microsoft.com/fwlink/?LinkId=199096)   
 [Créer une base de données du serveur de rapports (Reporting Services Configuration)](https://go.microsoft.com/fwlink/?LinkId=199094)   
 [Mettre à niveau et migrer Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628)   
 [Installation via l’invite de commandes en mode natif et en mode SharePoint de Reporting Services](https://go.microsoft.com/fwlink/?LinkId=217620)  
  
  
