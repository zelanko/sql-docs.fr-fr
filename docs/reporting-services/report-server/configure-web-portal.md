---
title: Configurer le portail web | Documents Microsoft
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- the web portal [Reporting Services], configuring
ms.assetid: e918986c-af15-48f6-8178-256aed829c6a
caps.latest.revision: 28
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c0c6cc27711140e96bbf4420e8de596af53ddfcd
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="configure-the-web-portal"></a>Configurer le portail web

le portail web est une application Web frontale utilisée pour afficher des rapports, gérer le contenu du serveur de rapports et accorder l’accès utilisateur à un serveur de rapports en mode natif. le portail web est installé avec le service Web Report Server dans la même instance de serveur de rapports et éventuellement configuré si vous sélectionnez le **installer la configuration en mode natif par défaut** option dans le programme d’installation. Vous pouvez également configurer le portail web comme une tâche après l’installation. Cette rubrique fournit des informations sur ce qui suit les scénarios de configuration du portail web :

## <a name="prerequisites"></a>Conditions préalables

Pour utiliser le portail web, vous devez satisfaire aux conditions suivantes :

- Vous devez disposer d'un serveur de rapports doté d'une configuration minimale. Pour plus d’informations sur la configuration minimale d’un serveur de rapports, consultez [configurer un serveur de rapports](../../reporting-services/report-server/configure-a-report-server-reporting-services-native-mode.md).

- Votre serveur de rapports doit s'exécuter en mode natif. Vous ne pouvez pas utiliser le portail web avec un serveur de rapports est configuré en mode intégré SharePoint. Dans SQL Server 2012, vous ne pouvez pas basculer un serveur de rapports d'un mode à un autre. Si vous souhaitez modifier le type de serveur de rapports que votre environnement utilise, vous devez installer le mode souhaité du serveur de rapports, puis copier ou déplacer les éléments de rapport vers le nouveau serveur de rapports. Ce processus est habituellement désigné sous le terme de « migration ». Les étapes nécessaires pour la migration dépendent du mode vers lequel vous effectuez la migration et de la version d'origine de la migration. Pour plus d'informations, consultez [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).

- Vous devez également disposer d’Internet Explorer 11 ou version ultérieure avec des scripts activée. Pour plus d’informations, consultez [Prise en charge des navigateurs pour Reporting Services et Power View](../../reporting-services/browser-support-for-reporting-services-and-power-view.md).

## <a name="configure-the-web-portal-to-use-the-default-url"></a>Configurer le portail web pour utiliser l’URL par défaut

Le portail web est une application Web que les utilisateurs accèdent via un navigateur Web. Vous devez au minimum définir l'URL utilisée pour ouvrir l'application dans une fenêtre de navigateur. L'URL est formée d'un nom d'hôte, d'un port et d'un répertoire virtuel. Les valeurs par défaut de cette URL utilisent les valeurs de nom d'hôte et de port que vous avez définies pour l'URL du service Web Report Server, plus le nom du répertoire virtuel **rapports** . Si vous disposez d’une instance nommée, le répertoire virtuel est **reports_instance**, où **instance** est le nom de votre instance [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .

Par défaut, le portail web URL se compose d’un nom de répertoire virtuel unique, ainsi que le nom de port et l’hôte qui est défini pour le service Web Report Server qui s’exécute dans la même instance. Dans la plupart des cas, le nom d'hôte est le nom de réseau du serveur de rapports, mais il peut également s'agir d'une adresse IP ou d'un en-tête d'hôte qui résout l'ordinateur. Pour configurer le portail web pour utiliser l’URL par défaut, utilisez le **URL du portail Web** page dans le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] outil de Configuration.

> [!TIP]
> Si vous essayez d’accéder au portail web sur un ordinateur distant et que vous recevez des messages d’erreur de connexion dans votre navigateur, les paramètres de pare-feu sont généralement en cause. Pour plus d’informations, consultez [Configurer un pare-feu pour accéder au serveur de rapports](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md).

#### <a name="to-configure-the-default-the-web-portal-url-and-virtual-directory"></a>Pour configurer la valeur par défaut du portail web URL et le répertoire virtuel

