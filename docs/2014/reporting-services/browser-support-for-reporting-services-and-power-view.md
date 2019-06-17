---
title: Planification de la prise en charge des navigateurs pour Reporting Services et Power View (Reporting Services 2014)
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 58ed105619ca5ad5eadb00271e18ddaa10c6bfe3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63266820"
---
# <a name="planning-for-reporting-services-and-power-view-browser-support-reporting-services-2014"></a>Planification de la prise en charge des navigateurs pour Reporting Services et Power View (Reporting Services 2014)
  Dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)][!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], vous utilisez un navigateur Web pour afficher les rapports et exécuter le Gestionnaire de rapports. Certains navigateurs ne prennent pas en charge toutes les fonctionnalités de rapport. Cette rubrique décrit la prise en charge et la configuration requise pour les fonctionnalités de gestion du Gestionnaire de rapports, l'affichage de rapports, les contrôles de la visionneuse de rapports dans Visual Studio. Elle résume également la disponibilité des fonctionnalités pour les navigateurs pris en charge, les conditions requises pour l'authentification et les conditions requises pour les scripts.  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode SharePoint | [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode natif  
  
 **Dans cette rubrique :**  
  
- [Scénarios de navigateur Power View](#bkmk_powerview)  
  
- [Configuration requise du navigateur Report Manager (mode natif)](#bkmk_reportmanager)  
  
- [Configuration requise du navigateur pour afficher des rapports](#bkmk_reportviewer)  
  
- [Exigences d’authentification](#bkmk_authentication)  
  
- [Prise en charge du navigateur pour les contrôles de serveur Web ReportViewer dans Visual Studio](#bkmk_controls)  
  
##  <a name="bkmk_powerview"></a> Scénarios de navigateur Power View

 La liste des navigateurs pris en charge et des versions de navigateur que [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] prend en charge dépend du type de document ouvert. Les classeurs Excel 2013 et " **.rdlx**" fichiers utilisent des composants différents.  
  
|Type de document|Environnement|Prise en charge des navigateurs|  
|-------------------|-----------------|---------------------|  
|Rapport Power View (.RDLX)|**SharePoint Server :** [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] en mode intégré SharePoint pour [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et l'application Web Power View.|Consultez [Power View sur SharePoint Server et Reporting Services en mode intégré SharePoint](#bkmk_powerview_on_SSRS).|  
|Classeur Excel 2013 avec des feuilles Power View|**SharePoint Server :** [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] dans Excel Services.<br /><br /> **SharePoint Online (Office 365) :** [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] sur Excel Web App.|Consultez [Power View dans Excel Services ou Excel Web App dans SharePoint Online](#bkmk_powerview_on_ExcelServices).|  
  
###  <a name="bkmk_powerview_on_SSRS"></a> Power View sur SharePoint Server et Reporting Services SharePoint en Mode intégré  
 Le tableau suivant récapitule les versions de navigateur prises en charge pour [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] lorsqu'un utilisateur ouvre un rapport Power View (.RDLX) sur une batterie de serveurs SharePoint qui possède une application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour SharePoint installé et configuré.  
  
- La table s'applique à SharePoint 2010 et SharePoint 2013.  
  
- Pour plus d’informations sur la prise en charge des navigateurs SharePoint 2013, consultez [planifier la prise en charge des navigateurs dans SharePoint 2013](https://technet.microsoft.com//library/cc263526\(office.15\).aspx) (https://technet.microsoft.com/library/cc263526(office.15).aspx).  
  
- Pour plus d’informations sur la prise en charge des navigateurs SharePoint 2010, consultez [planifier la prise en charge des navigateurs (SharePoint Server 2010)](https://technet.microsoft.com/library/cc263526\(office.14\).aspx) (https://technet.microsoft.com/library/cc263526(office.14).aspx).  
  
|**Navigateur**|**Windows 8 et 8.1**|**Windows 7**|**Windows Server 2012 et 2012 R2**|**Windows Server 2008 R2**|**Windows Server 2008**|**Mac OS X 10.6-10.9**|  
|-----------------|---------------------------|-------------------|-----------------------------------------|--------------------------------|-----------------------------|------------------------------|  
|**Internet Explorer 11 (pour le bureau)**|32 bits, 64 bits|32 bits, 64 bits|32 bits, 64 bits|32 bits, 64 bits|Non pris en charge|Non pris en charge|  
|**Internet Explorer 10 (pour le bureau)**|32 bits, 64 bits|32 bits, 64 bits|32 bits, 64 bits|32 bits, 64 bits|Non pris en charge|Non pris en charge|  
|**Internet Explorer 9**|Non pris en charge|32 bits, 64 bits|Non pris en charge|32 bits, 64 bits|32 bits, 64 bits|Non pris en charge|  
|**Internet Explorer 8**|Non pris en charge|32 bits, 64 bits|Non pris en charge|32 bits, 64 bits|32 bits, 64 bits|Non pris en charge|  
|**Mozilla Firefox (dernière version commercialisée)**|32 bits|32 bits|32 bits|32 bits|32 bits|Non pris en charge|  
|**Apple Safari (dernière version commercialisée)**|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|32 bits, 64 bits|  
  
> [!NOTE]  
> « 32 bits » fait référence au navigateur, pas au système d'exploitation. Vous pouvez utiliser Internet Explorer 9 32 bits sur Windows 7 64 bits, par exemple.  
  
#### <a name="inprivate-browsing-feature-in-internet-explorer"></a>Fonctionnalités de navigation InPrivate dans Internet Explorer

 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] ne prend pas en charge les fonctionnalités de navigation InPrivate dans [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer versions 8 et 9. Pour plus d'informations sur la navigation InPrivate, consultez [Qu'est-ce que la navigation InPrivate ?](http://windows.microsoft.com/Windows7/What-is-InPrivate-Browsing) (http://windows.microsoft.com/Windows7/What-is-InPrivate-Browsing).  
  
###  <a name="bkmk_powerview_on_ExcelServices"></a> Power View dans Excel Services ou Excel Web App dans SharePoint Online

 Le tableau suivant récapitule les versions prises en charge du navigateur pour [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] lorsqu'un utilisateur ouvre un classeur Excel 2013 avec des feuilles Power View sur un serveur SharePoint qui exécute Excel Services :  
  
-   Pour plus d’informations sur la prise en charge des navigateurs SharePoint 2013, consultez [planifier la prise en charge des navigateurs dans SharePoint 2013](https://technet.microsoft.com/library/cc263526\(office.15\).aspx) (https://technet.microsoft.com/library/cc263526(office.15).aspx).  
  
|**Navigateur**|**Windows 8 et 8.1**|**Windows 7**|**Windows Server 2012 et 2012 R2**|**Windows Server 2008 R2**|**Windows Server 2008**|**Mac OS X 10.6-10.9**|  
|-----------------|---------------------------|-------------------|-----------------------------------------|--------------------------------|-----------------------------|------------------------------|  
|**Internet Explorer 11 (pour le bureau)**|32 bits, 64 bits|32 bits, 64 bits|32 bits, 64 bits|32 bits, 64 bits|Non pris en charge|Non pris en charge|  
|**Internet Explorer 10 (pour le bureau)**|32 bits, 64 bits|32 bits, 64 bits|32 bits, 64 bits|32 bits, 64 bits|Non pris en charge|Non pris en charge|  
|**Internet Explorer 9**|Non pris en charge|32 bits, 64 bits|Non pris en charge|32 bits, 64 bits|32 bits, 64 bits|Non pris en charge|  
|**Internet Explorer 8**|Non pris en charge|32 bits, 64 bits|Non pris en charge|32 bits, 64 bits|32 bits, 64 bits|Non pris en charge|  
|**Mozilla Firefox (dernière version commercialisée)**|32 bits|32 bits|32 bits|32 bits|32 bits|32 bits, 64 bits|  
|**Apple Safari (dernière version commercialisée)**|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|32 bits, 64 bits|  
|**Google Chrome (dernière version commercialisée)**|32 bits **(\*)** pour une durée limitée|32 bits **(\*)** pour une durée limitée|32 bits **(\*)** pour une durée limitée|32 bits **(\*)** pour une durée limitée|32 bits **(\*)** pour une durée limitée|Non pris en charge|  
  
 **(\*)** Chrome cessera de prise en charge de Netscape plug-in API (NPAPI), utilisée par Silverlight. Power View est dépendant de Silverlight.  Pour plus d'informations, consultez [The Final Countdown for NPAPI](http://blog.chromium.org/2014/11/the-final-countdown-for-npapi.html).  
  
##  <a name="bkmk_reportmanager"></a> Configuration requise du navigateur Report Manager (mode natif)

 Voici la liste actuelle des navigateurs pris en charge pour exécuter le Gestionnaire de rapports de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode natif et gérer les rapports et le serveur de rapports.  
  
|Browser|  
|-------------|  
|Internet Explorer 7, ou version ultérieure, avec activation des scripts.|  
|Mozilla FireFox (dernière version commercialisée)|  
|Apple Safari (dernière version commercialisée)|  
|Google Chrome (dernière version commercialisée)|  
  
##  <a name="bkmk_reportviewer"></a> Configuration requise du navigateur pour afficher des rapports

 Voici la liste actuelle des navigateurs et des fonctionnalités pris en charge avec la visionneuse de rapports. La visionneuse de rapports prend en charge les rapports du Gestionnaire de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et des bibliothèques SharePoint.  
  
|**Navigateur**|**Windows 8 et 8.1**|**Windows 7**|**Windows Server 2012 et 2012 R2**|**Windows Server 2008 R2**|**Windows Server 2008**|**Mac OS X 10.6-10.9**|**iOS 6 -7 pour iPad**|  
|-----------------|---------------------------|-------------------|-----------------------------------------|--------------------------------|-----------------------------|------------------------------|----------------------------|  
|**Internet Explorer 11 (pour le bureau)**|32 bits, 64 bits|32 bits, 64 bits|32 bits, 64 bits|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|  
|**Internet Explorer 10 (pour le bureau)**|32 bits, 64 bits|32 bits, 64 bits|32 bits, 64 bits|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|  
|**Internet Explorer 9**|Non pris en charge|32 bits, 64 bits|Non pris en charge|32 bits, 64 bits|32 bits, 64 bits|Non pris en charge|Non pris en charge|  
|**Internet Explorer 8**|Non pris en charge|32 bits, 64 bits|Non pris en charge|32 bits, 64 bits|32 bits, 64 bits|Non pris en charge|Non pris en charge|  
|**Internet Explorer 7**|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|32 bits, 64 bits|Non pris en charge|Non pris en charge|  
|**Mozilla Firefox (dernière version commercialisée)**|32 bits|32 bits|32 bits|32 bits|32 bits|Non pris en charge|Non pris en charge|  
|**Apple Safari (dernière version commercialisée)**|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|32 bits, 64 bits|Prise en charge avec des fonctionnalités limitées <sup>(1)</sup>|  
|**Google Chrome (dernière version commercialisée)**|32 bits|32 bits|32 bits|32 bits|32 bits|Non pris en charge|Non pris en charge|  
  
 **<sup>(1)</sup>**  Les fonctionnalités suivantes sont prises en charge :  
  
- Exportez vers des fichiers au format PDF et TIFF.  
  
- Affichez interactivement des rapports dans Apple Safari sur des périphériques iOS. Les fonctionnalités prises en charge incluent la bascule Développer/Réduire, le volet des paramètres et le tri interactif.  
  
- Pour plus d’informations, consultez [vue rapports Reporting Services sur les appareils Microsoft Surface et Apple iOS](../../2014/reporting-services/view-reporting-services-reports-surface-ios-devices.md).  
  
 **Remarque** Si vous accédez à un serveur de rapports à partir d'un ordinateur Macintosh, nous vous recommandons d'utiliser Safari. Si vous utilisez un produit SharePoint intégré à [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], consultez [Planifier la prise en charge des navigateurs (Windows SharePoint Services)](https://go.microsoft.com/fwlink/?LinkId=183583).  
  
### <a name="url-access-for-viewing-reports"></a>Accès URL pour afficher des rapports

 Pour consulter des rapports directement, sans les afficher dans le Gestionnaire de rapports, vous pouvez utiliser l'accès URL pour associer le rapport et la visionneuse de rapports. L'accès URL prend en charge différents navigateurs.  
  
 Pour plus d'informations sur l'accès URL, consultez la rubrique suivante :  
  
- [Référence de paramètres d'accès URL](url-access-parameter-reference.md)  
  
###  <a name="bkmk_authentication"></a> Exigences d’authentification

 Les navigateurs prennent en charge des schémas d'authentification spécifiques qui doivent être gérés par le serveur de rapports pour que la demande du client réussisse. Le tableau suivant identifie les types d'authentification par défaut pris en charge par chaque navigateur exécuté sur un système d'exploitation Windows.  
  
|**Type de navigateur**|**Prise en charge**|**Valeur de navigateur par défaut**|**Valeur de serveur par défaut**|  
|----------------------|------------------|-------------------------|------------------------|  
|**Internet Explorer**|Negociate, Kerberos, NTLM, Basic|Negotiate|Oui. Les paramètres d'authentification par défaut fonctionnent avec Internet Explorer.|  
|**Firefox**|NTLM, Basic|NTLM|Oui. Les paramètres d'authentification par défaut fonctionnent avec Firefox.|  
|**Safari**|Simple|Simple|Oui. Les paramètres d'authentification par défaut fonctionnent avec Safari.|  
|**Chrome**|Negotiated, NTLM, Basic|Negotiated|Oui. Les paramètres d'authentification par défaut fonctionnent avec Chrome.|  
  
### <a name="script-requirements"></a>Contraintes liées aux scripts

 Pour utiliser la visionneuse de rapports, configurez votre navigateur pour exécuter des scripts.  
  
 Si l'utilisation de scripts n'est pas activée, vous recevez un message d'erreur similaire au suivant lors de l'ouverture d'un rapport :  
  
- **Votre navigateur ne prend pas en charge les scripts ou est configuré pour ne pas les autoriser. Cliquez ici pour afficher ce rapport sans les scripts**.  
  
 Si vous choisissez de visualiser le rapport sans la prise en charge des scripts, le rapport est rendu en HTML sans fonctionnalités d'afficheur de rapports, telles que la barre d'outils Rapport et l'explorateur de documents.  
  
> [!NOTE]  
> La barre d'outils Rapport fait partie du composant Visionneuse HTML. Par défaut, la barre d'outils s'affiche en haut de chaque rapport affiché dans une fenêtre de navigateur. La visionneuse de rapports contient des fonctionnalités qui vous permettent de rechercher des informations dans le rapport, d'atteindre une page spécifique, et d'ajuster la taille de la page à des fins d'affichage. Pour plus d'informations sur la barre d'outils du rapport ou sur la Visionneuse HTML, consultez [HTML Viewer and the Report Toolbar](html-viewer-and-the-report-toolbar.md).  
  
##  <a name="bkmk_controls"></a> Prise en charge du navigateur pour les contrôles de serveur Web ReportViewer dans Visual Studio

 Le contrôle serveur Web ReportViewer est utilisé pour inclure la fonctionnalité de rapports dans une application Web ASP.NET. Les contrôles sont inclus dans Visual Studio et prennent en charge des navigateurs et des versions de navigateur différents de ceux des autres composants décrits dans cette rubrique. Le type de navigateur utilisé pour afficher l'application détermine le type de fonctionnalité ReportViewer que vous pouvez fournir dans votre application. Utilisez le tableau de cette rubrique pour déterminer quels sont les navigateurs pris en charge soumis à des restrictions de fonctionnalités de rapport et quelles sont les plateformes prises en charge.  
  
 En raison des différences qui existent au niveau du rendu des moteurs des navigateurs pris en charge, certaines fonctionnalités de rapport avancées peuvent s'afficher différemment dans différents navigateurs.  Par exemple, la rotation du texte.  
  
### <a name="scripting-requirements"></a>Contraintes liées aux scripts

 Utilisez un navigateur dans lequel la prise en charge du script est activée. Si le navigateur ne peut pas exécuter de scripts, vous ne pourrez pas afficher le rapport.  
  
### <a name="browser-requirements-for-viewing-reports-with-the-reportviewer-web-server-controls"></a>Exigences de navigateur pour afficher des rapports avec les contrôles de serveur Web ReportViewer

 La prise en charge des fonctionnalités de rapport interactives varie en fonction du type de navigateur. Le tableau ci-dessous indique les types de navigateur et les plateformes pris en charge, sous réserve des conditions notées dans la colonne Remarques.  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|**Navigateur**|**Windows 8** et **Windows 8.1**|**Windows 7**|**Windows Server 2012** et **2012 R2**|**Windows Server 2008** et **2008 R2**|**Windows Server 2003**|**Mac OS X 10.6-10.9**|**Remarques**|  
|**Internet Explorer 11 (pour le bureau**|Oui|Oui|Oui|Non pris en charge|Non pris en charge|Non pris en charge|Internet Explorer prend en charge l'ensemble complet des fonctionnalités ReportViewer.|  
|**Internet Explorer 10 (pour le bureau)**|Oui|Oui|Oui|Non pris en charge|Non pris en charge|Non pris en charge|Internet Explorer prend en charge l'ensemble complet des fonctionnalités ReportViewer.|  
|**Internet Explorer 9**|Non pris en charge|Oui|Non pris en charge|Oui|Oui|Oui|Internet Explorer prend en charge l'ensemble complet des fonctionnalités ReportViewer.|  
|**Internet Explorer 8.0**|Non pris en charge|Oui|Non pris en charge|Oui|Oui<sup>1</sup>|Non pris en charge|Internet Explorer prend en charge l'ensemble complet des fonctionnalités ReportViewer. <sup>1</sup>|  
|**Internet Explorer 7.0**|Non pris en charge|Oui|Non pris en charge|Oui|Oui<sup>1</sup>|Non pris en charge|Internet Explorer prend en charge l'ensemble complet des fonctionnalités ReportViewer. <sup>1</sup>|  
|**Firefox (dernière version commercialisée)**|Oui|Oui|Oui|Oui|Oui|Non pris en charge|L'impression et le zoom ne sont pas pris en charge.|  
|**Safari (dernière version commercialisée)**|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|Oui|L'impression et le zoom ne sont pas pris en charge.<br /><br /> Le contrôle de calendrier utilisé pour sélectionner des dates sur un rapport paramétré a été désactivé dans ce navigateur. Les utilisateurs doivent taper manuellement les dates dans la zone de message du paramètre.|  
|**Chrome (dernière version commercialisée)**|Oui|Oui|Oui|Oui|Oui|Non pris en charge|L'impression et le zoom ne sont pas pris en charge.|  
  
 <sup>1</sup>en mode standard, Internet Explorer 7.0 et 8.0 n’affichent pas les lignes inclinées dans les rapports. Si vous utilisez des lignes inclinées dans vos rapports, configurez votre page ASP.NET pour qu'elle s'exécute en mode Quirks dans Internet Explorer. Pour ce faire, recherchez le \<! DOCTYPE > dans votre page ASP.NET. Ou, si vous utilisez une page maître, vous pouvez rechercher la balise dans le fichier .master. Cette balise ressemble à celle-ci :  
  
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
```
  
 Remplacez le \<! DOCTYPE > balise avec la balise suivante :  
  
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">  
```
  
 Pour plus d’informations sur les modes de compatibilité dans Internet Explorer, consultez [définissant la compatibilité des documents](https://go.microsoft.com/fwlink/?LinkId=180380) (https://go.microsoft.com/fwlink/?LinkId=180380).  
  
 Pour plus d’informations sur l’utilisation de contrôles ReportViewer, consultez [déploiement de rapports et des contrôles ReportViewer](https://msdn.microsoft.com/library/ms251723.aspx) (https://msdn.microsoft.com/library/ms251723.aspx).  
  
## <a name="next-steps"></a>Étapes suivantes

 [Outils de Reporting Services](tools/reporting-services-tools.md) [le Gestionnaire de rapports &#40;SSRS en Mode natif&#41; ](../../2014/reporting-services/report-manager-ssrs-native-mode.md) [visionneuse HTML et la barre d’outils rapport](html-viewer-and-the-report-toolbar.md) [référence de paramètre d’accès URL](url-access-parameter-reference.md)  
