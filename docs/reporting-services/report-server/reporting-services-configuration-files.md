---
title: Fichiers de configuration de Reporting Services | Microsoft Docs
ms.date: 05/30/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], configuration files
- configuration options [Reporting Services]
- modifying configuration files
- configuration files [Reporting Services]
ms.assetid: 21e5c32f-ad67-4917-b55a-8e21bd64f5a6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 25b695456bbac34e2c6ce8bf8c312c4108dd852e
ms.sourcegitcommit: 561cee96844b82ade6cf543a228028ad5c310768
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66506652"
---
# <a name="reporting-services-configuration-files"></a>Fichiers de configuration de Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stocke les informations sur les composants dans le Registre et dans des fichiers de configuration qui sont copiés dans le système de fichiers au cours de l'installation. Les fichiers de configuration contiennent une combinaison de valeurs destinées à un usage interne uniquement et de valeurs définies par l'utilisateur. Les valeurs définies par l'utilisateur sont spécifiées par le biais du programme d'installation, des outils de configuration, des utilitaires de ligne de commande ou en modifiant manuellement les fichiers de configuration.  
  
 La modification des fichiers de configuration est uniquement nécessaire si vous ajoutez ou configurez des paramètres avancés. Les paramètres de configuration sont spécifiés soit comme des éléments, soit comme des attributs XML. Si le langage XML et les fichiers de configuration vous sont familiers, vous pouvez modifier les paramètres définissables par l'utilisateur dans un éditeur de texte ou de code. Pour plus d’informations sur la modification d’un fichier de configuration, ou pour en savoir plus sur la façon dont le serveur de rapports lit les paramètres de configuration nouveaux et mis à jour, consultez [Modifier un fichier de configuration Reporting Services &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
> [!NOTE]  
> Dans les versions antérieures, le Gestionnaire de rapports avait son propre fichier de configuration nommé RSWebApplication.config. Ce fichier est maintenant obsolète. Si vous avez effectué une mise à niveau à partir d'une installation antérieure, le fichier n'est pas supprimé ; toutefois, le serveur de rapports ne lira pas les paramètres qu'il contient. Si le fichier existe sur votre ordinateur, vous devez le supprimer. Dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les versions ultérieures, tous les paramètres de configuration du Gestionnaire de rapports sont stockés et lus dans le fichier RSReportServer.config. Pour obtenir une liste des paramètres qui ont été supprimés ou déplacés, consultez [Modifications importantes de SQL Server Reporting Services dans SQL Server 2016](../../reporting-services/breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
 Contenu de cet article  
  
