---
title: "Planification de la prise en charge des navigateurs pour Reporting Services et Power View (Reporting Services 2014) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "affichage de rapports"
  - "scripts [Reporting Services], configuration requise"
  - "affichage de rapports"
  - "navigateurs [Reporting Services]"
  - "Navigateurs [Reporting Services], à propos de la prise en charge des navigateurs"
  - "exploration des rapports [Reporting Services]"
  - "composants [Reporting Services], navigateurs"
  - "navigateurs Web [Reporting Services]"
ms.assetid: 48a75bbb-0029-4c43-891d-dc8f4fc0ebe1
caps.latest.revision: 121
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 121
---
# Planification de la prise en charge des navigateurs pour Reporting Services et Power View (Reporting Services 2014)
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]

Découvrez les versions de navigateurs prises en charge pour la gestion et l’affichage de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], des contrôlesReportViewer Controls et de Power View.
  
 **S’applique à :** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode natif | [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode SharePoint  
  
##  <a name="bkmk_webportal"></a> Navigateurs requis pour le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]

Voici la liste actuelle des navigateurs pris en charge pour le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)].

**Microsoft Windows**  
*Windows 7, 8.1, 10 ; Windows Server 2008 R2, 2012, 2012 R2*
- Microsoft Edge (+)
- Microsoft Internet Explorer 10 ou 11
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple iOS**  
*iPhone et iPad IOS 9 avec iOS 9*

- Apple Safari (+)

**Google Android**  
*Téléphones portables et tablettes avec Android 4.4 (KitKat) ou version ultérieure*

- Google Chrome (+)

 **(+)** Dernière version commercialisée  
  
