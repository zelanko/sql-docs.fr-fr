---
title: Installer le Générateur de rapports | Microsoft Docs
description: Générateur de rapports est une application autonome installée sur votre ordinateur par vos propres soins ou par un administrateur.
ms.date: 01/31/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
ms.assetid: 6b2291bb-1d20-4d08-81cb-a16dd8e01faf
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: f1c8338fe9c477f8885839a0236f2aaaa0e9ebde
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91890849"
---
# <a name="install-report-builder"></a>Installer le Générateur de rapports

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

[!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] est une application autonome installée sur votre ordinateur par vos propres soins ou par un administrateur. Vous pouvez l’installer à partir du Centre de téléchargement Microsoft, d’un serveur de rapport [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] le serveur de rapports ou d’un site SharePoint intégré avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  

> [!NOTE]
> Vous recherchez des informations sur l’installation de Power BI Report Builder à la place ? Consultez la page [Microsoft Power BI Report Builder](https://www.microsoft.com/download/details.aspx?id=58158) dans le Centre de téléchargement Microsoft. 

 Un administrateur installe et configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], accorde l’autorisation de télécharger l’[!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] à partir du portail web, et gère les dossiers et les autorisations d’accès aux rapports, les parties des rapports et les datasets partagés enregistrés sur le serveur de rapports. Pour plus d’informations sur l’administration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [Reporting Services Report Server &#40;mode natif&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md).  
  
## <a name="install-ssrbnoversion-from--a--web-portal-or-sharepoint-library"></a>Installez l’[!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] à partir d’un portail web ou d’une bibliothèque SharePoint 

> [!NOTE]
> L’intégration de Reporting Services à SharePoint n’est plus disponible après SQL Server 2016.
  
 Vous pouvez démarrer l’[!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] à partir d’un portail web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ou d’un site SharePoint intégré avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Pour plus d’informations, consultez [Démarrer le Générateur de rapports](../../reporting-services/report-builder/start-report-builder.md).  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
  
### <a name="sharepoint-site-integrated-with-ssrsnoversion"></a>Site SharePoint intégré avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]
  
 Sur un site SharePoint intégré avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)],, si le menu **Nouveau document** ne répertorie pas **Rapport du Générateur de rapports**, **Modèle du générateur de rapports**et **Source de données du rapport**, leurs types de contenus doivent être ajoutés à la bibliothèque SharePoint. Pour plus d’informations, consultez [Ajouter des types de contenus Reporting Services à une bibliothèque SharePoint](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md).  

::: moniker-end
 
## <a name="install-ssrbnoversion-with-microsoft-endpoint-configuration-manager"></a>Installer [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] avec le Gestionnaire de configuration Microsoft Endpoint 
  
 Un administrateur peut également utiliser un logiciel tel que le Gestionnaire de configuration Microsoft Endpoint pour placer le programme sur votre ordinateur. Pour savoir comment utiliser des logiciels spécifiques pour installer le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)], consultez la documentation des logiciels en question. Pour plus d'informations, consultez la [documentation du Gestionnaire de configuration Microsoft Endpoint](/configmgr/).  
  
> [!IMPORTANT]  
>  Les fonctionnalités de sécurité de Windows Vista et Windows 7 requièrent des autorisations élevées pour exécuter des opérations en ligne de commande ; par conséquent, vous êtes invité à confirmer que vous avez l'autorisation d'exécuter la ligne de commande. Il ne s'agit pas d'une installation sans assistance. Pour effectuer une installation sans assistance, vous devez exécuter la ligne de commande en tant qu'administrateur.  
  
## <a name="system-requirements"></a>Configuration requise
  
 Consultez la section **Configuration système requise** de la [page de téléchargement du Générateur de rapports](https://go.microsoft.com/fwlink/?LinkID=734968) du Centre de téléchargement Microsoft.
  
##  <a name="to-install-ssrbnoversion-from-the-download-site"></a><a name="download"></a> Pour installer le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] à partir du site de téléchargement  
  
1.  Sur la [page Générateur de rapports du Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?LinkID=734968) , cliquez sur **Télécharger**.  
  
2.  Une fois le téléchargement du [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] terminé, cliquez sur **Exécuter**.  
  
     Cette opération lance l’Assistant SQL Server [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] .  
  
3.  Acceptez les conditions du contrat de licence, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Serveur cible par défaut** , spécifiez éventuellement l'URL du serveur de rapports cible s'il est différent du serveur par défaut. Cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  Si vous prévoyez de travailler avec le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] quand celui-ci est connecté à un serveur de rapports, il est plus commode de spécifier l’URL du serveur à ce stade. Vous pouvez également le faire à partir de la boîte de dialogue **Options** dans le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)].  
  