-   [Résumé des fichiers de configuration (mode natif)](#bkmk_config_file_Summary_native_mode)  
  
-   [Résumé des fichiers de configuration (mode SharePoint)](#bkmk_config_file_Summary_sharepoint_mode)  
  
##  <a name="bkmk_config_file_Summary_native_mode"></a> Résumé des fichiers de configuration (mode natif)  
 Le tableau suivant fournit une description de l'emplacement de stockage des paramètres de configuration. La plupart des paramètres de configuration sont stockés dans des fichiers de configuration inclus dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Par défaut, le répertoire d'installation est le suivant :  
  
''' Installer les chemins d’accès  
C:\Program Files\Microsoft SQL Server\MSRSxx.MSSQLSERVER (où xx est le numéro de version de MS SQL) ou  
C:\Program Files\Microsoft SQL Server Reporting Services  
  selon la version SSRS
```  
  
|Stored in:|Description|Location|  
|----------------|-----------------|--------------|  
|RSReportServer.config|Stores configuration settings for feature areas of the Report Server service: Report Manager or the web portal, the Report Server Web service, and background processing. For more information about each setting, see [RsReportServer.config Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).|\<Installation directory> \Reporting Services \ReportServer|  
|RSSrvPolicy.config|Stores the code access security policies for the server extensions. For more information about this file, see [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<Installation directory> \Reporting Services \ReportServer|  
|RSMgrPolicy.config|Stores the code access security policies for the web portal. For more information about this file, see [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<Installation directory> \Reporting Services \ReportManager|  
|Web.config for the Report Server Web service|Includes only those settings that are required for ASP.NET.|\<Installation directory> \Reporting Services \ReportServer|  
|Web.config for Report Manager|Includes only those settings that are required for ASP.NET if applicable for the SSRS version.|\<Installation directory> \Reporting Services \ReportManager|  
|ReportingServicesService.exe.config|Stores configuration settings that specify the trace levels and logging options for the Report Server service. For more information about the elements in this file, see [ReportingServicesService Configuration File](../../reporting-services/report-server/reportingservicesservice-configuration-file.md).|\<Installation directory> \Reporting Services \ReportServer \Bin|  
|Registry settings|Stores configuration state and other settings used to uninstall Reporting Services. If you are troubleshooting an installation or configuration problem, you can view these settings to get information about how the report server is configured.<br /><br /> Do not modify these settings directly as this can invalidate your installation.|HKEY_LOCAL_MACHINE \SOFTWARE \Microsoft \Microsoft SQL Server \\<InstanceID\> \Setup<br /><br /> **- And -**<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\Services\ReportServer|  
|RSReportDesigner.config|Stores configuration settings for Report Designer. For more information, see [RSReportDesigner Configuration File](../../reporting-services/report-server/rsreportdesigner-configuration-file.md).|\<drive>:\Program Files \Microsoft Visual Studio 10 \Common7 \IDE \PrivateAssemblies.|  
|RSPreviewPolicy.config|Stores the code access security policies for the server extensions used during report preview. For more information about this file, see [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssembliesr|  
  
##  <a name="bkmk_config_file_Summary_sharepoint_mode"></a> Summary of configuration Files (SharePoint mode)  
 The following table provides a description of configuration files used for a SharePoint mode report server. Most configuration settings are stored in SharePoint service application databases. For more information, see [Reporting Services SharePoint Service and Service Applications](../../reporting-services/report-server-sharepoint/reporting-services-sharepoint-service-and-service-applications.md).  
  
 By default, the installation directory for SharePoint mode is the following:  
  
```Install path
C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting  
```  
  
|Stockage dans :|Description|Emplacement|  
|----------------|-----------------|--------------|  
|RSReportServer.config|Stocke les paramètres de configuration des fonctionnalités du service Report Server : Gestionnaire de rapports, service Web Report Server et traitement en arrière-plan. Pour plus d’informations sur chaque paramètre, consultez [Fichier de configuration RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).|\<Répertoire d’installation>\Reporting Services\ReportServer|  
|RSSrvPolicy.config|Stocke les stratégies de sécurité d'accès du code pour les extensions serveur. Pour plus d'informations sur ce fichier, consultez [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<Répertoire d’installation>\Reporting Services\ReportServer|  
|Web.config pour le service Web Report Server|Inclut uniquement les paramètres qui sont requis pour ASP.NET, le cas échéant pour la version SSRS.|\<Répertoire d’installation>\Reporting Services\ReportServer|  
|Paramètres du Registre|Stocke l'état de la configuration et d'autres paramètres utilisés pour la désinstallation de Reporting Services. Stocke également des informations sur chaque application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .<br /><br /> Ne modifiez pas directement ces paramètres, car cela risque de rendre votre installation non valide.|HKEY_LOCAL_MACHINE \SOFTWARE \Microsoft \Microsoft SQL Server \\<ID_Instance\> \Setup<br /><br /> Exemple d’ID d’instance : MSSQL13.MSSQLSERVER<br /><br /> **- et -**<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\Reporting Services\Service Applications|  
|RSReportDesigner.config|Stocke les paramètres de configuration du Concepteur de rapports. Pour plus d’informations, consultez [RSReportDesigner Configuration File](../../reporting-services/report-server/rsreportdesigner-configuration-file.md).|\<lecteur>:\Program Files\Microsoft Visual Studio 10\Common7\IDE\PrivateAssemblies.|  
  
## <a name="see-also"></a>Voir aussi  
 [Serveur de rapports Reporting Services &#40;mode natif&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Extensions Reporting Services](../../reporting-services/extensions/reporting-services-extensions.md)   
 [Utilitaire rsconfig &#40;SSRS&#41;](../../reporting-services/tools/rsconfig-utility-ssrs.md)   
 [Démarrer et arrêter le service du serveur de rapports](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)  
  
  
