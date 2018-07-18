---
title: Modifications avec rupture dans SQL Server Reporting Services dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Me.Value references
- Reporting Services, backward compatibility
- breaking changes [Reporting Services]
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
caps.latest.revision: 111
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2e13cebd7697f2ff497ad0f288333e517c9e575d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327619"
---
# <a name="breaking-changes-in-sql-server-reporting-services-in-sql-server-2014"></a>Modifications importantes de SQL Server Reporting Services dans SQL Server 2014
  Cette rubrique décrit les changements importants apportés à [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Ces modifications peuvent interrompre les applications, scripts ou fonctionnalités fondés sur les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Vous pouvez rencontrer ces problèmes lorsque vous effectuez une mise à niveau, ou dans les scripts ou les rapports personnalisés. Pour plus d'informations, consultez [Use Upgrade Advisor to Prepare for Upgrades](../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
 **Dans cette rubrique :**  
  
-   [SQL Server 2014 Reporting Services des modifications avec rupture](#bkmk_sql14)  
  
-   [SQL Server 2012 Reporting Services des modifications avec rupture](#bkmk_rc0)  
  
-   [SQL Server 2008 R2 Reporting Services des modifications avec rupture](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Modifications avec rupture de Reporting Services  
 Il y a aucune [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] modifications avec rupture dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Modifications avec rupture de Reporting Services  
  
### <a name="sharepoint-mode-server-references-require-the-sharepoint-site"></a>Les références de serveur en mode SharePoint nécessitent un site SharePoint  
 Vous ne pouvez pas parcourir ou référencer directement le serveur de rapports à l'aide du nom direct virtuel dans le chemin d'accès de l'URL. Exemple :  
  
 `http://<Server name>/ReportServer`  
  
 Vous devez maintenant inclure le site SharePoint dans le chemin d'accès de l'URL. Par exemple, si votre nom du site est «`videos`» et utilise le préfixe «`sites`», l'URL devrait être semblable à ce qui suit :  
  
 `http://<Server Name>/sites/videos/_vti_bin/ReportServer`  
  
### <a name="changes-to-sharepoint-mode-command-line-installation"></a>Modifications à l'installation de ligne de commande en mode SharePoint  
 Le paramètre d'entrée **/RSINSTALLMODE** fonctionne uniquement avec les installations en mode natif, et non pour les installations en mode SharePoint. Par exemple, ce qui suit n’est pas pris en charge dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]: **/rsinstallmode = « DefaultSharePointMode »**. Au lieu de ce paramètre d'entrée, utilisez **/RSSHPINSTALLMODE="DefaultSharePointMode"**.  
  
 L'instruction suivante est un exemple d'une commande d'installation complète et d’un jeu de paramètres : **setup /ACTION=install /FEATURES=SQL,RS /InstanceName=Denali_INST1 …./RSSHPINSTALLMODE="DefaultSharePointMode"**  
  
 Pour plus d’informations sur les installations de ligne de commande, consultez [invite de commandes de Reporting Services SharePoint Mode d’Installation et en Mode natif](install-windows/install-reporting-services-at-the-command-prompt.md).  
  
### <a name="the-reporting-services-wmi-provider-no-longer-supports-configuration-of-sharepoint-mode"></a>Le fournisseur WMI de Reporting Services ne prend plus en charge la configuration du mode SharePoint  
 La configuration de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint est maintenant exécutée avec les applets de commande PowerShell et l'Administration centrale de SharePoint. La nouvelle architecture [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode SharePoint utilise l'architecture de services SharePoint. SharePoint ne prend pas en charge les interfaces WMI.  
  
 Ces modifications concernent la liste suivante de composants et de flux de travail :  
  
-   Applications personnalisées qui utilisent le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fournisseur WMI pour [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode SharePoint.  
  
-   Le gestionnaire de configuration [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], rskeymgmt.exe et rsconfig.exe. Au lieu d’utiliser ces utilitaires pour la configuration de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] mode SharePoint, utilisez l’Administration centrale de SharePoint et PowerShell.  
  
-   SQL Server Management Studio : Les clients ne peuvent pas faire référence à un serveur avec la syntaxe similaire à <nom_ordinateur>/<nom_instance>. À compter de la version [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], la méthode recommandée consistait à utiliser une URL de site SharePoint. Par exemple, **http://<sharepoint_server>/<sharePoint_site&gt ;**. En commençant par [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], URL d’un site SharePoint est la seule syntaxe prise en charge.  
  
### <a name="report-model-designer-is-not-available-in-sql-server-data-tools"></a>Le générateur de modèles de rapport est disponible dans les outils de données SQL Server  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] n’est plus prend en charge les projets de modèle de rapport. Le générateur de modèles de rapport n'est pas disponible dans [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]. Vous ne pouvez pas créer de nouveaux projets de modèle de rapport ou ouvrir des projets existants dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] et vous ne pouvez pas créer ou mettre à jour des modèles de rapport. Pour mettre à jour des modèles de rapport, vous pouvez utiliser [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ou des outils précédents. Vous pouvez continuer à utiliser les modèles de rapport comme sources de données dans les rapports créés à l'aide d'outils [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] tels que le Générateur de rapports et le Concepteur de rapports. Le Concepteur de requêtes que vous utilisez pour créer des requêtes pour extraire des données de rapport à partir de modèles de rapport continue à être disponibles dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
##  <a name="bkmk_kj"></a> SQL Server 2008 R2 Reporting Services des modifications avec rupture  
 Cette section décrit les changements essentiels dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  SQL Server 2008 R2 étant une mise à niveau de version secondaire de SQL Server 2008, nous vous recommandons d'examiner également le contenu de la section SQL Server 2008.  
  
### <a name="expanded-csv-data-renderer"></a>Amélioration du rendu des données CSV  
 Dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], le fichier CSV inclut des données de graphique et jauge. Les applications qui dépendent d'une structure antérieure des fichiers CSV ne fonctionnent plus en raison de l'ajout de colonnes supplémentaires pour les graphiques et les jauges.  
  
 Pour plus d’informations, consultez [Exporting to a CSV File &#40;Report Builder and SSRS&#41;](report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Changements de comportement apportés à SQL Server Reporting Services dans SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Quelles sont les nouveautés &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Fonctionnalités déconseillées dans SQL Server Reporting Services dans SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [Fonctionnalités supprimées de SQL Server Reporting Services dans SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