##  <a name="bkmk_reportviewer"></a> Navigateurs requis pour le contrôle web ReportViewer (2015) 
 Voici la liste actuelle des navigateurs pris en charge avec le contrôle web ReportViewer (2015). La Visionneuse de rapports prend en charge l’affichage des rapports du portail web [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et des bibliothèques SharePoint.  
  
**Microsoft Windows**  
*Windows 7, 8.1, 10 ; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Edge (+)
- Microsoft Internet Explorer 10 ou 11
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
  
 **(+)** Dernière version commercialisée  
  
 Si vous utilisez un produit SharePoint intégré à [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], consultez  [Planifier la prise en charge du navigateur dans SharePoint 2016](http://technet.microsoft.com//library/cc263526\(v=office.16\).aspx).  
  
###  <a name="bkmk_authentication"></a> Exigences relatives à l’authentification  
 Les navigateurs prennent en charge des schémas d'authentification spécifiques qui doivent être gérés par le serveur de rapports pour que la demande du client réussisse. Le tableau suivant identifie les types d'authentification par défaut pris en charge par chaque navigateur exécuté sur un système d'exploitation Windows.  
  
|**Type de navigateur**|**Prise en charge**|**Valeur de navigateur par défaut**|**Valeur de serveur par défaut**|  
|----------------------|------------------|-------------------------|------------------------|  
|**Microsoft Edge** (+)|Negociate, Kerberos, NTLM, Basic|Negotiate|Oui. Les paramètres d’authentification par défaut fonctionnent avec Microsoft Edge.|  
|**Microsoft Internet Explorer**|Negociate, Kerberos, NTLM, Basic|Negotiate|Oui. Les paramètres d'authentification par défaut fonctionnent avec Internet Explorer.|  
|**Google Chrome**(+)|Negotiated, NTLM, Basic|Negotiate|Oui. Les paramètres d'authentification par défaut fonctionnent avec Chrome.|  
|**Mozilla Firefox**(+)|NTLM, Basic|NTLM|Oui. Les paramètres d'authentification par défaut fonctionnent avec Firefox.|  
|**Apple Safari**(+)|NTLM, Basic|Basic|Oui. Les paramètres d'authentification par défaut fonctionnent avec Safari.|  
  
 **(+)** Dernière version commercialisée  
  
### Contraintes relatives à l’utilisation de scripts pour afficher des rapports  
 Pour utiliser la visionneuse de rapports, configurez votre navigateur pour exécuter des scripts.  
  
 Si l'utilisation de scripts n'est pas activée, vous recevez un message d'erreur similaire au suivant lors de l'ouverture d'un rapport :  
  
-   **Votre navigateur ne prend pas en charge les scripts ou est configuré pour ne pas les autoriser. Cliquez ici pour afficher ce rapport sans les scripts**.  
  
 Si vous choisissez de visualiser le rapport sans la prise en charge des scripts, le rapport est rendu en HTML sans fonctionnalités d'afficheur de rapports, telles que la barre d'outils Rapport et l'explorateur de documents.  
  
> [!NOTE]  
>  La barre d'outils Rapport fait partie du composant Visionneuse HTML. Par défaut, la barre d'outils s'affiche en haut de chaque rapport affiché dans une fenêtre de navigateur. La visionneuse de rapports contient des fonctionnalités qui vous permettent de rechercher des informations dans le rapport, d'atteindre une page spécifique, et d'ajuster la taille de la page à des fins d'affichage. Pour plus d'informations sur la barre d'outils du rapport ou sur la Visionneuse HTML, consultez [HTML Viewer and the Report Toolbar](../reporting-services/html-viewer-and-the-report-toolbar.md).  
  
##  <a name="bkmk_controls"></a> Prise en charge des navigateurs pour les contrôles serveurs Web ReportViewer dans Visual Studio  
 Le contrôle serveur Web ReportViewer est utilisé pour inclure la fonctionnalité de rapports dans une application Web ASP.NET. Les contrôles sont inclus dans Visual Studio et prennent en charge des navigateurs et des versions de navigateur différents de ceux des autres composants décrits dans cette rubrique. Le type de navigateur utilisé pour afficher l'application détermine le type de fonctionnalité ReportViewer que vous pouvez fournir dans votre application. Utilisez le tableau de cette rubrique pour déterminer quels sont les navigateurs pris en charge soumis à des restrictions de fonctionnalités de rapport et quelles sont les plateformes prises en charge.  
  
 Utilisez un navigateur dans lequel la prise en charge du script est activée. Si le navigateur ne peut pas exécuter de scripts, vous ne pourrez pas afficher le rapport.  
  
**Microsoft Windows**  
*Windows 7, 8.1, 10 ; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Edge (+)
- Microsoft Internet Explorer 10 ou 11
- Google Chrome (+)
- Mozilla Firefox (+)
  
 **(+)** Dernière version commercialisée  
  
##  <a name="bkmk_powerview"></a> Prise en charge du navigateur Power View  

**Microsoft Windows**  
*Windows 7, 8.1, 10 ; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Internet Explorer 10 ou 11
- Mozilla Firefox (+)
  
**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
  
 **(+)** Dernière version commercialisée  
  
 Pour en savoir plus sur la prise en charge des navigateurs SharePoint 2016, consultez [Planifier la prise en charge du navigateur dans SharePoint 2013](http://technet.microsoft.com//library/cc263526\(v=office.16\).aspx).  
  
## Voir aussi  
[Recherche et affichage de rapports dans le portail web &#40;Générateur de rapports et SSRS&#41;](http://msdn.microsoft.com/fr-fr/8556807e-f2e2-4a7b-bb1b-ac5ea1872e51)  
[Outils de Reporting Services](../reporting-services/tools/reporting-services-tools.md)  
[Portail web (SSRS en mode natif)](http://msdn.microsoft.com/fr-fr/7349e626-6ed5-4d21-b05f-cf042ad9ad70)  
[Visionneuse HTML et barre d'outils Rapport](../reporting-services/html-viewer-and-the-report-toolbar.md)  
[Référence de paramètre d'accès URL](../reporting-services/url-access-parameter-reference.md)  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]
