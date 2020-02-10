---
title: Planifier la conception de rapports et le déploiement de rapports (Reporting Services 2014) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1c1e265e-52a2-4de3-96fd-ca4abae01c02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6104bfc97d2f66652ffa9b16e9ff0ae8f9b0550
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108048"
---
# <a name="plan-for-report-design-and-report-deployment-reporting-services-2014"></a>Planifier la conception de rapports et le déploiement de rapports (Reporting Services 2014)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] offre plusieurs approches pour la création et le déploiement de rapports. Utilisez cette rubrique pour planifier un environnement de création de rapports et un serveur de rapports fonctionnant ensemble. Cette rubrique offre une vue d'ensemble de la prise en charge de la définition de rapport par les composants [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Une définition de rapport est un fichier XML écrit dans le langage RDL (Report Definition Language) ou RDLC (Report Definition Language for Clients). Chaque définition de rapport est conforme à une version de schéma spécifique qui est indiquée au début du fichier.  
  
 Les fichiers RDL sont créés dans le Concepteur de rapports dans les projets [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] et dans le Générateur de rapports version 3.0. Les fichiers RDLC sont créés à l'aide des contrôles ReportViewer qui sont inclus dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Dans cette rubrique :  
  
-   [Versions de schéma RDL](#bkmk_rdl_schema_versions)  
  
-   [Prise en charge du serveur de rapports et du schéma RDL](#bkmk_report_server_rdl_schema_support)  
  
-   [Prise en charge de la création et du déploiement de rapports](#bkmk_report_authoring_and_deployment)  
  
-   [Contrôles ReportViewer](#bkmk_reportviewer)  
  
##  <a name="bkmk_rdl_schema_versions"></a>Versions de schéma RDL  
 Le tableau suivant répertorie chaque version disponible du schéma et l'abréviation utilisée dans le reste de cette rubrique :  
  
|Abréviation|Version de schéma|  
|------------------|--------------------|  
|RDL 2010|https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition|  
|RDL 2008|https://schemas.microsoft.com/sqlserver/reporting/2008/01/reportdefinition|  
|RDL 2005<br /><br /> RDLC 2005|https://schemas.microsoft.com/sqlserver/reporting/2005/01/reportdefinition|  
|RDL 2000|https://schemas.microsoft.com/sqlserver/reporting/2003/10/reportdefinition|  
  
 Pour plus d'informations sur RDL et les schémas RDL, reportez-vous aux rubriques suivantes :  
  
-   [Schémas XML Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=31850)  
  
-   [Spécifications de Report Definition Language](https://go.microsoft.com/fwlink/?linkid=116865)  
  
-   [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md)  
  
 Pour plus d’informations sur les contrôles ReportViewer, consultez [Contrôles ReportViewer (Visual Studio)](https://msdn.microsoft.com/library/ms251671.aspx).  
  
##  <a name="bkmk_report_server_rdl_schema_support"></a>Prise en charge du serveur de rapports et du schéma RDL  
 Un fichier de définition de rapport peut être déployé sur un serveur de rapports [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] des manières suivantes :  
  
-   **Concepteur de rapports :** Déployez un rapport à partir [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)]de concepteur de rapports dans.  
  
-   **Générateur de rapports :** Enregistrez un rapport sur le serveur de rapports à partir de Générateur de rapports.  
  
-   **Gestionnaire de rapports :** Téléchargez un rapport sur un serveur de rapports en mode natif à partir de Gestionnaire de rapports.  
  
-   **SharePoint :** Téléchargez un rapport sur un site SharePoint configuré avec un serveur de rapports en mode SharePoint.  
  
-   **Par programme :** Publiez par programme un rapport à l’aide des interfaces API SOAP vers un serveur de rapports. Pour plus d'informations, consultez [Report Server Web Service](report-server-web-service/report-server-web-service.md).  
  
 Le tableau suivant indique version par version le schéma RDL pris en charge pour le serveur de rapports.  
  
|Version de serveur de rapports|Version de schéma RDL|  
|---------------------------|------------------------|  
|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<br /><br /> ou<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]<br /><br /> ou<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|RDL 2010<br /><br /> RDL 2008<br /><br /> RDL 2005<br /><br /> RDL 2000|  
|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]|RDL 2008<br /><br /> RDL 2005<br /><br /> RDL 2000|  
|[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]|RDL 2005<br /><br /> RDL 2000|  
  
 Lorsque vous téléchargez ou publiez une définition de rapport vers le serveur de rapports ou mettez à niveau un serveur de rapports qui contient des rapports, le serveur de rapports conserve la définition de rapport dans le format d'origine. **Lors de la première utilisation**, le serveur de rapports met à niveau le rapport dans la base de données du serveur de rapports vers un format binaire qui est conservé pour les vues suivantes. La définition de rapport (.rdl) proprement dite n'est pas mise à niveau.  
  
 Vous pouvez extraire du serveur de rapports une copie en lecture seule du fichier de définition de rapport (.rdl). Sur un serveur de rapports en mode natif, accédez au gestionnaire de rapports, sélectionnez le rapport et cliquez sur **Télécharger**. Dans un déploiement en mode SharePoint, accédez à la bibliothèque de documents, sélectionnez le rapport et cliquez sur **Télécharger une copie**.  
  
 Pour mettre à niveau la définition de rapport, vous devez ouvrir le rapport dans un environnement de création de rapports et l'enregistrer.  
  
 Pour plus d’informations sur les mises à niveau de rapports et les versions de schéma prises en charge, consultez [Mettre à niveau des rapports](install-windows/upgrade-reports.md).  
  
##  <a name="bkmk_report_authoring_and_deployment"></a>Prise en charge de la création et du déploiement de rapports  
 Les environnements de création de rapports sont le Concepteur de rapports dans les projets [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] et le Générateur de rapports. Les environnements de création de rapports fournissent de nombreuses prises en charge pour la mise à niveau de rapport, la conception de rapport, l'aperçu de rapport en mode local, l'aperçu de rapport sur le serveur de rapports et le déploiement de rapport.  
  
 Le tableau suivant récapitule la prise en charge de la création et du déploiement de définitions de rapport pour les différentes versions de schéma :  
  
|Environnement de création|Version RDL créée|Version RDL de déploiement|Versions de déploiement sur le serveur de rapports|  
|---------------------------|--------------------------|------------------------|--------------------------------------|  
|Concepteur de rapports dans SQL Server 2014 Data Tools - Business Intelligence pour Microsoft Visual Studio 2012, dans le Centre de téléchargement Microsoft.<br /><br /> ou<br /><br /> Concepteur de rapports dans SQL Server 2012 Data Tools - Business Intelligence pour Microsoft Visual Studio 2012, dans le Centre de téléchargement Microsoft.<br /><br /> ou<br /><br /> Concepteur de rapports dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Data Tools, inclus dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].|Auteurs 2010 RDL. À l'ouverture d'un RDL existant :<br /><br /> RDL 2000, mises à niveau vers RDL 2010<br /><br /> RDL 2005, mises à niveau vers RDL 2010<br /><br /> RDL 2008, mises à niveau vers RDL 2010|RDL 2008<br /><br /> RDL 2010|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|  
|Concepteur de rapports dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Business Intelligence Development Studio|Auteurs 2010 RDL. À l'ouverture d'un RDL existant :<br /><br /> RDL 2000, mises à niveau vers RDL 2010<br /><br /> RDL 2005, mises à niveau vers RDL 2010<br /><br /> RDL 2008, mises à niveau vers RDL 2010|RDL 2008<br /><br /> RDL 2010|[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|  
|Concepteur de rapports dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] Business Intelligence Development Studio|Auteurs 2008 RDL. À l'ouverture d'un RDL existant :<br /><br /> RDL 2000, mises à niveau vers RDL 2008<br /><br /> RDL 2005, mises à niveau vers RDL 2008|RDL 2008|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]|  
|[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]Générateur de rapports|Auteurs 2010 RDL. À l'ouverture d'un RDL existant :<br /><br /> RDL 2000, mises à niveau vers RDL 2010<br /><br /> RDL 2005, mises à niveau vers RDL 2010<br /><br /> RDL 2008, mises à niveau vers RDL 2010|RDL 2010|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|  
|Concepteur de rapports Visual Studio RDLC|RDLC 2005|N/A|N/A|  
  
 Pour plus d'informations sur [!INCLUDE[ss_dtbi_vs2013](../includes/ss-dtbi-vs2013-md.md)], consultez les documents suivants :  
  
-   [Déploiement et prise en charge des versions dans SQL Server Data Tools &#40;SSRS&#41;](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)  
  
-   [Microsoft SQL Server Data Tools-Business Intelligence pour Visual Studio 2012](https://www.microsoft.com/download/details.aspx?id=36843).  
  
##  <a name="bkmk_reportviewer"></a>Contrôles ReportViewer  
 Le contrôle ReportViewer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] peut d'afficher un rapport .rdlc en mode de prévisualisation local ou distant. Il peut afficher un fichier .rdl hébergé sur un serveur de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Le tableau suivant fournit la liste des versions RDL prises en charge par les contrôles de ReportViewer pour le traitement local (.rdlc). La prise en charge RDL côté serveur est résumée dans la section [Prise en charge du serveur de rapports et du schéma RDL](#bkmk_report_server_rdl_schema_support).  
  
|Contrôle ReportViewer du produit|Version de RDL pour la prévisualisation locale|  
|-------------------------------------|--------------------------------------|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]2013<br /><br /> ou<br /><br /> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]2012<br /><br /> ou<br /><br /> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]|RDL 2008|  
|[!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]<br /><br /> ou<br /><br /> [!INCLUDE[vsOrcas](../includes/vsorcas-md.md)]|RDL 2005|  
  
 Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Conversion de fichiers RDLC en fichiers RDL](https://msdn.microsoft.com/library/ms252109.aspx)  
  
-   [Contrôles ReportViewer (Visual Studio)](https://msdn.microsoft.com/library/ms251671.aspx)  
  
-   [Ajout et configuration des contrôles ReportViewer](https://msdn.microsoft.com/library/ms252104.aspx)  
  
## <a name="see-also"></a>Voir aussi  
 [Rapports, parties de rapports et définitions de rapports &#40;Générateur de rapports et SSRS&#41;](report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md)   
 [Outils de Reporting Services](tools/reporting-services-tools.md)   
 [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md)  
  
  
