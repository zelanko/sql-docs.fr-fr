---
title: Paramètres du Site et les fonctionnalités du Site (Mode SharePoint) Reporting Services | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0040fec-e2b7-4099-ae01-3b9bb9128bbd
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 1128105b7334fc5bf81fd72b9e178c15634a1cab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36037931"
---
# <a name="reporting-services-site-settings-and-site-featuressharepoint-mode"></a>Paramètres et fonctions du site Reporting Services (mode SharePoint)
  Le mode SharePoint de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fournit plusieurs fonctionnalités personnalisées au niveau du site qui peuvent être gérées à partir de la page des paramètres du site SharePoint. Les paramètres sont à l'échelle du site et affectent toutes les applications de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Vous devez disposer des autorisations de gestionnaire de contenu et d'administrateur système pour consulter cette page.  
  
|Paramètre du site|Description|  
|------------------|-----------------|  
|Paramètre du site [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|Paramètres à l'échelle du site décrits dans cette rubrique.|  
|Gérer les alertes de données|Gestion de la fonctionnalité d'alertes de données.|  
|Synchronisation des fichiers du serveur de rapports|Fonctionnalité au niveau du site désactivée par défaut.<br /><br /> Synchronise les fichiers du serveur de rapports (.rdl, .rsds, .smdl, .rsd, .rsc, .rdlx) à partir d'une bibliothèque de documents SharePoint sur le serveur de rapports lorsque des fichiers sont ajoutés ou mis à jour directement dans la bibliothèque de documents.<br /><br /> Pour plus d’informations, consultez [activer la fonctionnalité de synchronisation de fichier de serveur de rapports dans l’Administration centrale de SharePoint](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)|  
  
## <a name="to-open-the-reporting-services-site-settings-page"></a>Pour ouvrir la page des paramètres du site de Reporting Services  
  
1.  Dans le menu **Actions de site** du site SharePoint, cliquez sur **Paramètres du site**.  
  
2.  Dans la section **Reporting Services** , cliquez sur **Paramètres du site Reporting Services**.  
  
## <a name="options-for-reporting-services-site-settings"></a>Options des paramètres du site de Reporting Services  
  
|Option|Description|  
|------------|-----------------|  
|**Activer le téléchargement du contrôle ActiveX RSClientPrint**|Le contrôle affiche une boîte de dialogue d'impression personnalisée qui prend en charge les fonctionnalités communes aux autres boîtes de dialogue d'impression, notamment l'aperçu avant impression, les options de pages pour les choix spécifiques liés aux pages, aux plages, aux marges des pages et à l'orientation. Pour plus d’informations sur le contrôle, consultez [Utilisation du contrôle RSClientPrint dans les applications personnalisées](report-server-web-service/net-framework/using-the-rsclientprint-control-in-custom-applications.md)|  
|**Activer les erreurs distantes en mode local**|Affiche ou masque des messages d'erreur détaillés sur des ordinateurs distants en mode local. Si vous voyez s'afficher un message d'erreur semblable au suivant, l'activation des erreurs distantes peut être utile :<br /><br /> `For more information about this error navigate to the report server on the local server machine or enable remote errors`|  
|**Activer les métadonnées d'accessibilité pour les rapports**|Activer les métadonnées d'accessibilité dans la sortie HTML des rapports|  
|**Activer le dimensionnement exact d'ajustement de la visualisation des données pour les rapports**|Configurez le comportement d'ajustement de la visualisation des données à l'intérieur d'un tableau matriciel, pour l'ajuster exactement. Cela inclut le graphique, la jauge et la carte. Si désactivé, le comportement consiste à ajuster approximativement les visualisations des données, ce qui peut laisser des vides. Ce paramètre s'applique uniquement au rendu dans le composant WebPart Visionneuse de rapports. Pour gérer ce comportement pour le rendu côté serveur, vous devez modifier le fichier **rsreportserver.config** . Pour plus d'informations, consultez les documents suivants :<br /><br /> [Fichier de Configuration RSReportServer](report-server/rsreportserver-config-configuration-file.md).<br /><br /> [Personnaliser le rendu des paramètres d’Extension dans RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md).<br /><br /> [Paramètres d’informations de périphérique HTML](html-device-information-settings.md).<br /><br /> L'activation exacte peut avoir un impact sur les performances car le traitement permettant de déterminer la taille peut prendre plus de temps qu'un ajustement approximatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer une application de service SharePoint Reporting Services](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)  
  
  