5.  Cliquez sur **Installer** pour effectuer l’installation du [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)].  
  
## <a name="to-install-ssrbnoversion-from-a-share"></a>Pour installer le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] à partir d’un partage  
  
1.  Contactez votre administrateur afin de connaître l’emplacement du fichier ReportBuilder.msi que vous exécutez pour installer le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] sur votre ordinateur local.  
  
2.  Recherchez le fichier ReportBuilder.msi, le package MSI Windows Installer du [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)], et cliquez dessus.  
  
     Cette opération lance l’Assistant SQL Server [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] .  
  
3.  Suivez les étapes suivantes décrites dans [Pour installer le Générateur de rapports à partir du site de téléchargement](#download).  
  
## <a name="to-install-ssrbnoversion-from-the-command-line"></a>Pour installer l’ [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] à partir de la ligne de commande 

 Vous pouvez également effectuer une installation du [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] à partir de la ligne de commande et spécifier des arguments afin de personnaliser l’installation. En plus des paramètres MSI standard intrinsèques, vous pouvez utiliser les paramètres personnalisés fournis par le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] : RBINSTALLDIR et REPORTSERVERURL. RBINSTALLDIR spécifie le dossier d’installation racine du [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)]. REPORTSERVERURL spécifie le serveur de rapports par défaut utilisé par le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] pour enregistrer des rapports.  
  
 Si vous souhaitez effectuer une installation totalement sans assistance, sans aucune interaction avec l’interface utilisateur, spécifiez l’option **/quiet** . Par défaut, l'indicateur d'option quiet supprime les erreurs d'installation. Il est par conséquent recommandé d’inclure l’option **/l** , qui spécifie l’enregistrement dans le journal, lorsque vous utilisez l’option quiet.   
  
1.  Sur la [page Générateur de rapports du Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?LinkID=734968), cliquez sur **Télécharger**.  
  
2.  Une fois le téléchargement du [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] terminé, cliquez sur **Enregistrer**.  
  
3.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
4.  Dans la zone **Ouvrir** , tapez **cmd.**  
  
5.  Dans la fenêtre d’invite de commandes, naviguez jusqu’au dossier où vous avez enregistré ReportBuilder.msi.  
  
6.  Tapez une commande au format suivant :  
  
     `msiexec/i ReportBuilder.msi /option [value] [/option [value]]`  
  
     Les deux options spécifiques à l’installation du [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] sont : RBINSTALLDIR et REPORTSERVERURL. Il est inutile d’inclure ces arguments dans la ligne de commande. Voici la ligne de commande de base :  
  
     `msiexec /i ReportBuilder3_x86.msi /quiet`  
  
7.  Pour exécuter la commande, appuyez sur ENTRÉE.  
  
## <a name="set-ssrbnoversion-defaults"></a>Définir les paramètres par défaut du [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)]  
  
-   Après avoir installé le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)], vous pouvez définir des options par défaut. Cliquez sur **Fichier** > **Options**.  
  
     Le plus utile est de définir le site SharePoint ou le portail web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] par défaut. Pour plus d’informations, consultez [Set default options for Report Builder](../../reporting-services/report-builder/set-default-options-for-report-builder.md).  
  
-   Cliquez sur **Générateur de rapports** .  
  
     Si le serveur de rapports ne figure pas dans la liste des serveurs existants, fermez la boîte de dialogue **Ouvrir un rapport**, puis cliquez sur **Se connecter** au bas de [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] pour vous connecter au serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Générateur de rapports](../../reporting-services/report-builder/start-report-builder.md)   
 [Désinstaller le Générateur de rapports](../../reporting-services/install-windows/uninstall-report-builder.md)  
  