1. Démarrez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , puis connectez-vous à l'instance du serveur de rapports.

2. Dans le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] outil de Configuration, sélectionnez **URL du portail Web** pour ouvrir la page de configuration de l’URL.

3. Entrez un nom de répertoire virtuel unique pour le portail web.

4. Cliquez sur **Appliquer**.

5. Si vous utilisez [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] ou Windows Server 2008, des étapes supplémentaires peuvent être requises avant de pouvoir utiliser le portail web. Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).

## <a name="configure-the-web-portal-to-use-a-specific-report-server-url"></a>Configurer le portail web pour utiliser une URL de serveur de rapports spécifique

Par défaut, le portail web se connecte au service Web Report Server qui s’exécute dans le même service de serveur de rapports. Le portail web utilise l’URL du service Web Report Server pour établir la connexion. Si vous définissez plusieurs URL pour le service Web Report Server, le portail web utilise la dernière que vous avez définie. Toutefois, pour certains déploiements, vous pouvez le portail web se connecte toujours au service Web via une URL statique. En effet, si vous avez configuré le filtrage des paquets sur un port ou une adresse IP spécifique et que vous souhaitez que toutes les connexions au serveur de rapports se soumettent aux règles de filtrage que vous avez définies, vous utiliserez une URL statique.

Lorsque vous configurez des URL dans le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] outil de Configuration, le portail web détecte et utilise automatiquement les URL nouveaux et mis à jour pour le serveur de rapports qui s’exécute dans la même instance de serveur. Si votre déploiement exige que vous utilisiez une URL statique unique pour toutes les demandes de serveur de rapports, vous pouvez spécifier cette URL dans le fichier RSReportServer.config.

#### <a name="to-configure-a-static-report-server-url"></a>Pour configurer une URL de serveur de rapports statique

1. Ouvrez le fichier **RSReportServer.config** dans un éditeur de texte. Par défaut, il se trouve à \Program Files\Microsoft SQL Server\MSRS12. \< *instancename*> \Reporting.  

2. Recherchez **ReportServerURL**.

3. Remplacez-le par l'URL de l'instance du serveur de rapports.

4. Enregistrez vos modifications et fermez le fichier.

Pour plus d’informations sur le fichier de configuration, consultez [Modifier un fichier de configuration Reporting Services &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) et [Fichier de configuration RSReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).

## <a name="customize-styles-or-application-title"></a>Personnaliser les styles ou le titre de l'application

Vous pouvez créer un package de marque personnalisée pour modifier les couleurs utilisées pour le portail web. Pour plus d’informations, consultez [personnalisation du portail web](../branding-the-web-portal.md)

#### <a name="to-modify-application-title"></a>Pour modifier le titre de l'application

1. Connectez-vous à l'aide d'un compte auquel les autorisations **Administrateur système** sont assignées sur le serveur de rapports.

2. Ouvrez Internet Explorer.

3. Entrez le portail web URL. Par défaut, il s’agit de http://\<**nom de votre serveur**> / reports, mais si vous avez installé Reporting Services comme instance nommée, l’URL par défaut sera http://\<**nom de votre serveur**> / reports\<**_nominstance**>.

4. Sélectionnez **Paramètres du site**.

5. Sous l'onglet **Général** , dans **Nom**, remplacez **SQL Server Reporting Services** par un nom différent.

6. Sélectionnez **Appliquer**.

## <a name="next-steps"></a>Étapes suivantes

[Portail Web](../../reporting-services/web-portal-ssrs-native-mode.md)  
[Prise en charge des navigateurs pour Reporting Services](../../reporting-services/browser-support-for-reporting-services-and-power-view.md)
[configurer une URL](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
[Vérifier une installation de Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)   
[Activer les fonctionnalités de Reporting Services ou désactiver](../../reporting-services/report-server/turn-reporting-services-features-on-or-off.md)   
[Gérer un serveur de rapports Reporting Services (SSRS) en mode natif](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)   
[Fichier de configuration RSReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
[Configurer un serveur de rapports en Mode natif pour l’Administration locale](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)

 D’autres questions ? [Essayez de poser le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

